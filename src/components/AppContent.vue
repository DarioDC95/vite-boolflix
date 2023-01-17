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
            image(value) {
                if(value.poster_path) {
                    return `https://image.tmdb.org/t/p/w300${value.poster_path}`
                }
                else {
                    return `/src/assets/immagine-non-disponibile1005159164531791008.jpg`
                }
            },
            getFlag(value) {
                let lang = '';
                switch (value.original_language) {
                    case 'ja':
                        lang = 'jp'
                        break;

                    case 'en':
                        lang = 'gb'   
                        break; 
                
                    default:
                        lang = (value.original_language)
                        break;
                }
                let url = lang.toUpperCase()
                return url
            }
        }
    }
</script>
<template>
    <div class="card rounded-top-0">
        <img :src="image(element)" :alt="title(element)">
        <div class="description">
            <div>Titolo: <span class="fs-5 fw-semibold">{{ title(element) }}</span></div>
            <div>Titolo originale: <span class="fs-5 fw-semibold">{{ original_title(element) }}</span></div>
            <div>Lingua: <img :src="`https://flagsapi.com/${getFlag(element)}/shiny/64.png`" :alt="element.original_language"></div>
            <div>Voto: <span class="fs-5 fw-semibold">{{ element.vote_average }}</span></div>
        </div>
    </div>
</template>
<style scoped lang="scss">
    @use '../styles/partials/variables' as *;

    .card {
        width: 250px;
        // height: 350px;
        position: relative;

        // img {
        //     height: 100%;
        // }

        // .description {
        //     position: absolute;
        //     display: none;
        //     background-color: black;
        //     width: 100%;
        //     height: 100%;
        //     color: $color-white;
        // }

        &:hover .description {
            display: block;
        }
    }
</style>