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
      // Fetch movies based on title filter
      this.fetchApi('search/movie', 'movies');
      // Fetch series based on title filter
      this.fetchApi('search/tv', 'series');
    },
    // Add the 'target' parameter to specify the store property to update
    fetchApi(endpoint, target) {
      axios.get(`${api.baseUri}/${endpoint}`, this.axiosConfig)
        .then(res => {
          // Update the store property with the fetched data
          store[target] = res.data.results;
        });
    }
  }

};


</script>

<template>
  <!-- Display the AppHeader component and listen for search-submit event -->
  <AppHeader @search-submit="fetchProductions" />
  <AppMain />
</template>

<style></style>
