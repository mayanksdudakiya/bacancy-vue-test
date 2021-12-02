<template>
  <div id="app">
    <GithubSearch @githubusers="searchResults($event)"/>
    <GithubResults :results="results"/>
  </div>
</template>

<script>
import GithubSearch from './components/GithubSearch.vue'
import GithubResults from './components/GithubResults.vue'

export default {
  name: 'App',
  components: {
    GithubSearch,
    GithubResults
  },
  data() {
    return {
        results: ''
    }
  },
  methods: {
    searchResults(response) {
      this.results = response;
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
