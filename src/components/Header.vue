<template>
  <header class="py-3">
      <div class="container">
          <div class="row justify-content-between align-items-center">
              <div class="col-4">
                  <div class="logo">
                    <img src="../assets/LogoBig.png" alt="Logo Pezzotto">
                  </div>
              </div>
              <div class="col-3 d-flex justify-content-between align-items-center">
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
    background: linear-gradient(#000, 70%, rgba(0, 0, 0, 0));

    .logo {
        overflow: hidden;
        width: 6%;
        transition: width 1.5s;
        position: relative;
        cursor: pointer;

        &:hover {
            width: 100%;
        }
    }

    input {
        background-color: transparent;
        border: 0px;
        border-bottom: 1px solid transparent;
        color: #444;

        &:hover {
            border-bottom:1px solid #333;
        }

        &:focus {
            outline: none;
            border-bottom:1px solid #333;
            color: #fff;
        }
    }

    .search_btn {
        background-color: #333;
        border: 1px solid #333;
        padding: 3px 15px;
        border-radius: 7px;
        color: #dedede;

        &:hover {
            background-color: #555;
        }
    }
}


</style>