<template lang="html">
   <li v-on:mouseover="handleMouseOver" >
       <h3>{{film.Title}}</h3>
       <h4>Media type: {{film.Type}}</h4>
       <h4>Year of release: {{film.Year}}</h4>
       <label for="seenItBox">Watched it/Played it!</label>
       <br></br>
       <input id="seenItBox" type="checkbox" v-on:change.self="handleChange" value="Click to add to seen"></button>
   </li>
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
input[type=checkbox]{
    transform: scale(3);
    opacity: 0.5;
    position: relative;
    margin-top: 2vw;
    
}
h3{
    line-height: 10mm;
}
li{
    min-height: 300px;
    line-height: 3mm;
    font-size: smaller;
    width:  15rem;
    background-color: rgba(99, 38, 74, 0.384) ;
    margin: 0.8%;
    padding: 2vw;
    color: rgb(255, 255, 255);
    cursor: pointer;
    list-style: none;
    border-radius: 3%;
}
button {display: inline;}
li:hover{
    color: darkblue;
    background-color: rgba(90, 214, 236, 0.267);
}
</style>