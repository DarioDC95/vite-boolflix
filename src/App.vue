<script>
  // libraries
  import axios from 'axios'

  // components
  import AppHeader from './components/AppHeader.vue'
  import AppBody from './components/AppBody.vue'

  export default {
    components: {
      AppHeader,
      AppBody,
    }
  }
</script>

<template>
  <AppHeader />
  <AppBody />
</template>

<style lang="scss">
@use './styles/general.scss' as *;

</style>
