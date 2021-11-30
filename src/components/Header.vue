<template>
  <header class="p-3">
      <input type="text" placeholder="Quale film cerchi?"
        v-model.trim="SearchBarText" @keyup.enter="$emit('searchClick', SearchBarText)">
      <button @click="$emit('searchClick', SearchBarText)">Cerca</button>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            SearchBarText: '',
        }
    }

}
</script>

<style scoped lang="scss">
header {
    background-color: #dedede;
}

</style>