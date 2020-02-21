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
    },
    getSimilarBrewerys: function(brewery_type){
      fetch(`https://api.openbrewerydb.org/breweries?by_type=${brewery_type}`)
        .then(typeRes => typeRes.json())
        .then(typeBrewerys => this.typeBrewerys = typeBrewerys)


        // (this.brewery_type = brewery_type);

      }
    },


  // },
  mounted() {
    this.getBrewerys();

    eventBus.$on("get-similar-brewerys", brewery_type => (
      (this.brewery_type = brewery_type)
      .then(this.getSimilarBrewerys(this.brewery_type))
    ))
  }
}
</script>
