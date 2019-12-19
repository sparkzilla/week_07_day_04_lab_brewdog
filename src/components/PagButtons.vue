<template lang="html">
  <button type="button" name="button" v-on:click="handleUpPageClick">Page Up</button>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name:'pag-buttons',
  methods: {
    handleUpPageClick(){
      eventBus.$emit('up-page', 1)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
