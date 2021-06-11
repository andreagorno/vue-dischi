<template>
  <div id="app">
    <Header :genres="allGenres" @changedGenre="updateSelectedGenre"/>

    <ArtistList @genresReady="setGenres" :selectedGenre="currentGenre"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ArtistList from "./components/ArtistList.vue";

export default {
  name: 'App',
  data: function () {
    return {
      allGenres: [],
      currentGenre: ""
    }
  },
  methods: {
    setGenres: function (array) {
      this.allGenres = array;
    },
    updateSelectedGenre: function (newGenre) {
      this.currentGenre = newGenre;
    }
  },
  components: {
    Header,
    ArtistList
  }
}
</script>

<style lang="scss">
  @import "./style/general";
</style>
