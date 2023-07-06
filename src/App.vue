<script>
import axios from 'axios';

import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';
import { api } from './assets/data/index';
import { store } from './assets/data/store.js';

export default {
  components: { AppMain, AppHeader },

  methods: {

    fetchMovies() {
      if (!store.titleFilter) {
        store.movies = [];
        return;
      };

      const { key, baseUri } = api

      const axiosConfig = {
        params: {
          api_key: key,
          query: store.titleFilter,
        }
      }

      axios.get(`${baseUri}/search/movie`, axiosConfig)
        .then(res => {
          store.movies = res.data.results
        });
    },
  }
}

</script>

<template>
  <AppHeader @search-submit="fetchMovies" />
  <AppMain />
</template>

<style></style>
