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

.seenCard figcaption { 
    white-space: normal;
    font-size: 1.3rem;
padding: 0.5rem;
height: 100px;

}
.seenCard li{
    position: relative;
    border: 0px;
    align-content: center;
    height: 270px;
    background-color: rgba(248, 248, 255, 0.568);
    width: 200px;
    word-break: keep-all;
    margin: 0.5rem;
    border: 1px;
    border-color: seagreen;
    margin-top: 50%;
}
img{
    height: 9rem;
    width: 6rem;
    margin: 0.5em;

}
</style>
