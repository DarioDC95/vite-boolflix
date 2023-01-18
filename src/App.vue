<script>
  // libraries
  import { store } from './store.js'
  import axios from 'axios'

  // components
  import AppHeader from './components/AppHeader.vue'
  import AppBody from './components/AppBody.vue'

  export default {
    components: {
      AppHeader,
      AppBody,
    },
    data() {
      return {
        store,
      }
    },
    created() {
      this.getcards()
    },
    methods: {
      getcards() {
        axios.get(`${store.url_movies}${store.search}`).then((response) => {
          let provisionCard = response.data.results;
          store.cards = provisionCard.filter(Object => {
            return Object.media_type != 'person'
          })
        })
      },
      changeSearch( newvalue ) {
        store.search = newvalue;
        this.getcards()
      }
    },
  }
</script>

<template>
  <AppHeader @searching="changeSearch"/>
  <AppBody />
</template>

<style lang="scss">
@use './styles/general.scss' as *;

</style>
