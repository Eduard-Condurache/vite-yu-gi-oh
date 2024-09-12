<script>

import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js';

export default {
  data () {
    return {
      store,
      allCards: []
    }
  },
  created() {
    axios
      .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=39&offset=0')
      .then((resp) => {
        this.store.allCards = resp.data.data
      })

  },
  components: {
    AppHeader,
    AppMain
  }
}
</script>

<template>
  <div>
    <AppHeader/>
    
    <AppMain />

  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
@import "bootstrap/scss/bootstrap";
</style>
