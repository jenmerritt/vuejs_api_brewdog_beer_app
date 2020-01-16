<template lang="html">
  <div>
    <h1>Favourite Beers</h1>
    <ul>
      <li v-for="beer in favouritebeers">
        <img class="beer-image" :src="beer.image_url"/>
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
    max-height:150px;
  }
</style>
