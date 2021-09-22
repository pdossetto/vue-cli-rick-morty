<template>
  <div id="app" class="text-center">
    <Header msg="Rick and Morty App" />
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style lang="scss">
  @import "./styles/general.scss";
</style>
