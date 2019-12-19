<template>
  <div>
    <h1>Who's in the Doghouse</h1>
    <div class="main-container">
    <fav-beers-list :favoriteBeers='favoriteBeers'></fav-beers-list>
    <beers-list :beers='beers'></beers-list>
    <beer-details :beer='selectedBeer'></beer-details>

    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import {eventBus} from './main.js';
import BeerDetails from './components/BeerDetails.vue';
import FavBeersList from './components/FavBeersList.vue';

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favoriteBeers: [],
    }
  },

mounted(){
  fetch('https://api.punkapi.com/v2/beers?per_page=80')
  .then(res => res.json())
  .then(beers => this.beers = beers)

  eventBus.$on('beer-selected',(beer) => {
    this.selectedBeer = beer;
  })

  eventBus.$on('fav-beer-selected', (beer) => {
    this.favoriteBeers.push(beer)
  })

},

components: {
  "beers-list": BeersList,
  "beer-details": BeerDetails,
  "fav-beers-list": FavBeersList
}

}
</script>

<style>
.main-container{
  display: flex;
  justify-content: space-around;
}
</style>
