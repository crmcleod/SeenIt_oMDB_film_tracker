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
#seenFilmList {
    position: relative;
    left: 100px;
    top: 0px;
}
#seenFilmList ul{
    background-image: url('../../public/seen.png');
    background-size: cover;
    list-style: none;
    display: flex;
    overflow-y: scroll;
    height: 300px;
    width: 600px;
    white-space: nowrap;
}
</style>