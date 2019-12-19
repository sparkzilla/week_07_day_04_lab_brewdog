<template>
  <h1>The Page</h1>
</template>

<script>
import BeersList from ('./components/BeersList.vue');

export default {
  name: 'app',
  data(){
    return {
      beers: []
    }
  },

mounted(){
  fetch('https://api.punkapi.com/v2/beers')
  .then(res => res.json())
  .then(beers => this.beers = beers)
},
components: {
  "beers-list": BeersList
}

}
</script>

<style>

</style>
