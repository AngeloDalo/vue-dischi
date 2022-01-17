<template>
  <div class="col-2">
    <img class="title-image"
    :src="src"
    :alt="alt">
    <h3> {{ author }} </h3>
    <p> {{ genre }} </p>
    <p> {{ year }} </p>
  </div>
</template>

<script>
export default {
    name: "MainAlbum",
    props: ['src', 'alt', 'author', 'genre', 'year'],
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>

</style>