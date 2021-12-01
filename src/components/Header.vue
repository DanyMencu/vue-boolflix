<template>
  <header class="py-3">
      <div class="container">
          <div class="row justify-content-between align-items-center">
              <div class="col-4">
                  <div class="logo">
                    <img src="../assets/LogoBig.png" alt="Logo Pezzotto">
                  </div>
              </div>
              <div class="col-3">
                    <input type="text" placeholder="Quale film cerchi?"
                        v-model.trim="SearchBarText" @keyup.enter="$emit('searchClick', SearchBarText)">
                    <button class="search_btn"
                        @click="$emit('searchClick', SearchBarText)"
                    >
                        Cerca
                    </button>
              </div>
          </div>
      </div>
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
    background-color: #000;
    height: 13vh;

    .logo {
        overflow: hidden;
        width: 6%;
        transition: width linear 2s;
        position: relative;
        cursor: pointer;

        &:hover {
            width: 100%;
        }
    }

    .search_btn {
        background-color: #ededed;border: 1px solid #fff;
    }

}


</style>