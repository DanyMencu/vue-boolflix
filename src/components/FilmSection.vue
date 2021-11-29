<template>
  <main>
      <ul class="py-2" v-for="element in Films" :key="`FilmID-${element.id}`">
          <li>
              <h2>Titolo: {{ element.title }} </h2>
            </li>
          <li>
              <h4>Titolo originale: {{ element.original_title }} </h4>
          </li>
          <li>
              <p>Lingua: {{ element.original_language }} </p>
          </li>
          <li>
              <p>Voto: {{ element.vote_average }} </p>
          </li>
      </ul>
  </main>
</template>

<script>
export default {
    name: 'FilmSection',
    props: {
        Films: Array,
    },
    data() {
        return {
            
        }
    }
}
</script>

<style scoped lang="scss">

ul:nth-child(odd) {
    background-color: #cdcdcd;
}
</style>