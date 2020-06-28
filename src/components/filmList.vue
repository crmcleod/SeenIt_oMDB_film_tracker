<template>
    <div id="filmList">
    <ul>
        <list-component v-for="(film, index) in films" :film="film" :key="index"></list-component>
    </ul>
    </div>
</template>

<script>
import ListComponent from './listComponent'
import { eventBus } from '../main'

export default {
    name: "film-list",
    props: ['films'],
    components: {
        "list-component": ListComponent
    }
    // props: ['']
        // }
    // }

}
</script>

<style>
#filmList ul{
    height: 600px;
    overflow-y: scroll;
    width: 60%;
    margin: 0%;
    padding: 0%;
    justify-content:space-evenly;
    display: flex;
    flex-direction: row;
    flex-wrap:wrap;
    /* background-color: rgba(255, 237, 180, 0.5); */
}
</style>