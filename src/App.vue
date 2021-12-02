<template>
  <div id="app">
    <Header @searchClick='getResult' />

    <main class="py-3">
      <div v-if="filmsFind.length != 0 || seriesFind.length != 0">
        <!-- Film section -->
        <FilmSection 
        :Result="filmsFind"
        />
        <!-- TV Series section -->
        <FilmSection 
        :Result="seriesFind"
        />
      </div>
      <div v-else class="no-content">
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
  created() {
      this.getRandomCotent();
  },
  methods: {
    getResult(text) {
      if (text !== '') {
        const apiParams = {
            api_key: 'ea406b3b6df3538757d7eb19761ffa58',
            query: text,
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
    getRandomCotent() {
      let randomChar = '';
      const chars = 'abcdefghijklmnopqrstuvwxyz';

      randomChar = chars.charAt( Math.floor( Math.random() * chars.length));

      console.log('random letter:',randomChar);
      const apiParams = {
        api_key: 'ea406b3b6df3538757d7eb19761ffa58',
        query: randomChar,
      }
      /* Call API for FILM data */
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: apiParams,
      })
      .then(result => {
        this.filmsFind = result.data.results.slice(0, 6);
      })
      .catch(error => console.log(error));
      
      /* Call API for SERIES data */
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: apiParams,
      })
      .then(result => {
        this.seriesFind = result.data.results.slice(0, 6);
  
      })
      .catch(error => console.log(error));
    },
  }
}
</script>

<style lang="scss">
@import '@/styles/Global';
.no-content {
    height: 80.1vh;
    padding: 4rem 0;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: #dedede;
}
</style>
