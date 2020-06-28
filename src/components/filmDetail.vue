<template lang="html">
  <div class="card" v-if="film" id="filmDetail" style="width:30%">
      <img :src="film.Poster">
        <div class="container">
            <p>{{film.Plot}}</p>
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

<style scoped>
img {width: 60%;}
.card{
    font-size: smaller;
    padding: 3vw;
    grid-template-columns: repeat(2, auto-fill);
    grid-template-rows: 1;
    justify-content: center;
    align-items: center;
    grid-gap: 1vw;
    position: absolute;
    word-break: keep-all;
    left: 60%;
    top: 15%;
    width: 50%;
}
</style>