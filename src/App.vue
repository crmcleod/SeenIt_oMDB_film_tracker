<template lang="html">
  <div id="app">
   <h1>Articles</h1>
   <articles-list></articles-list>
   <list-component></list-component>
  </div>
</template>

<script>

import ArticlesList from './components/articles-list'
import ListComponent from './components/listComponent'

export default {
    name: 'App',
  data(){
    return {
    results: []
  }
  },
  components: {
    "articles-list": ArticlesList,
    "list-component": ListComponent
  },

  mounted(){
    const searchTerm = "Edinburgh"
  fetch(`https://content.guardianapis.com/search?q=${searchTerm}s&format=json&api-key=test`)
  .then(response => response.json())
  .then(results => this.results = results)
}}

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
