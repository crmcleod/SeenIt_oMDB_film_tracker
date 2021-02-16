<template>
    <div id="seenFilmList">
        <ul>
            <seen-list-items id="seenList" v-for="(film, index) in films" :film="film" :key="index"></seen-list-items>
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


#seenList:hover{
    transition: 0.5s;
    transform:translateY(-4rem);

}
#seenFilmList {
    position: relative;
    margin-right: none;
    padding-left: 5vw;
    top: 0px;
}
#seenFilmList ul{
    background-image: url('../../public/seen.png');
    background-size: contain;
    background-repeat: no-repeat;
    background-position: bottom;
    list-style: none;
    display: flex;
    overflow-y: scroll;
    overflow-y: hidden;
    height: 400px;
    width: 45vw;
}
</style>