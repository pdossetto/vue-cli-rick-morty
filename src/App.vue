<template>
  <div id="app" class="text-center">
    <Header msg="Rick and Morty App" />

    <CharactersList />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import CharactersList from './components/CharactersList.vue';

export default {
  name: 'App',
  components: {
    Header,
    CharactersList
  }
}
</script>

<style lang="scss">
  @import "./styles/general.scss";
</style>
