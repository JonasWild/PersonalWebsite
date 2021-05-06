<template>
  <v-container
    id="user-profile"
    fluid
    tag="section"
  >
      <chessboard />
  </v-container>
</template>

<script>
  export default {
    name: 'DashboardDashboard',
    components: {
      Chessboard: () => import('.././component/Chessboard'),
    },
  }

</script>
