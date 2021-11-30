<template>
  <div class="card">
      <ul class="py-2">
          <li>Titolo: {{ title }}</li>
          <li>Titolo Originale: {{ originalTitle }}</li>
          <li class="lenguage">
              Lingua:
                <img 
                v-if="isAvailable"
                :src="require(`../assets/${lenguage}.png`)" :alt="lenguage"
                />
                <span v-else> {{lenguage}}</span>
          </li>
          <li>Voto: {{ vote }} </li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        originalTitle: String,
        lenguage: String,
        vote: Number,
    },
    data() {
        return {
            lenguageAvailable: ['it', 'en',],
        }
    },
    computed: {
        isAvailable() {
            return this.lenguageAvailable.includes(this.lenguage);
        }
    },
}
</script>

<style scoped lang="scss">

ul {
    &:nth-child(odd) {
    background-color: #cdcdcd;
    }
    .lenguage {
        img {
            width: 30px;
        }
    }
}

</style>