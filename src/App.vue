<template>
  <div id="app">
    <Header/>
    <ArtistList/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ArtistList from "./components/ArtistList.vue";

export default {
  name: 'App',
  components: {
    Header,
    ArtistList
  }
}
</script>

<style lang="scss">
  @import "./style/general";
</style>
