<template lang="html">
  <div id="brewery-details" >
    <p> Brewery Type: {{ brewery.brewery_type }} </p>
    <p> Brewery Address: {{ brewery.street }}, {{ brewery.city }}, {{ brewery.state }}, {{ brewery.country }}</p>
    <p> Brewery Website: <a href> {{ brewery.website_url }}</a></p>
    <input type='submit' value='Same Type Of Brewery' v-on:click="getSimilarBrewerys" />
  </div>

</div>
</template>

<script>
import { eventBus } from '../main.js'
import BreweryList from './BreweryList.vue'
import BreweryItem from './BreweryItem.vue'

export default {
  name: 'brewery-details',
  props: ['brewery'],
  methods: {

    getSimilarBrewerys: function() {
      console.log(`within brewery details, brewery type : ${this.brewery.brewery_type}`)
      eventBus.$emit("get-similar-brewerys", this.brewery.brewery_type);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
