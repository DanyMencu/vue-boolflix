<template>
  <main class="container">
      <div class="row" v-if="Result.length != 0">
        <!-- V-FOR per il contenuto dell'array RESULT -->
        <div class="col-2 p-1" v-for="element in Result" :key="`Film ID-${element.id}`">
          <Card 
              :poster="element.poster_path"
              :title="element.title ? element.title : element.name"
              :originalTitle="element.original_title ? element.original_title : element.original_name"
              :language="element.original_language"
              :vote="element.vote_average"
          />
        </div>
      </div>

      <div v-else class="empty">
        <h2>Cerca un film/serie TV che ti interessa...</h2>
      </div>
  </main>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
    name: 'FilmSection',
    components: {
        Card,
    },
    props: {
        Result: Array,
    },
}
</script>

<style scoped lang="scss">
</style>