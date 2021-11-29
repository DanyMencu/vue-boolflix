<template>
  <div id="app">
    <Header />

    <main>
      <!-- Film section -->
      <FilmSection />
    </main>
  </div>
</template>

<script>
/* import axios from 'axios'; */
import Header from './components/Header.vue';
import FilmSection from './components/FilmSection.vue';

export default {
  name: 'App',
  components: {
    Header,
    FilmSection,
  }
}
</script>

<style lang="scss">
@import '@/styles/Global';

</style>
