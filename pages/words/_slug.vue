<template>
  <article class="post">
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <p>Article last updated: {{ formatDate(article.updatedAt) }}</p>
    <nuxt-content :document="article" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    return { article }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
  },
}
</script>

<style scoped lang="scss">
article.post {
  max-width: 640px;
  margin: auto;
}
</style>
