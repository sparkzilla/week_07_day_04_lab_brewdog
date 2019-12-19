<template>
  <div>
    <h1>Who's in the Doghouse</h1>
    <div class="main-container">


    <beers-list :beers='beers'></beers-list>
    <beer-details :beer='selectedBeer'></beer-details>
    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import {eventBus} from './main.js';
import BeerDetails from './components/BeerDetails.vue'

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null
    }
  },

mounted(){
  fetch('https://api.punkapi.com/v2/beers')
  .then(res => res.json())
  .then(beers => this.beers = beers)

  eventBus.$on('beer-selected',(beer) => {
    this.selectedBeer = beer;
  })
},

components: {
  "beers-list": BeersList,
  "beer-details": BeerDetails
}

}
</script>

<style>
.main-container{
  display: flex;
  justify-content: space-around;
}
</style>
