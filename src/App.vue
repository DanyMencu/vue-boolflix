<template>
  <div id="app">
    <Header @searchClick='filmChosen' />

    <main>
      <!-- Film section -->
      <FilmSection :Films="filmsFind"/>
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
      };
  },
  methods: {
    SearchFilms(text) {
      /* Call API for data */
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
    },
    filmChosen(text) {
        this.filmSelected = text;

        this.SearchFilms()
    },
  }
}
</script>

<style lang="scss">
@import '@/styles/Global';

</style>
