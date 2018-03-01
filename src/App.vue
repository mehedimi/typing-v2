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

<style>
  .container{
    max-width: 1000px;
    margin: auto;
  }
</style>
