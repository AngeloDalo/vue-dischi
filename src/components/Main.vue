<template>
  <main class="container-fluid">
      <div class="container">
          <div class="row p-5" v-if="cardMusics">
              <MainAlbum
                    v-for="(cardMusic, index) in cardMusics"
                    :key="index"
                    :src = "cardMusics[index].poster"
                    :alt = "cardMusics.title"
                    :title = "cardMusic.title"
                    :author = "cardMusic.author"
                    :year = "cardMusic.year" 
              /> 
          </div>
          <div v-else>
              <h1 class="loading">Caricamento...</h1>
          </div>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import MainAlbum from "./MainAlbum.vue"
export default {
    name: 'Main',
    components: {
        MainAlbum,
    },
    data () {
        return {
            cardMusics: null,
        }
    },
    created() {
        setTimeout (() => {
            axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.cardMusics = response.data.response;
                console.log(this.cardMusics.poster);
            })
            .catch(function (error) {
                console.log(error);
            });
        }, 1000);
    },
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
.container-fluid {
    background-color: $mainColor;
}
.loading {
    color: white;
}
</style>