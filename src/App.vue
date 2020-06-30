<template lang="html">
  <div id="app">
   <h1>Seen it?</h1>
   <form v-on:submit.prevent>
     <input type="text" v-model="searchTerm" v-on:keyup="fetchFilms" placeholder="search for films here...">
     </form>
   <film-list :films="films"></film-list>
    <film-detail :film="selectedFilmAllDetails"></film-detail>
    <seen-list :films="seenFilmsFiltered"></seen-list>


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
    selectedFilm: {},
    searchTerm: "",
    selectedFilmAllDetails: null
  }
  },
  computed: {
    seenFilmsFiltered: function() {
    return this.seenFilms.filter((v, i, a) => a.indexOf(v)===i)
  }
  },
  methods: {
    fetchFilms() {
      const url = "https://www.omdbapi.com/?"
    // s= returns an array of up to 10 objects
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
      // returns just the best match film
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

h1{
  text-align: left;
  margin: 0px;
  margin-left: 24.5%;
}
input[type=text]{
  position: relative;
  left: -19.5%;
  transform: scale(1.5);
  margin: 10px;
}
body {
@import url(https://fonts.googleapis.com/css?family=Amatic+SC:regular,700);
background-color: rgb(108, 128, 154);
  font-family: "Amatic SC";
  font-size: xx-large;
  text-align: center;
  color: #2c3e50;
}
li {
  cursor: pointer;
}
</style>
