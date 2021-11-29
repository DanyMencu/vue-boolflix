<template>
  <header>
      <input type="text" placeholder="Quale film cerchi?"
        v-model="SearchBar">
      <button>Cerca</button>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            SearchBar: '',

        }
    }

}
</script>

<style scoped lang="scss">

</style>