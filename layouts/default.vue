<template>
  <v-app>
    <Navbar />
    <div class="app">
      <nuxt />
    </div>
  </v-app>
</template>

<script>
import Navbar from '~/components/Navbar'

export default {
  components: {
    Navbar
  }
}
</script>

<style>
  .app {
    text-align: center;
    margin: 30px;
  }
</style>
