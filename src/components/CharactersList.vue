<template>
  <section class="container">
    <div v-if="!loading" class="row">
      <div class="col-12">
        <Search @performSearch="searchCharacter"/>
      </div>
      <!-- Stampo la lista dei personaggi ottenuta tramite Axios API -->
      <div v-for="(character, index) in filteredCharactersList" :key="index"  class="col-6 col-md-4 col-lg-3 mb-5">
        <Character :key="index"  :info="character" />
      </div>
    </div>

    <Loader v-else />
  </section>
</template>

<script>
import axios from 'axios';
import Character from './Character.vue';
import Loader from './Loader.vue';
import Search from './Search.vue';

export default {
  name: 'CharactersList',
  components: {
    Character,
    Loader,
    Search
  },
  data() {
    return {
      APIUrl: 'https://api.sampleapis.com/rickandmorty/characters',
      charactersList: [],
      loading: true,
      searchText: ''
    }
  },
  created() {
    this.getCharacters();
  },
  computed: {
    filteredCharactersList() {
      if (this.searchText === "") {
        return this.charactersList;
      }

      let filteredList = this.charactersList.filter( item => {
        return item.name
                  .toLowerCase()
                  .includes(this.searchText.toLowerCase());
      })

      return filteredList;
    }
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
    },
    searchCharacter(text) {
      this.searchText = text;
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
