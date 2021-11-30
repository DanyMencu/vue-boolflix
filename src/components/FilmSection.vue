<template>
  <main>
      <div v-if="Films.length != 0">
      <!-- V-FOR per i FILM -->
      <div class="col px-1 py-2" v-for="element in Films" :key="`Film ID-${element.id}`">
        <Card 
            :poster="element.poster_path"
            :title="element.title"
            :originalTitle="element.original_title"
            :language="element.original_language"
            :vote="element.vote_average"
        />
      </div>
            <!-- V-FOR per le SERIE -->
      <div class="col px-1 py-2" v-for="element in Series" :key="`Serie ID-${element.id}`">
        <Card 
            :poster="element.poster_path"
            :title="element.name"
            :originalTitle="element.original_name"
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
        Films: Array,
        Series: Array,
    },
}
</script>

<style scoped lang="scss">

main {
    background-color: #555;
}

.empty {
    padding: 4rem 0;
    text-align: center;
    color: #dedede;
}
</style>