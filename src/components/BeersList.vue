<template lang="html">
<div class="list-container">
  <ul>
    <list-item v-for="(beer, index) in beers" :beer="beer" :key="index"></list-item>
  </ul>

</div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'beers-list',
  props: ['beers'],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
.list-container {
  min-width: 350px;
}

ul {
  list-style-type: none;

}
</style>
