<template lang="html">
<div id="brewery-list" v-if="brewerys.length">
<!-- <div id="brewery-list"> -->

  <ul>
    <brewery-item v-for="(brewery, index) in brewerys" :brewery="brewery" :key='index'></brewery-item>
  </ul>
</div>
</template>

<script>
import { eventBus } from '../main.js'
import BreweryItem from './BreweryItem.vue'
export default {
  name: 'brewery-list',
  props: ['brewerys'],
  components: {
    "brewery-item": BreweryItem
  }
}
</script>

<style lang="css" scoped>
</style>
