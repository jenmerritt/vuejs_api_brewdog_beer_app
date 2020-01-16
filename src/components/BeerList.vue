<template lang="html">
  <section>
    <ul>
      <li class="beer-item" v-for="beer in beers">
        <span>{{ beer.name }}</span>
        <img class="beer-image" :src="beer.image_url">
        <button>Add to Favourites</button>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'beer-list',
  props: ['beers']
}
</script>

<style lang="css" scoped>
.beer-image{
  max-height:150px;
}
.beer-item{
  margin-bottom:50px;
}
</style>
