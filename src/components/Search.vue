<template>
    <div class="search">
        <select name="genre" @change="$emit('changeGenre', inputText)" class="form-control" v-model="inputText">
            <option value="All">All</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>
    </div>  
</template>

<script>
export default {
    name: "Search",
    props: [],
    data() {
        return {
            inputText: '',
        }
    },
    created() {
        console.log(this.inputText);
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
.form-control {
    margin-left: 35%;
    margin-top: 2em;
    width: 20%;
}
</style>