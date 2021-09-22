<template>
  <header>
    <h1>{{ msg }}</h1>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  h1 {
    font-weight: 700;
  }
</style>
