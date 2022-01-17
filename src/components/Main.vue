<template>
  <main>
      <div class="container">
          <div class="row">
              <MainAlbum
                    v-for="(cardMusic, index) in cardMusics"
                    :key="index"
                    :src = "cardMusics.poster"
                    :alt = "cardMusics.title"
                    :author = "cardMusic.author"
                    :genre = "cardMusic.genre"
                    :year = "cardMusic.year" 
              /> 
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
    mounted() {
            axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.cardMusics = response.data.response;
                console.log(this.cardMusics.poster);
            })
            .catch(function (error) {
                console.log(error);
            });
    },
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
</style>