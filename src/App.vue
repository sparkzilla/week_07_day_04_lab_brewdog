<template>
  <div>
    <h1>Who's in the Doghouse?</h1>
    <page-buttons></page-buttons>
    <div class="main-container">

      <div class="beers-list-container column">
    <beers-list :beers='beers'></beers-list>
  </div>

  <div class="beer-details-container column">
    <beer-details :beer='selectedBeer'></beer-details>
  </div>

    <div class="fav-beers-container column">
    <fav-beers-list :favoriteBeers='favoriteBeers'></fav-beers-list>
    </div>
    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import {eventBus} from './main.js';
import BeerDetails from './components/BeerDetails.vue';
import FavBeersList from './components/FavBeersList.vue';
import PagButtons from './components/PagButtons.vue'

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favoriteBeers: [],
      currentPage: 1
    }
  },

methods: {
  page : function() {
    fetch(`https://api.punkapi.com/v2/beers?page=${this.currentPage}`)
    .then(res => res.json())
    .then(beers => this.beers = beers)
  }
},

mounted(){
  fetch(`https://api.punkapi.com/v2/beers?page=${this.currentPage}`)
  .then(res => res.json())
  .then(beers => this.beers = beers)

  eventBus.$on('beer-selected',(beer) => {
    this.selectedBeer = beer;
  })

  eventBus.$on('fav-beer-selected', (beer) => {
    this.favoriteBeers.push(beer)
  })
  eventBus.$on('up-page', (number) => {
    this.currentPage = this.currentPage + number
    this.page();
  })
  eventBus.$on('down-page', (number) => {
    if (this.currentPage !== 1){
    this.currentPage = this.currentPage + number
      this.page()};
  })

},

components: {
  "beers-list": BeersList,
  "beer-details": BeerDetails,
  "fav-beers-list": FavBeersList,
  "page-buttons": PagButtons
}

}
</script>

<style>
.main-container{
  display: flex;
  justify-content: space-around;
}
.column{
  max-width: 350px;
}

</style>
