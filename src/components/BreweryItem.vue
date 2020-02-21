<template lang="html">
  <div id="brewery-item">
    <p>In the brewery item </p>

    <p>{{ brewery }} </p>
    <!--<p>{{ brewery.brewery_type}} </p> -->
  </div>
</template>

<script>
import { eventBus } from '../main.js'
import BreweryList from './BreweryList.vue'


export default {
    name: "brewery-item",
    props: ['brewery']
    // eventBus.$emit("brewery-selected", this.brewery);


}
</script>

<style lang="css" scoped>
</style>
