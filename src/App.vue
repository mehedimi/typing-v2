<template>
  <div id="app">
    <Article/>
  </div>
</template>

<script>
import Article from './components/Article.vue'

export default {
  name: 'app',
  components: {
    Article
  },
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Exo+2');
  *{
    font-family: 'Exo 2', sans-serif;
  }
  .container{
    max-width: 1000px;
    margin: auto;
  }
</style>
