<template lang="html">
   <li v-on:mouseover="handleMouseOver" >
       {{film.Title}}<br>

       {{film.Type}}<br>
       {{film.Year}}<br>
        <input type="checkbox" v-on:change.self="handleChange" value="Click to add to seen">Seen it!</button>
       
   </li>
        <!-- <input type="checkbox" v-on:change.prevent="addToSeen" value="Click to add to seen">Seen it!</button> -->

    <!-- <img :src="article.webUrl.img"> -->
</template>

<script>
import { eventBus } from '../main'
export default {
    name: 'list-component',
    props: ['film'],
    methods: {
        handleMouseOver(){
            eventBus.$emit('film-selected', this.film)
        },
        handleChange(){
            eventBus.$emit('film-seen', this.film)
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
    /* height: auto; */
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