<template>
  <article class="post">
    <div class="hero">
      <h1 class="post-title">{{ article.title }}</h1>
      <p class="post-descr">
        {{ article.description }}
      </p>
      <div class="post-meta">
        <p class="post-tag">{{ article.tag }}</p>
        <span class="post-updated"> {{ formatDate(article.createdAt) }}</span>
      </div>
      <img
        v-if="article.img"
        class="hero-img"
        :src="require(`~/assets/img/blog/${article.img}`)"
        :alt="article.alt"
      />
    </div>

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
  div.hero {
    position: relative;
    max-width: 680px;
    margin: 0 auto;
    padding-top: calc(var(--type-baseline) * 7.5);
    // width: 100vw;
    // height: 90vh;

    h1.post-title {
      position: relative;
      font-family: var(--sans-wide);
      text-transform: uppercase;
      letter-spacing: 2px;
      font-size: var(--text-2xl);
      line-height: calc(var(--type-baseline) * 4);
      margin-bottom: calc(var(--type-baseline) * 1);
    }

    p.post-descr {
      line-height: calc(var(--type-baseline) * 2);
      margin-bottom: 1.325rem;
    }

    div.post-meta {
      position: relative;
      align-items: center;
      display: flex;
      margin-bottom: calc(var(--type-baseline) * 2.75);

      p.post-tag {
        border-radius: 10rem;
        margin-right: 1rem;
        font-family: var(--sans-bold);
        font-size: var(--text-sm);
        letter-spacing: 0.25px;
        margin-top: 0.075rem;
        padding: 0.25rem 0.875rem;
        background-color: var(--blue);
      }

      .post-updated {
        opacity: 0.6;
      }
    }

    .hero-img {
      margin-bottom: calc(var(--type-baseline) * 4);
    }
  }

  .nuxt-content {
    max-width: 680px;
    margin: auto;

    h1,
    h2,
    h3,
    h4,
    h5,
    h6 {
      font-family: var(--sans-bold);
      font-weight: 700;
    }

    h1 {
      font-size: var(--text-5xl);
      line-height: calc(var(--type-baseline) * 6);
      margin-top: calc(var(--type-baseline) * -0.5);
      margin-bottom: calc(var(--type-baseline) * 2.5);
    }

    h2 {
      font-size: var(--text-4xl);
      line-height: calc(var(--type-baseline) * 6);
      margin-top: calc(var(--type-baseline) * 2);
      margin-bottom: calc(var(--type-baseline) * 2);
    }

    h3 {
      font-size: var(--text-3xl);
      line-height: calc(var(--type-baseline) * 5);
      margin-top: calc(var(--type-baseline) * 1);
      margin-bottom: calc(var(--type-baseline) * 2);
    }

    h4 {
      font-size: var(--text-2xl);
      line-height: calc(var(--type-baseline) * 4);
      margin-top: calc(var(--type-baseline) * 2);
      margin-bottom: calc(var(--type-baseline) * 2);
    }

    h5 {
      font-size: var(--text-xl);
      line-height: calc(var(--type-baseline) * 3);
      margin-top: calc(var(--type-baseline) * 2);
      margin-bottom: calc(var(--type-baseline) * 2);
    }

    h6 {
      font-size: var(--text-lg);
      line-height: calc(var(--type-baseline) * 3);
      margin-bottom: calc(var(--type-baseline) * 2);
    }

    p {
      line-height: calc(var(--type-baseline) * 2);
      margin-bottom: calc(var(--type-baseline) * 2);
    }

    img {
      margin: calc(var(--type-baseline) * 4) 0;
    }
  }
}
</style>
