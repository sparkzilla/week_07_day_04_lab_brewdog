<template lang="html">
  <div v-if="beer">
    <h3>{{beer.name}}</h3>
    <p>{{beer.description}}</p>
    <img :src="beer.image_url"
    alt="beer image" height=200 />
    <sub>{{beer.tagline}}</sub>
    <button type="button" name="button"></button>
  </div>
</template>

<script>
export default {
  name: "beer-details",
  props: ['beer']
}
</script>

<style lang="css" scoped>
</style>
