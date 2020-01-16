<template lang="html">
  <section>
    <ul id="beer-list">
      <li v-on:click="handleClick(index)" class="beer-item" :value="index" v-for="(beer, index) in beers">
        <img class="beer-image" :src="beer.image_url">
        <br/>
        <span>{{ beer.name }}</span>
      </li>
    </ul>
  </section>
</template>

<script>
import {eventBus} from '../main.js';
export default {
  name: 'beer-list',
  props: ['beers'],
  methods: {
    handleClick(index){
      eventBus.$emit('selected-beer', this.beers[index])
    }
  }
}
</script>

<style lang="css" scoped>

#beer-list{
  list-style-type: none;
  margin:0 auto;
}

.beer-image{
  max-height:150px;
}
.beer-item{
  margin-bottom:50px;
  display: inline-block;
  width: 150px;
  text-align:center;
}
</style>
