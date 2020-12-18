<template>
  <article class="post">
    <h1 class="post-title">{{ article.title }}</h1>
    <p class="post-descr">
      {{ article.description }}
      <span class="post-updated">
        Last updated: {{ formatDate(article.updatedAt) }}</span
      >
    </p>
    <!-- <p>Article last updated: {{ formatDate(article.updatedAt) }}</p> -->
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

<style lang="scss">
article.post {
  max-width: 640px;
  margin: auto;
  padding-top: 6rem;

  h1.post-title {
    font-family: var(--sans-wide);
    text-transform: uppercase;
    letter-spacing: 2px;
    font-size: var(--text-lg);
    margin-bottom: 1rem;
  }

  p.post-descr {
    margin-bottom: 1rem;

    .post-updated {
      opacity: 0.5;
    }
  }

  .nuxt-content {
    h2,
    h3,
    h4,
    h5,
    h6,
    p {
      margin-bottom: 1rem;
    }

    h2 {
      font-weight: var(--sans-bold);
      font-weight: 700;
      font-size: var(--text-lg);
    }

    h3 {
      font-weight: bold;
      font-size: 22px;
    }

    p {
      margin-bottom: 20px;
    }
  }
}
</style>
