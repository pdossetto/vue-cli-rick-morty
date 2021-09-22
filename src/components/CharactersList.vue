<template>
  <section class="container">
    <div class="row">
      <!-- Stampo la lista dei personaggi ottenuta tramite Axios API -->
      <div v-for="(character, index) in charactersList" :key="index" class="col-6 col-md-4 col-lg-3 mb-5">
        <Character :info="character" />
      </div>

    </div>
  </section>
</template>

<script>
import axios from 'axios';
import Character from "./Character.vue";

export default {
  name: 'CharactersList',
  components: {
    Character
  },
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
