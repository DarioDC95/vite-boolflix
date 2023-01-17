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
        }
    }
</script>
<template>
    <div class="card">
        <h5>Titolo: {{ title(element) }}</h5>
        <h5>Titolo originale: {{ original_title(element) }}</h5>
        <h5>Lingua: {{ element.original_language }}</h5>
        <h5>Voto: {{ element.vote_average }}</h5>
    </div>
</template>
<style scoped lang="scss">
    
</style>