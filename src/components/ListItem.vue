<template lang="html">
  <li v-on:mouseover="handleClick">{{beer.name}}</li>

</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'list-item',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('beer-selected', this.beer)
    }
  },
}
</script>

<style lang="css" scoped>
li {
  margin: 10px 0;
}
</style>
