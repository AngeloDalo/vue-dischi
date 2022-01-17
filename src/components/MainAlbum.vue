<template>
  <div class="col-2">
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
.col-2 {
    background-color: $boxAlbumColor;
    margin-right: 2em;
    margin-bottom: 2em;
    padding-bottom: 2em;
    img {
        width: 100%;
        margin-bottom: 1em;
    }
    h1 {
        color: white;
        text-transform: uppercase;
        font-size: 1em;
        font-weight: bold;
        text-align: center;
        margin-bottom: 2em;
    }
    p {
        text-align: center;
        margin-bottom: 0em;
        color: grey;
    }
}
</style>