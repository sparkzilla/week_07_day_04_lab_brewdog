<template lang="html">
  <div v-if="beer">
    <h3>{{beer.name}}</h3>
    <p>{{beer.description}}</p>
    <img :src="beer.image_url"
    alt="beer image" height=200 />
    <sub>{{beer.tagline}}</sub>
    <div class="button">
    <add-fav-button :beer='beer'></add-fav-button>
  </div>
  </div>
</template>

<script>
import AddFavButton from './AddFavButton.vue';

export default {
  name: "beer-details",
  props: ['beer'],

  components: {
    "add-fav-button": AddFavButton
  }
}
</script>

<style lang="css" scoped>
.button {
  margin: 10px 0;
}
</style>
