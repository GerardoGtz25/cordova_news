<template>
  <v-ons-page id="app">
    <v-ons-toolbar>
      <div class="center">Journal Electronique</div>
    </v-ons-toolbar>
    <home-page></home-page>
  </v-ons-page>
</template>

<script>
import HomePage from './components/HomePage'
// import MenuPage from './components/MenuPage'

export default {
  name: 'app',
  computed: {

  },
  components: {
    HomePage,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
