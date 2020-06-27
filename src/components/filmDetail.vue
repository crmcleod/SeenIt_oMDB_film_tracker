<template lang="html">
  <div v-if="film" id="filmDetail">
      <img :src="film.Poster">
      <h2>{{film.Title}}</h2>
      <h3>{{film.Year}}</h3>
      <h3>{{film.Plot}}</h3>
    <input type="checkbox" v-on:change.prevent="addToSeen" value="Click to add to seen">click me</button>
      
    </div>
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film'],
}

</script>

<style>
#filmDetail {
    font-size: small;
    display: ;
    width: 30%;
    position: absolute;
    word-break: break-all;
    left: 70%;
    /* position:; */
    top: 30%;
    width: fit-content;
}
img{
    width: 50%;
}
</style>