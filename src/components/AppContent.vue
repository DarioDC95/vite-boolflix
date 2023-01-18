<script>
    export default {
        props: {
            element: Object,
        },
        methods: {
            title(value) {
                if(value.media_type == 'tv') {
                    return value.name
                }
                else {
                    return value.title
                }
            },
            original_title(value) {
                if(value.media_type == 'tv') {
                    return value.original_name
                }
                else {
                    return value.original_title
                }
            },
            type(value) {
                if (value.media_type == 'tv') {
                    return 'tv-series'
                }
                return value.media_type
            },
            image(value) {
                return `https://image.tmdb.org/t/p/w300${value.poster_path}`
            },
            getFlag(value) {
                let lang = '';
                
                if(value.original_language) {

                    switch (value.original_language) {
                        case 'ja':
                            lang = 'jp'
                            break;
    
                        case 'en':
                            lang = 'gb'   
                            break; 

                        case 'ko':
                            lang = 'kr'   
                            break; 
                    
                        default:
                            lang = (value.original_language)
                            break;
                    }
    
                    let url = lang.toUpperCase()
                    return url
                }
            },
            getStars(value) {
                let vote = Math.round((value.vote_average) / 2);
                let star = [];
                for(let i = 0; i < vote; i++) {
                    star.push('fa-solid fa-star')
                }
                let voteNot = 5 - vote;
                for(let i = 0; i < voteNot; i++) {
                    star.push('fa-regular fa-star')
                }
                return star 
            },
        }
    }
</script>
<template>
    <div v-if="element.poster_path" class="card">
        <img :src="image(element)" :alt="title(element)">
        <div class="description">
            <div>Tipologia: <span class="fs-5 fw-semibold">{{ type(element) }}</span></div>
            <div>Titolo: <span class="fs-5 fw-semibold">{{ title(element) }}</span></div>
            <div>Titolo originale: <span class="fs-5 fw-semibold">{{ original_title(element) }}</span></div>
            <div>Lingua: <img :src="`https://flagsapi.com/${getFlag(element)}/shiny/64.png`" :alt="element.original_language"></div>
            <div class="d-flex">
                <div class="me-2">Voto:</div>
                <div class="stars d-flex text-warning">
                    <div v-for="(value, index) in getStars(element)" :key="index"><font-awesome-icon :icon="value"/></div>
                </div>
            </div>
        </div>
    </div>
    <div v-else class="card sub-card">
        <div class="description">
            <div>Tipologia: <span>{{ element.media_type }}</span></div>
            <div>Titolo: <span class="fs-6 fw-semibold">{{ title(element) }}</span></div>
            <div>Titolo originale: <span class="fs-6 fw-semibold">{{ original_title(element) }}</span></div>
            <div>Lingua: <img :src="`https://flagsapi.com/${getFlag(element)}/shiny/64.png`" :alt="element.original_language"></div>
            <div class="d-flex">
                <div class="me-2">Voto:</div>
                <div class="stars d-flex text-warning">
                    <div v-for="(value, index) in getStars(element)" :key="index"><font-awesome-icon :icon="value"/></div>
                </div>
            </div>
        </div>
    </div>
</template>
<style scoped lang="scss">
    @use '../styles/partials/variables' as *;

    .card {
        width: 250px;
        height: 100%;
        overflow: hidden;
        position: relative;

        img {
            height: 100%;
        }

        .description {
            position: absolute;
            opacity: 0;
            padding: 20px;
            background-color: black;
            width: 100%;
            height: 100%;
            color: $color-white;
        }

        &:hover .description {
            opacity: 1;
        }
    }

    .sub-card {

        .description {
            opacity: 1;
        }
    }
</style>