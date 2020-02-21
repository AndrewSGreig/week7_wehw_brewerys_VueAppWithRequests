<template lang="html">
  <div id="brewery-item">
    <p>_____________________________ </p>
    <p v-on:click="handleClick">{{ brewery.name }} </p>
    <p>State: {{ brewery.state }} </p>
    <brewery-details v-if="clicked" :brewery="brewery">{{ brewery.name }}</brewery-details>

    <!--<p>{{ brewery.brewery_type}} </p> -->
  </div>
</template>

<script>
import { eventBus } from '../main.js'
import BreweryList from './BreweryList.vue'
import BreweryDetails from './BreweryDetails.vue'


export default {
  name: "brewery-item",
  props: ['brewery'],
  // eventBus.$emit("brewery-selected", this.brewery);
  data() {
    return{
      clicked :false
    }
  },
  components: {
    'brewery-details': BreweryDetails
  },
  methods: {
    handleClick(){
      if (!this.clicked){
        this.clicked = true;
      }else{
        this.clicked=false;
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
