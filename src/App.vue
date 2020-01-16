<template>
  <div id="app">
    <div id="header">
      <a id="back-to-top"><h1>BREWDOG BEER APP</h1></a>
      <a href="#favourites-link"><p>View Favourites</p></a>
    </div>
    <div id="container">
      <div id="left-column">
        <div id="beer-list">
          <beer-list :beers="beers"></beer-list>
        </div>
        <div id="favourite-beers">
          <a id="favourites-link"><favourite-beers :favouritebeers="favouriteBeers"></favourite-beers></a>
          <a href="#back-to-top">^ back to top</a>
        </div>
      </div>
      <div id="right-column">
        <div id="selected-beer-details">
          <selected-beer-details :beer="selectedBeer"></selected-beer-details>
        </div>
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
    for (var i = 1; i < 6; i++) {
       let apiaddress = `https://api.punkapi.com/v2/beers?page=${i}&per_page=80`
       fetch(apiaddress)
         .then(response => response.json())
         .then(beers => this.beers=this.beers.concat(beers))
     }

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
  margin:0;
  padding:20px;
  background-color: #1ba7cd;;
}

h1{
  color: #fff;
  font-size:40px;
}

#header{
  margin-left:50px;
}

#header a{
  text-decoration:none;
  color:#fff;
  font-weight:bold;
}

#header a:hover{
  text-decoration:underline;
  font-weight:bold;
}


#favourite-beers a{
  text-decoration:none;
  color:#fff;
  font-weight:bold;
}

#favourite-beers a:hover{
  text-decoration:underline;
  font-weight:bold;
}

#container{
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
  /* min-height:10%; */
  position: fixed;
  margin-right:40px;
  padding-top:0px;
  margin-top: -40px;
}

#favourite-beers{
  /* position:fixed;
  margin-top:500px; */
}



</style>
