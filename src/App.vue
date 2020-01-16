<template>
  <div id="app">
    <div id="left-column">
      <div id="beer-list">
        <beer-list :beers="beers"></beer-list>
      </div>
    </div>
    <div id="right-column">
      <div id="selected-beer-details">
        <selected-beer-details :beer="selectedBeer"></selected-beer-details>
      </div>
      <div id="favourite-beers">
        <favourite-beers :favouritebeers="favouriteBeers"></favourite-beers>
      </div>
    </div>
  </div>
</template>

<script>

import {eventBus} from './main.js';
import BeerList from './components/BeerList.vue';
import SelectedBeerDetails from './components/SelectedBeerDetails.vue';
import FavouriteBeersList from './components/FavouriteBeersList.vue';

export default {
  name: 'app',
  components: {
    "beer-list": BeerList,
    "selected-beer-details": SelectedBeerDetails,
    "favourite-beers": FavouriteBeersList
  },
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
      .then(response => response.json())
      .then(beers => this.beers = beers)
      // .then(cheese => this.favouriteBeers.push(this.beers[0]))

    eventBus.$on('selected-beer', (beer) =>{
      this.selectedBeer = beer;
    });

    eventBus.$on('favourite-beer', (beer) => {
      this.favouriteBeers.push(beer);
    });
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
  /* margin-top: 0px; */
  display: flex;
  flex-direction: row;
}

#left-column{
  width: 75%;
}

#right-column{
    display: flex;
    flex-direction: row;
    /* width:300px; */
    overflow: scroll;
}

#beer-list{

}

#selected-beer-details{
  min-height:10%;
  position: fixed;
}

#favourite-beers{
  position:fixed;
  margin-top:500px;
}



</style>
