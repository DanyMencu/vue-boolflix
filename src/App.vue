<template>
  <div id="app">
    <Header @searchClick='getResult' />

    <main>
      <div v-if="filmsFind.length != 0 && seriesFind.length != 0">
        <!-- Film section -->
        <FilmSection 
        :Result="filmsFind"
        />

        <FilmSection 
        :Result="seriesFind"
        />
      </div>
      <div v-else class="empty">
        <h2>Cerca un film/serie TV che ti interessa...</h2>
      </div>
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
  data() {
      return {
        filmsFind: [],
        seriesFind: [],
      };
  },
  methods: {
    getResult(text) {
      if (text !== '') {
        const apiParams = {
            api_key: 'ea406b3b6df3538757d7eb19761ffa58',
            query: text,
            language: 'it-IT',
        }

        /* Call API for FILM data */
        axios.get('https://api.themoviedb.org/3/search/movie', {
          params: apiParams,
        })
        .then(result => {
          this.filmsFind = result.data.results;
  
        })
        .catch(error => console.log(error));
  
        /* Call API for SERIES data */
        axios.get('https://api.themoviedb.org/3/search/tv', {
          params: apiParams,
        })
        .then(result => {
          this.seriesFind = result.data.results;
  
        })
        .catch(error => console.log(error));
      }
    },
  }
}
</script>

<style lang="scss">
@import '@/styles/Global';

main {
  background-color: #555;
}

.empty {
    height: 87vh;
    padding: 4rem 0;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: #dedede;
}
</style>
