<template>
<!-- elemento figlio di Main -->
  <div class="col-2">
    <!-- elementi celesti collegati al propr prenderanno le informazioni dal Main.vue -->
    <img class="title-image"
    :src="src"
    :alt="alt">
    <h1> {{ title }} </h1>
    <p> {{ author }} </p>
    <p> {{ year }} </p>
  </div>
</template>

<script>
export default {
    name: "MainAlbum",
    props: ['src', 'alt', 'title', 'author', 'year'],
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
@import "../assets/scss/partials/_mainAlbum.scss";
.col-2 {
    @include col-2 (2em, 2em, 2em, 100%, 1em,white, uppercase, 1em, bold, center, 2em, center, 0em, grey);
}
</style>