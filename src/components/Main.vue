<template>
  <main class="container-fluid">
      <div class="container">
          <div class="row p-5" v-if="cardMusics">
              <!-- elemento che potrà essere riutilizzato -->
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
          <div class="box-loading" v-else>
              <h1 class="loading">Caricamento...</h1>
          </div>
      </div>
  </main>
</template>

<script>
//azios
import axios from 'axios';
//importo elemento figlio
import MainAlbum from "./MainAlbum.vue"
export default {
    name: 'Main',
    //metto elemento figlio
    components: {
        MainAlbum,
    },
    data () {
        return {
            //conterrà tutti gli elementi dell'api
            cardMusics: null,
        }
    },
    created() {
        setTimeout (() => {
            axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                //guardare bene il collegamento
                this.cardMusics = response.data.response;
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
@import "../assets/scss/partials/_main.scss";
.container-fluid {
    background-color: $mainColor;
}
.box-loading {
    @include box-loading (100vh, white);
}
</style>