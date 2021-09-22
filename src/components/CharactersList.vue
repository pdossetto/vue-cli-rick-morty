<template>
  <section class="container">
    <div class="row">
      <!-- TODO: Stampo la lista dei personaggi ottenuta tramite Axios API -->
    </div>
  </section>
</template>

<script>
import axios from 'axios';
export default {
  name: 'CharactersList',
  data() {
    return {
      APIUrl: 'https://api.sampleapis.com/rickandmorty/characters',
      charactersList: []
    }
  },
  created() {
    this.getCharacters();
  },
  methods: {
    getCharacters() {
      axios
          .get(this.APIUrl)
          .then( res => {
            // console.log(res.data);
            this.charactersList = res.data;
            
          })
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  h1 {
    font-weight: 700;
  }
</style>
