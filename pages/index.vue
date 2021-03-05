<template>
  <div>
    <article-content />
  </div>
</template>

<script>
import ArticleContent from '~/components/Article/article-content';

export default {
  components: {
    ArticleContent
  },
  transition: {
    name: 'page',
    mode: ''
  }
}
</script>

<style>

</style>
