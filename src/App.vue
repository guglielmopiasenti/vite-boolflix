<script>
import axios from 'axios';
const endpoint = 'https://api.themoviedb.org/3/search/movie?api_key=417ff78debed7617bb96dc46540a0f3d';
import AppMain from './components/AppMain.vue';
import { store } from './assets/data/store.js';

export default {
  components: { AppMain, },

  created() {
    // Fetching data from the specified endpoint using axios
    axios.get(endpoint).then(res => {
      // Assigning the received data to the 'movies' property in the store
      store.movies = res.data.docs;
    });
  },
}

</script>

<template>
  <AppMain />
</template>

<style></style>
