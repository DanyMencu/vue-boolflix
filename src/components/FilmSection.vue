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
              <img v-if="element.original_language === 'it'" src="../assets/it.png" :alt="element.original_language">
              <img v-else-if="element.original_language === 'en'" src="../assets/en.png" :alt="element.original_language">
              <p v-else>Lingua: {{ element.original_language }} </p>
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
img {
    width: 40px;
}
</style>