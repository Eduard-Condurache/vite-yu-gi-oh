<script>
import SingleCard from './SingleCard.vue';
import { store } from '../store.js';

export default {
  data() {
    return {
      store
    }
  },
  components: {
    SingleCard
  }
}
</script>

<template>
  <main>
    <div class="container">
      <div class="dropdown py-3 text-start">
        <button class="btn btn-light dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
          Alien
        </button>
      </div>
    </div>
    <div class="container bg-white p-5">
      <header class="p-3">
        <h4>
          Found
          {{ store.allCards.length }}
          cards
        </h4>
      </header>

      <div class="cards-container">
        <div v-for="(card, index) in store.allCards" :key="index" class="single-card">
          <SingleCard :card="card"/>
        </div>
      </div>
    </div>
    
  </main>
</template>

<style lang="scss" scoped>
 main {
  background-color: #D48F38;

  .container {
    header {
      width: calc(100% - 31px);
      margin: 0 auto;
      background-color: #212529;
      text-align: start;
      color: white;
    }
  }

  .cards-container {
    display: flex;
    flex-wrap: wrap;
    background-color: white;
    .single-card {
      width: calc(100% / 5 - 30px);
      margin: 0 15px;
      margin-bottom: 20px;
      background-color: #D48F38;
    }
  }
 }

 
</style>
