<template lang="html">
<div id="brewery-list" v-if="breweries.length">
<!-- <div id="brewery-list"> -->

  <ul>
    <brewery-item v-for="(brewery, index) in breweries" :brewery="brewery" :key='index'></brewery-item>
  </ul>
</div>
</template>

<script>
import { eventBus } from '../main.js'
import BreweryItem from './BreweryItem.vue'
export default {
  name: 'brewery-list',
  props: ['breweries'],
  components: {
    "brewery-item": BreweryItem
  }
}
</script>

<style lang="css" scoped>
</style>
