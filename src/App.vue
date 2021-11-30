<template>
  <div id="app">
    <Header @searchClick='getResult' />

    <main>
      <!-- Film section -->
      <FilmSection 
      :Films="filmsFind"
      :Series="seriesFind"
      />
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import FilmSection from './components/FilmSection.vue';

export default {
  name: 'App',
  components: {
    Header,
    FilmSection,
  },
  created() {
  },
  data() {
      return {
        filmsFind: [],
        seriesFind: [],
      };
  },
  methods: {
    getResult(text) {
      /* Call API for FILM data */
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'ea406b3b6df3538757d7eb19761ffa58',
          query: text,
          language: 'it-IT',
        }
      })
      .then(result => {
        console.log(result.data.results);
        this.filmsFind = result.data.results;

      })
      .catch(error => console.log(error));

      /* Call API for SERIES data */
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: 'ea406b3b6df3538757d7eb19761ffa58',
          query: text,
          language: 'it-IT',
        }
      })
      .then(result => {
        console.log(result.data.results);
        this.seriesFind = result.data.results;

      })
      .catch(error => console.log(error));
    },
  }
}
</script>

<style lang="scss">
@import '@/styles/Global';

</style>
