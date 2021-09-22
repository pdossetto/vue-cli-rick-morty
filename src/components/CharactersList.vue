<template>
  <section class="container">
    <div v-if="!loading" class="row">
      <!-- Stampo la lista dei personaggi ottenuta tramite Axios API -->
      <div v-for="(character, index) in charactersList" :key="index" class="col-6 col-md-4 col-lg-3 mb-5">
        <Character :info="character" />
      </div>
    </div>

    <Loader v-else />
  </section>
</template>

<script>
import axios from 'axios';
import Character from './Character.vue';
import Loader from './Loader.vue';

export default {
  name: 'CharactersList',
  components: {
    Character,
    Loader
  },
  data() {
    return {
      APIUrl: 'https://api.sampleapis.com/rickandmorty/characters',
      charactersList: [],
      loading: true
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
            //setTimeout( () => {this.loading = false; }, 5000);
            this.loading = false;
          })
          .catch( err => {
            console.log("Error ", err);
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
