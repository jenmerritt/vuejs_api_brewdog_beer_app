<template lang="html">
  <div>
    <h1>Favourite Beers</h1>
    <ul id="favourite-beers-list">
      <li class="beer-item" v-for="beer in favouritebeers">
        <img class="beer-image" :src="beer.image_url"/>
        <br/>
        <span>{{ beer.name }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name:'favourite-beers-list',
  props: ['favouritebeers']
}
</script>

<style lang="css" scoped>

.beer-image{
    max-height:200px;
}

#favourite-beers-list{
  list-style-type: none;
  margin:0 auto;
}

.beer-item{
  margin-bottom:50px;
  display: inline-block;
  width: 200px;
  text-align:center;
}

</style>
