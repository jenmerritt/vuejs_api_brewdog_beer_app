<template>
  <div id="app">
    <beer-list :beers="beers"></beer-list>
  </div>
</template>

<script>

import {eventBus} from './main.js';
import BeerList from './components/BeerList.vue';

export default {
  name: 'app',
  components: {
    "beer-list": BeerList
  },
  data(){
    return {
      beers: []
    };
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
