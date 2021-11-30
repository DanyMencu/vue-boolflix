<template>
  <main>
      <div class="col" v-for="element in Films" :key="element.id">
        <Card 
            :title="element.title"
            :originalTitle="element.original_title"
            :lenguage="element.original_lenguage"
            :vote="element.vote_average"
        />
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
    },
    data() {
        return {
        
        }
    },

}
</script>

<style scoped lang="scss">

</style>