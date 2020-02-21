<template>
  <div id="app" if="brewery">
    <h1> US Brewerys </h1>

    <brewery-list :brewerys="brewerys"></brewery-list>

  </div>
</template>

<script>
import { eventBus } from './main.js'
// import HelloWorld from './components/HelloWorld.vue'
import BreweryList from './components/BreweryList.vue'
export default {
  name: 'app',
  components: {
    // HelloWorld
    "brewery-list": BreweryList
  },
  data() {
    return {
      brewerys: []
    }
  },
  methods: {
    getBrewerys: function() {
      fetch("https://api.openbrewerydb.org/breweries")
      .then(res => res.json())
      .then(brewerys => this.brewerys = brewerys )
    }
  },
  mounted() {
    this.getBrewerys();


  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
