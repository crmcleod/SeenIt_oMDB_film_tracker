<template lang="html">
   <li v-on:mouseover="handleMouseOver" >
       <h3>{{film.Title}}</h3>
       <h4>Media type: {{film.Type}}</h4>
       <h4>Year of release: {{film.Year}}</h4>
       <label for="seenItBox">Watched it/Played it!
       <p><input id="seenItBox" type="checkbox" v-on:change.self="handleChange" value="Click to add to seen"></button></p>
       </label>
       
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
    opacity: 50%;
    
}
h3{
    line-height: 10mm;
}
li{
    line-height: 3mm;
    font-size: smaller;

    justify-content: center;
    display:flexbox;
    vertical-align: middle;
    width:  15rem;
    background-color: rgba(99, 38, 74, 0.384) ;
    margin: 0.8%;
    padding: 4%;
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