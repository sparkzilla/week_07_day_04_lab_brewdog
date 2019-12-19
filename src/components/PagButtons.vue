<template lang="html">
  <div class="">

  <div class="button-left">
  <button type="button" name="button" v-on:click="handleUpPageClick">Page Up</button>
  </div>
  <div class="button-right">
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
.button-right {
  display: inline-block;

}
.button-left {
  display: inline-block;
    margin-right: 10px;
}
</style>
