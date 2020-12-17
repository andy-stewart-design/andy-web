<template>
  <div class="articles-container">
    <ul>
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink :to="`words/${article.slug}`">
          <!-- <img :src="article.img" /> -->
          <div>
            <h2>{{ article.title }}</h2>
            <p>{{ article.description }}</p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content('articles', params.slug)
      .only(['title', 'description', 'img', 'slug', 'author'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      articles,
    }
  },
}
</script>

<style scoped lang="scss">
div.articles-container {
  max-width: 640px;
  margin: auto;
}
</style>
