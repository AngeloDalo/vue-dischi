<template>
  <main>
      main
     <MainAlbum /> 
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
            cardMusic: null,
        }
    },
    mounted() {
            axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.cardMusic = response.data.response;
                console.log(this.cardMusic);
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