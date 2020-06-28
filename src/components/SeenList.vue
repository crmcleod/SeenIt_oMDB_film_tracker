<template>
    <div id="seenFilmList">
        <ul>
            <seen-list-items v-for="(film, index) in films" :film="film" :key="index"></seen-list-items>
        </ul>
    </div>
</template>

<script>
import SeenListItems from './SeenListItems.vue'
import {eventBus} from '../main'
export default {
    name: "seen-list",
    props: ['films'],
    components: {
        "seen-list-items": SeenListItems
    }

}
</script>

<style>
#seenFilmList ul{
    list-style: none;
    display: flex;
    /* overflow-y: hidden; */
    overflow-y: scroll;
    height: 300px;
    width: 1000px;
    /* position: absolute; */
    background-position-x: left;
    background-position-y: top;
    white-space: nowrap;

}
/* ul {margin
    position: absolute;
    background-position-x: left;
    background-position-y: top;
    overflow-x: auto;
    /* display: flex; */
    /* flex-direction: row; */
/* } */
</style>