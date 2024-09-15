<script>

import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js';

export default {
  data () {
    return {
      store
    }
  },
  components: { 
    AppHeader,
    AppMain
  },
  created() {
    this.getDataFromApi();
    this.getArchetypes();
  },
  methods: {
    getDataFromApi() {
      axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
          params: {
            archetype: this.store.searchArchetype
          }
        })
        .then((resp) => {
          this.store.allCards = resp.data.data; 
        })
        .catch((error) => {
          this.store.allCards = [];
        });
    },
    getArchetypes() {
      axios
      .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
      .then((resp) => {
        this.store.archetypes = resp.data
      })
    }
  }
}
</script>

<template>
  <div>
    <AppHeader />
    
    <AppMain @performSearch="getDataFromApi()" />

  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
@import "bootstrap/scss/bootstrap";
</style>
