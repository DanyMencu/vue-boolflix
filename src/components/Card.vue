<template>
  <div class="card py-2">
      <ul>
          <li>
              <img :src="`https://image.tmdb.org/t/p/w92/${poster}`" :alt="originalTitle"></li>
          <li> <strong>Titolo:</strong> {{ title }}
          </li>
          <li> <strong>Titolo Originale: </strong> {{ originalTitle }}</li>
          <li class="language">
              <strong>Lingua: </strong>
                <img 
                v-if="languageAvailable.includes(language)"
                :src="require(`../assets/${language}.png`)" :alt="language"
                />
                <span v-else> {{ language }}</span>
          </li>
          <li><strong>Voto: </strong>{{ vote }} </li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        poster: String,
    },
    data() {
        return {
            languageAvailable: ['it', 'en','es','fr','de','ja',],
        }
    },
    computed: {
        isAvailable() {
            return this.languageAvailable.includes(this.language);
        }
    },
}
</script>

<style scoped lang="scss">

ul {
    list-style: none;
    padding-left: 1rem;

    .language {
        img {
            width: 30px;
        }
    }
}

</style>