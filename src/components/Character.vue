<template>
  <div class="character text-center">
    <img class="img-fluid mb-3" :src="info.image" :alt="info.name">
    <h4>{{ info.name }}</h4>
    <div>{{ info.origin }}</div>
    <div>{{ info.species }}</div>
  </div>
</template>

<script>
export default {
  name: 'Character',
  props: ['info']

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  h1 {
    font-weight: 700;
  }

  h4 {
    text-transform: capitalize;
    &::after {
      content: '';
      display: block;
      width: 40px;
      height: 1px;
      margin: 1rem auto;
      background: black;
    }
  }

  img {
    border-radius: 50%;
    box-shadow: 0 0 6px 3px rgba(#000, 0.15);
  }
</style>
