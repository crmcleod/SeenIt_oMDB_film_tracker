<template lang="html">
   <li>{{film.Title}}</li>
    <!-- <img :src="article.webUrl.img"> -->
</template>

<script>
import { eventBus } from '../main'
export default {
    name: 'list-component',
    props: ['film']

}
</script>

<style>
li {
    list-style: none;
}
</style>