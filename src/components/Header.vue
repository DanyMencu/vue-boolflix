<template>
  <header class="py-3">
      <div class="container">
          <div class="row justify-content-between align-items-center">
              <div class="col-4">
                  <div class="logo">
                    <img src="../assets/LogoBig.png" alt="Logo Pezzotto">
                  </div>
              </div>
              <div class="col-4 d-flex justify-content-end align-items-center">
                  <div class="search d-flex justify-content-between">
                    <input type="text" placeholder="Cerca..."
                        v-model.trim="SearchBarText" @keyup.enter="$emit('searchClick', SearchBarText)">
                    <button 
                        class="search_btn"
                        @click="$emit('searchClick', SearchBarText)"
                    >
                        <i class="fas fa-search"></i>
                    </button>
                  </div>
                  <div class="d-flex justify-content-between align-items-center">
                    <button class="log">Log in</button>
                    <button class="log up">Sing up</button>
                  </div>
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
        min-width: 125px;
        background-color: transparent;
        border: 0px;
        border-bottom: 1px solid transparent;
        color: #444;
        opacity: 0;
        transition: opacity 0.25s;

        &:hover {
            border-bottom:1px solid #333;
        }

        &:focus {
            outline: none;
            border-bottom:1px solid #333;
            color: #fff;
            opacity: 100%;
        }
    }

    .search_btn {
        background-color: transparent;
        border: 0;
        padding: 10px 20px 0 0;
        border-radius: 50%;
        color: #dedede;

    }
    .search {
        width: 50%;
        &:hover input {
            opacity: 100%;
        }
    }

    .log {
        border: 0;
        padding: 0 7px 2px;
        margin: 3px;
        border-radius: 10px;
        font-weight: 600;

        &:hover {
            transform: scale(1.05);
        }
    }
    .up {
        color: #dedede;
        background-color: #dc1a28;
    }
}


</style>