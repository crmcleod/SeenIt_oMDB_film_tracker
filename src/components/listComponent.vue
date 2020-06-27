<template lang="html">
   <li v-on:click="handleClick">{{film.Title}}
       {{film.Type}}<br>
       {{film.Year}}
   </li>
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

<style lang="css" scoped>
li{
    justify-content: center;
    display:flex;
    vertical-align: middle;
    width: 5rem;
    height: auto;
    background-color: rgba(69, 123, 157, 1) ;
    margin: 1%;
    padding: 10%;
    /* margin: %; */
    color: blue;
    cursor: pointer;
    list-style: none;
    border-radius: 5%;
}
li:hover{
    background-color: rgb(108, 155, 185);
/* font-size: 200% ; */
}
</style>