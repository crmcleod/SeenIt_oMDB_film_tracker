<template lang="html">
  <div v-if="film" id="filmDetail">
      <img :src="film.Poster">
      <h2>{{film.Title}}</h2>
      <h3>{{film.Year}}</h3>
      <h3>{{film.Plot}}</h3>
      
    </div>
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']
}
</script>

<style>
#filmDetail {
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