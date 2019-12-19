<template lang="html">
  <div class="">

  <div class="">
  <button type="button" name="button" v-on:click="handleUpPageClick">Page Up</button>
  </div>
  <div class="">
  <button type="button" name="button" v-on:click="handleDownPageClick">Page Down</button>
  </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name:'pag-buttons',
  methods: {
    handleUpPageClick(){
      eventBus.$emit('up-page', 1)
    },
    
    handleDownPageClick(){
      eventBus.$emit('down-page', -1)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
