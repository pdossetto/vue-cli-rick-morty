<template>
  <form class="d-flex my-5">
    <div class="flex-grow-1">
        <input 
            type="text"
            class="form-control"
            placeholder="Search character"
            v-model='inputText'>
    </div>
    <div class="mx-3">
        <button
            type="submit"
            class="btn btn-primary"
            @click.prevent="$emit('performSearch', inputText)"
        >
            Search
        </button>
    </div>
    <div class="">
        <button
            class="btn btn-warning"
            @click.prevent="resetSearch"
        >
            Reset
        </button>
    </div>

  </form>
</template>

<script>
export default {
    name: 'Search',
    data() {
        return {
            inputText: '',
        }
    },
    methods: {
        resetSearch() {
            this.inputText = '';

            this.$emit('performSearch', this.inputText);
        }
    }
}
</script>

<style>

</style>