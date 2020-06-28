<template>
<div class="seenCard">
  <li>
      <img :src="film.Poster">
      <div id="text-container">
      <figcaption>{{film.Title}}</figcaption>
      </div>
      </li>
      </div>
</template>

<script>
import { eventBus } from '../main'
export default {
    name: 'seen-list-item',
    props: ['film']
}
</script>

<style scoped>



/* li { background-color: coral;} */
.seenCard figcaption { 
    white-space: normal;
    font-size: 1.3rem;
padding: 0.5rem;
height: 100px;

}
.seenCard li{
    border: 0px;
    align-content: center;
    height: 270px;
    background-color: rgba(248, 248, 255, 0.342);
    width: 200px;
word-break: keep-all;
margin: 0.5rem;}

img{
    height: 9rem;
    width: 6rem;
    margin: 0.5em;
    /* display: flexbox;
    flex-direction: row;
    list-style-type: none; */
}
</style>
