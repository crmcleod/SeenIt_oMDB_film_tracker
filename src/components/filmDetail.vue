<template lang="html">
  <div class="card" v-if="film" id="filmDetail" style="width:30%">
      <!-- <div id="img-wrap"> -->
      <img :src="film.Poster">
        <div class="container">
            <p>{{film.Plot}}</p>
        </div>
      <!-- </div> -->
        <!-- <div id="text-wrap"> -->
      <!-- <h2>{{film.Title}}</h2>
      <h3>{{film.Year}}</h3>
      <h3>{{film.Plot}}</h3>
            <!-- <input type="checkbox" v-on:change.prevent="addToSeen" value="Click to add to seen">Seen it!</button> -->
            <!-- </div> -->
      </div>
</template>

<script>
import { eventBus } from '../main'

export default {
    name: 'film-detail',
    props: ['film'],
}

</script>

<style scoped>
img {width: 60%;}
.card{
    padding: 3vw;
    background-color: rgba(255, 255, 240, 0);

    /* display: grid; */
    grid-template-columns: repeat(2, auto-fill);
    grid-template-rows: 1;
    justify-content: center;
    align-items: center;
    grid-gap: 1vw;
    position: absolute;
    word-break: keep-all;
    left: 60%;
    top: 20%;
    width: 50%;
}
/* p{
    word-break: break-all;} */
/* input[type=checkbox]{
    transform: scale(1.5);
    margin: 1vw;
    vertical-align: text-top;
} */
/* img{
    /* justify-content: center; */
    /* grid-column: 1/2;
    width: 30%;
    padding: 0mm;
    align-self: center;
    margin-left:10rem; */
    /* margin-right: 0mm; */
/* } */
/* #text-wrap{
    grid-column: 2/2;
} */
</style>