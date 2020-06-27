<template lang="html">
  <div v-if="film" id="filmDetail">
      <h1>selected film</h1>
      <h2>{{film.Title}}</h2>
      <h3>{{film.Year}}</h3>
    </div>
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']
}
</script>

<style>

</style>