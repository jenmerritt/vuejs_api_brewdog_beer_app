<template lang="html">
  <section id="details" v-if="beer">
    <h1>{{ beer.name }}</h1>
    <!-- <img class="beer-image" :src="beer.image_url"> -->
    <button v-on:click="handleClick">Add to Favourites</button>
    <p>{{ beer.tagline }}</p>
    <p>{{ beer.abv }}%</p>
    <p>{{ beer.description }}</p>
  </section>
</template>

<script>
import {eventBus} from '../main.js';
export default {
  name: 'selected-beer-details',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('favourite-beer', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>

.beer-image{
  max-height:150px;
}

button{
  background-color: #fff;
  border: none;
  color: #000 !important;
  padding: 10px;
  text-decoration: none;
  font-size: 12pt;
  cursor: pointer;
  /* margin-top:30px; */
}

button:hover {
  background-color: #d3d3d3;
  border: none;
  color: #000000 !important;
  padding: 10px;
  text-decoration: none !important;
  font-size: 12pt;
  /* margin-top:30px; */
}

</style>
