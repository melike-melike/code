<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <div id="app">
    <p>Fetch me some Extra Pale Malt beers</p>
    {{ info }}
    <p>Your beers are served ... bon appétit ...</p>
    <router-view/>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data () {
    return {
      info: []
    }
  },
  mounted () {
    axios.get('https://api.punkapi.com/v2/beers/?q={%22malt%22:%20%22Extra%20Pale%22}').then(response => (this.info = response.data))
  }
}
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
