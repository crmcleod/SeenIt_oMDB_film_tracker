<template lang="html">
  <div id="app">
   <h1>Films</h1>
   <film-list :films="films"></film-list>
   <!-- <list-component></list-component> -->
    </div>

  </div>
</template>

<script>
import { eventBus } from './main'
import FilmList from './components/filmList'
import ListComponent from './components/listComponent'

export default {
    name: 'App',
  data(){
    return {
    films: [],
    selectedFilms: null
  }
  },
  components: {
    "film-list": FilmList,
    "list-component": ListComponent
  },

// film search ?s
  mounted(){
    const searchTerm = "blade"
  fetch(`http://www.omdbapi.com/?s=${searchTerm}&apikey=62df8c06`)
  .then(response => response.json())
  .then(films => this.films = films.Search)}


// film by title ?t
  // mounted(){
  //   const selectedFilm = "Blade"
  // fetch(`http://www.omdbapi.com/?t=${selectedFilm}&apikey=62df8c06`)
  // .then(response =>response.json())
  // .then(film=> this.film)}
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
