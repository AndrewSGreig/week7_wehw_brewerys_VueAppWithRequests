<template>
  <div id="app" if="brewery">
    <h1> US Breweries </h1>

    <brewery-list :breweries="breweries"></brewery-list>

  </div>
</template>

<script>
import { eventBus } from './main.js'
// import HelloWorld from './components/HelloWorld.vue'
import BreweryList from './components/BreweryList.vue'
import BreweryTypeList from './components/BreweryTypeList.vue'
export default {
  name: 'app',
  components: {
    // HelloWorld
    "brewery-list": BreweryList,
    "brewery-type-list": BreweryTypeList
  },
  data() {
    return {
      breweries: [],
      typeBreweries:[]
    }
  },
  methods: {
    getBreweries: function() {
      fetch("https://api.openbrewerydb.org/breweries")
      .then(res => res.json())
      .then(breweries => this.breweries = breweries )
    },
    getSimilarBreweries: function(brewery_type){
      fetch(`https://api.openbrewerydb.org/breweries?by_type=${brewery_type}`)
        .then(typeRes => typeRes.json())
        .then(typeBreweries => this.typeBreweries = typeBreweries)
        .then(console.log(this.typeBreweries))


        // (this.brewery_type = brewery_type);

      }

    },


  // },
  mounted() {
    this.getBreweries();

    eventBus.$on("get-similar-breweries", brewery_type => (
      // (this.brewery_type = brewery_type)
      // .then
      (this.getSimilarBreweries(this.brewery_type))
    ))
    eventBus.$on("favourite-added", beer => this.markFavourite(beer));

  }
}
</script>
