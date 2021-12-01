<template>
  <div class="container">
      <div class="row">
        <!-- V-FOR per il contenuto dell'array RESULT -->
        <div class="col-2 px-1 py-4" v-for="element in Result" :key="`Film ID-${element.id}`">
          <Card 
              :poster="element.poster_path"
              :title="element.title ? element.title : element.name"
              :originalTitle="element.original_title ? element.original_title : element.original_name"
              :language="element.original_language"
              :overview="element.overview"
              :vote="element.vote_average"
          />
        </div>
      </div>
  </div>
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