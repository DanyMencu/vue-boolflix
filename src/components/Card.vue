<template>
<div class="card align-items-center justify-content-center">
    <div class="poster">
        <img v-if="poster" :src="`https://image.tmdb.org/t/p/w154/${poster}`" :alt="originalTitle">
        <img v-else class="error-img" src="../assets/404.png" alt="404 Error not found">
    </div>
    <div class="descritpion">
        <ul class="d-flex flex-column justify-content-center">
            <li> <strong>Titolo:</strong> {{ title }}
            </li>
            <li> <strong>Titolo Originale: </strong> {{ originalTitle }}</li>
            <li v-if="overview.length === 0" class="language">
                <strong>Lingua: </strong>
                    <img 
                    v-if="languageAvailable.includes(language)"
                    :src="require(`../assets/${language}.png`)" :alt="language"
                    />
                <span v-else> {{ language }}</span>
            </li>
            <li v-else>
                <span v-if="overview.length > 100"><strong>Descrizione: </strong> {{ overview.slice(0, 100) }}...</span>
                <span v-else><strong>Descrizione: </strong> {{ overview }}</span>
            </li>
            <li><strong>Voto: </strong>
                <i class="fas fa-star yellow" v-for="(n, i) in Math.ceil(vote / 2)" :key="i" ></i>
                <i class="far fa-star" v-for="(n, i) in (5 - Math.ceil(vote / 2))" :key="`EmpyStar-${i}`" ></i>
            </li>
        </ul>
    </div>
</div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        originalTitle: String,
        overview: String,
        language: String,
        vote: Number,
        poster: String,
    },
    data() {
        return {
            languageAvailable: ['it', 'en','es','fr','de','ja',],
        }
    },
    computed: {
        isAvailable() {
            return this.languageAvailable.includes(this.language);
        }
    },
}
</script>

<style scoped lang="scss">
.card {
    height: 250px;
    position: relative;
    margin: 0 auto;
    background-color: #fff;
    border: 0;
    border-radius: 0;
    cursor: pointer;
    overflow: hidden;

    .yellow {
        color: rgb(255, 251, 0);
    }
    &:hover .descritpion {
        opacity: 100%;
    }

    .poster {
        width: 100%;
        height: 100%;
        overflow: hidden;


        img {
            height: 100%;
            width: 100%;
        }
    }
}
.error-img {
    width: 154px;
}

.descritpion {
    height: 100%;
    width: 100%;
    position: absolute;
    display: flex;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.7);
    opacity: 0;
    transition: opacity 0.4s;
}

ul {
    width: 100%;
    height: 100%;
    list-style: none;
    padding: 0 0 0 10px;
    margin: 0;
    color: #ededed;

    strong {
        color: #fff;
    }

    .language {
        img {
            width: 30px;
        }
    }
}

</style>