<template lang="html">
  <div id="full-list">
    <h1>FAVOURITE BEERS</h1>
    <ul id="favourite-beers-list">
      <li class="beer-item" v-for="(beer, index) in favouritebeers">
        <img class="beer-image" :src="beer.image_url"/>
        <br/>
        <span>{{ beer.name }}</span>
        <button v-on:click="removeBeer(index)">Remove from Favourites</button>
      </li>
    </ul>
  </div>
</template>

<script>
import {eventBus} from '../main.js';
export default {
  name:'favourite-beers-list',
  props: ['favouritebeers'],
  methods: {
    removeBeer(index){
      this.favouritebeers.splice(index, 1);
      eventBus.$emit('favourite-beers', this.favouritebeers);
    }
  }
}
</script>

<style lang="css" scoped>

#full-list{
  background-color: #fff;
  margin:0 auto;
  width:83%;
  padding:35px;
  /* border: 2px solid white; */
}

#full-list h1{
  color: #1ba7cd;
  text-align:center;
}

.beer-image{
    max-height:200px;
}

#favourite-beers-list{
  list-style-type: none;
  margin: 0 auto;
}

.beer-item{
  /* margin-bottom:0px;
  margin-left: 0px; */
  margin: 5px;
  padding:15px;
  display: inline-block;
  width: 170px;
  text-align: center;
  border: 3px solid #1ba7cd;

}

button{
  background-color: #1ba7cd;
  border: none;
  color: #fff !important;
  padding: 10px;
  text-decoration: none;
  font-size: 12pt;
  cursor: pointer;
  margin-top:30px;
}

button:hover {
  background-color: #d3d3d3;
  border: none;
  color: #000000 !important;
  padding: 10px;
  text-decoration: none !important;
  font-size: 12pt;
  margin-top:30px;
}

</style>
