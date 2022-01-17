<template>
  <header>
      <div class="container-fluid p-2">
          <img src="../assets/img/Spotify_logo_without_text.svg.png" alt="logo-spotify">
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data () {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
@import "../assets/scss/partials/_header.scss";
.container-fluid {
    @include container (50px, 100%);
}
</style>