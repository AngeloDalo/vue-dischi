<template>
  <main class="container-fluid">
      <div class="container">
          <div class="row">
                <div class="col-12">
                    <!-- event + inputText di Search.vue-->
                    <Search
                        @changeGenre="searchAlbum($event)"
                    />
                </div>
          </div>
          <div class="row p-5" v-if="cardMusics">
              <!-- elemento che potrà essere riutilizzato -->
              <MainAlbum
                    v-for="(cardMusic, index) in filteredGenre"
                    :key="index"
                    :src = "cardMusic.poster"
                    :alt = "cardMusic.title"
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
import Search from "./Search.vue"
export default {
    name: 'Main',
    //metto elemento figlio
    components: {
        MainAlbum,
        Search,
    },
    data () {
        return {
            //conterrà tutti gli elementi dell'api
            genreSearch: 0,
            cardMusics: null,
        }
    },
    computed: {
        filteredGenre() {
            if (this.genreSearch == 0 || this.genreSearch == 'All') {
                return this.cardMusics;
            } else {
                return  this.cardMusics.filter((element) => element.genre.includes(this.genreSearch));
            }
        }
    },
    created() {
        console.log(this.genreSearch);
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
    methods: {
        searchAlbum(event) {
            //genreSearch prende valore di event che corrisponde ad inputText di Search.vue
            this.genreSearch = event;
        }
    }
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