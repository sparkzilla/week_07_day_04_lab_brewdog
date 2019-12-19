<template lang="html">
  <button type="button" name="button" v-on:click="handleFavClick">Add to Favorites</button>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name:'add-fav-button',
  props: ['beer'],
  methods: {
    handleFavClick(){
      eventBus.$emit('fav-beer-selected', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
