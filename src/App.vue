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
  @import url('https://fonts.googleapis.com/css?family=Ubuntu');
  *{
    font-family: 'Ubuntu', sans-serif;
  }
  .container{
    max-width: 1000px;
    margin: auto;
  }
</style>
