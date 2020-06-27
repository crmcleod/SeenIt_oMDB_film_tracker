<template>
    <div id="filmList">
    <ul>
        <list-component v-for="(film, index) in films" :film="film" :key="index"></list-component>
    </ul>
    </div>
</template>

<script>
import ListComponent from './listComponent'
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

</style>