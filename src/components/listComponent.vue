<template lang="html">
   <h2 v-on:click="handleClick">{{film.Title}}</h2>
    <!-- <img :src="article.webUrl.img"> -->
</template>

<script>
import { eventBus } from '../main'
export default {
    name: 'list-component',
    props: ['film'],
    methods: {
        handleClick(){
            eventBus.$emit('film-selected', this.film)
        }
    }

}
</script>

<style>
li {
    list-style: none;
}
</style>