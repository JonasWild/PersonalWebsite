<template>
  <v-container
    id="chessboard"
    fluid
    tag="section"
  >
    <v-card>
      <chessboard />
    </v-card>
  </v-container>
</template>

<script>
  import { chessboard } from 'vue-chessboard'
  import 'vue-chessboard/dist/vue-chessboard.css'

  export default {
    name: 'Chessboard',
    components: {
      chessboard,
    },
  }
</script>

<style lang="sass">
  .v-application .blue
    background-color: transparent !important
    padding: 10vw
    display: flex
    justify-content: center
</style>
