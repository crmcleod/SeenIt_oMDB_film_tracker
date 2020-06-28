<template lang="html">
  <div id="app">
    <header>
      </header>
   <h1>Films</h1>
   <form v-on:submit.prevent>
   <!-- <label for id="search">Search for film: -->
     <input type="text" v-model="searchTerm" v-on:keyup="fetchFilms">
     <!-- </label> -->
     </form>
   <film-list :films="films"></film-list>
    <film-detail :film="selectedFilmAllDetails"></film-detail>
    <seen-list :films="seenFilms"></seen-list>

    <!-- <input type="checkbox" v-on:change.prevent="addToSeen" value="Click to add to seen">click me</button> -->


  </div>
</template>

<script>
import { eventBus } from './main'
import FilmDetail from './components/filmDetail'
import FilmList from './components/filmList'
import ListComponent from './components/listComponent'
import SeenListItems from './components/SeenListItems'
import SeenList from './components/SeenList'

export default {
    name: 'App',
  data(){
    return {
    films: [],
    seenFilms: [],
    selectedFilm: null,
    searchTerm: "",
    selectedFilmAllDetails: null
  }
  },
  methods: {
    fetchFilms() {
      const url = "https://www.omdbapi.com/?"
      // below line must be s= or t=
      let search = "s="
      const apiKey = "&apikey=62df8c06"
      let searchTerm = this.searchTerm
      fetch(url+search+searchTerm+apiKey)
      .then(result => result.json())
      .then(films =>this.films = films.Search)
    },

    addToSeen: function(film) {
      this.seenFilms.push(film)
    },
    fetchFilm() {
      const url = "https://www.omdbapi.com/?"
      let Title = "t="
      const apiKey ="&apikey=62df8c06"
      let filmName = this.selectedFilm
      fetch(url+Title+filmName+apiKey)
      .then(res => res.json())
      .then(film =>this.selectedFilmAllDetails = film)
    },
    
  },
  components: {
    "film-list": FilmList,
    "list-component": ListComponent,
    "film-detail": FilmDetail,
    "seen-list": SeenList,
    "seen-list-items": SeenListItems

  },

  mounted(){
    this.fetchFilms()
    this.fetchFilm()
    // this.addToSeen()


    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film.Title
      this.fetchFilm()}),

    eventBus.$on('search-term', (search) => {
      this.searchTerm = search}),

    eventBus.$on('film-seen', (film) => {
      this.addToSeen(film)
      })
  

  }
}

</script>

<style>
body {
@import url(https://fonts.googleapis.com/css?family=Amatic+SC:regular,700);
background-color: rgba(0, 0, 0, 0.226);
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
