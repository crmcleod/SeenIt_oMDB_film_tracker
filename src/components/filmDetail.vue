<template lang="html">
  <div v-if="film" id="filmDetail">
      <div id="img-wrap">
      <img :src="film.Poster">
      </div>
      <div id="text-wrap">
      <!-- <h2>{{film.Title}}</h2>
      <h3>{{film.Year}}</h3>
      <h3>{{film.Plot}}</h3>
    <!-- <input type="checkbox" v-on:change.prevent="addToSeen" value="Click to add to seen">Seen it!</button> -->
    </div>
      
    </div>
</template>

<script>
import { eventBus } from '../main'

export default {
    name: 'film-detail',
    props: ['film'],
}

</script>

<style>
#filmDetail {
    padding: 3vw;
    background-color: rgba(255, 255, 240, 0);
    /* font-size: small; */
    display: grid;
    grid-template-columns: repeat(2, auto-fill);
    grid-template-rows: 1;
    justify-content: center;
    align-items: center;
    grid-gap: 1vw;
    position: absolute;
    word-break: break-all;
    left: 50%;
    top: 30%;
    width: fit-content;
}
input[type=checkbox]{
    transform: scale(1.5);
    margin: 1vw;
    vertical-align: text-top;
}
img{
    /* justify-content: center; */
    grid-column: 1/2;
    width: 50%;
    padding: 0mm;
    align-self: center;
    margin-left:10rem;
    /* margin-right: 0mm; */
}
#text-wrap{
    grid-column: 2/2;
}
</style>