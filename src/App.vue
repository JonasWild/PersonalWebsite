<template>
  <router-view id='my_app' />
</template>

<script>
  export default {
    name: 'App',
    mounted: function () {
      this.$vuetify.theme.themes[this.isDark ? 'dark' : 'light'].primary = '#FFFFFF'
    },
  }
</script>

<style lang="sass">
  #my_app
    font-family: 'Montserrat', sans-serif
    color: grey
</style>
