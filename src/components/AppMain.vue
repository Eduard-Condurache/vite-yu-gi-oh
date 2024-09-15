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
  },
  methods: {
    performSearch() {

      this.$emit('performSearch');
    }
  }
}
</script>

<template>
  <main>
    <div class="container">
      <div class="py-3 w-50">
        <select 
          v-model="store.searchArchetype" 
          class="form-control w-25"
          @change="performSearch">

          <option value="">Select Archetype</option>
          <option 
            v-for="(archetype, index) in store.archetypes" 
            :key="index"
            :value="archetype.archetype_name">
            {{ archetype.archetype_name }}
            </option>
        </select>
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
