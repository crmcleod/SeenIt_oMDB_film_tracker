<template lang="html">
  <div id="app">
   <h1>Films</h1>
   <form v-on:submit.prevent>
   <!-- <label for id="search">Search for film: -->
     <input type="text" v-model="searchTerm" v-on:keyup="fetchFilms">
     <!-- </label> -->
     </form>
   <film-list :films="films"></film-list>
    <film-detail :film="selectedFilm"></film-detail>


  </div>
</template>

<script>
import { eventBus } from './main'
import FilmDetail from './components/filmDetail'
import FilmList from './components/filmList'
import ListComponent from './components/listComponent'

export default {
    name: 'App',
  data(){
    return {
    films: [],
    selectedFilm: null,
    searchTerm: ""
  }
  },
  methods: {
    fetchFilms() {
      let url = "https://www.omdbapi.com/?s="
      let apiKey = "&apikey=62df8c06"
      let searchTerm = this.searchTerm
      fetch(url+searchTerm+apiKey)
      .then(res => res.json())
      .then(films =>this.films = films.Search)
    }
    
  },
  components: {
    "film-list": FilmList,
    "list-component": ListComponent,
    "film-detail": FilmDetail
  },

// film search ?s
  mounted(){
    this.fetchFilms()
  
  // fetch(`http://www.omdbapi.com/?t=${searchTerm}&apikey=62df8c06`)
  // .then(response =>response.json())
  // .then(film=> this.selectedFilm = film)

  eventBus.$on('film-selected', (film) => {
    this.selectedFilm = film

  eventBus.$on('search-term', (search) => {
    this.searchTerm = search
  })
  })}


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
@import url(https://fonts.googleapis.com/css?family=Amatic+SC:regular,700);
background-color: rgba(0, 0, 0, 0);
  font-family: "Amatic SC";
  font-size: xx-large;
  /* -webkit-font-smoothing: antialiased; */
  /* -moz-osx-font-smoothing: grayscale; */
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
li {
  cursor: pointer;
}
</style>
