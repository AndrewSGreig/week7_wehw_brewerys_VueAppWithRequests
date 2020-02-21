<template lang="html">
  <div id="brewery-details" >
    <p> Welcome to brewery details </p>
    <p> Brewery Type: {{ brewery.brewery_type }} </p>
    <p> Brewery Website: {{ brewery.website_url }}</p>
    <!-- <p>{{ brewery.brewery_type }} </p>
    <p>{{ brewery.website_url }} </p> -->
  </div>
</template>

<script>
import { eventBus } from '../main.js'
import BreweryList from './BreweryList.vue'
import BreweryItem from './BreweryItem.vue'

export default {
  name: 'brewery-details',
  props: ['brewery']
}
</script>

<style lang="css" scoped>
</style>
