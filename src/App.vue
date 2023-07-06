<script>
import axios from 'axios';

import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';
import { api } from './assets/data/index';
import { store } from './assets/data/store.js';

export default {
  components: { AppMain, AppHeader },
  computed: {
    axiosConfig() {
      const { key } = api;
      return {
        params: {
          api_key: key,
          query: store.titleFilter,
        }
      };
    }
  },
  methods: {
    fetchProductions() {
      if (!store.titleFilter) {
        store.movies = [];
        store.series = [];
        return;

      }
      this.fetchApi('search/movies', 'movies');
      this.fetchApi('search/tv', 'series');

    },
    fetchApi(endpoint) {
      axios.get(`${api.baseUri}/${endpoint}`, this.axiosConfig)
        .then(res => {
          store[target] = res.data.results;
        });
    }
  }
};


</script>

<template>
  <AppHeader @search-submit="fetchProductions" />
  <AppMain />
</template>

<style></style>
