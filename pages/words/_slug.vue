<template>
  <div class="grid-container">
    <article class="post">
      <div class="hero">
        <h1 class="post-title">{{ article.title }}</h1>
        <p class="post-descr">
          {{ article.description }}
        </p>
        <div class="post-meta">
          <p class="post-tag">{{ article.tag }}</p>
          <span class="post-updated"> {{ formatDate(article.published) }}</span>
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
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()
    return { article }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'short', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
  },
}
</script>

<style lang="scss">
@use '@/assets/_base/mixins';

@font-face {
  font-family: 'Vesterbro poster';
  src: url('https://assets.website-files.com/5e9d939b6c7f32259d33c1cc/5e9d939b6c7f3233ba33c248_Vesterbro-Poster.woff2')
    format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: auto;
}

div.grid-container {
  padding: 0 0.5rem;

  @include mixins.respond(md) {
    padding: 0 4.25rem;
  }

  article.post {
    padding: 0 0.5rem;
    width: 100%;
    margin: 0 auto;
    padding-top: calc(var(--type-baseline) * 12.5);
    max-width: 42rem;
    hyphens: auto;

    @include mixins.respond(md) {
      width: 100%;
      padding: 0 0.75rem;
      padding-top: calc(var(--type-baseline) * 9.5);
    }

    @include mixins.respond(lg) {
      width: calc(10 / 12 * 100%);
    }

    @include mixins.respond(2xl) {
      width: calc(8 / 12 * 100%);
    }

    div.hero {
      position: relative;
      width: 100%;
      margin-bottom: calc(var(--type-baseline) * 4);

      h1.post-title {
        position: relative;
        font-family: var(--sans-wide);
        text-transform: uppercase;
        letter-spacing: 2px;
        font-size: var(--text-xl);
        line-height: calc(var(--type-baseline) * 4);
        margin-bottom: calc(var(--type-baseline) * 1);
      }

      p.post-descr {
        line-height: calc(var(--type-baseline) * 2);
        margin-bottom: 1.325rem;
      }

      div.post-meta {
        position: relative;
        display: flex;
        align-items: center;
        margin-bottom: calc(var(--type-baseline) * 4);
        font-size: var(--text-sm);

        p.post-tag {
          border-radius: 10rem;
          margin-right: 1rem;
          font-family: var(--sans-bold);
          letter-spacing: 0.25px;
          margin-top: 0.075rem;
          padding: 0.125rem 0.75rem;
          background-color: rgba(94, 50, 255, 0.6);
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
      width: 100%;

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
        margin-top: calc(var(--type-baseline) * 2.25);
        margin-bottom: calc(var(--type-baseline) * 2.75);
      }

      h2 {
        font-family: var(--sans-cond);
        text-transform: uppercase;
        letter-spacing: 0.5px;
        font-size: var(--text-4xl);
        line-height: calc(var(--type-baseline) * 5);
        margin-top: calc(var(--type-baseline) * 2.25);
        margin-bottom: calc(var(--type-baseline) * 2.75);
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
        font-family: var(--sans-bold);
        font-size: var(--text-xl);
        line-height: calc(var(--type-baseline) * 3);
        margin-top: calc(var(--type-baseline) * 2);
        margin-bottom: calc(var(--type-baseline) * 2);
      }

      h6 {
        font-family: var(--sans-bold);
        font-size: var(--text-lg);
        line-height: calc(var(--type-baseline) * 2.5);
        margin-bottom: calc(var(--type-baseline) * 2);
      }

      p {
        line-height: calc(var(--type-baseline) * 2);
        margin-bottom: calc(var(--type-baseline) * 2);
      }

      blockquote {
        position: relative;
        padding-left: 2rem;
        hyphens: none;

        &::after {
          content: '“';
          position: absolute;
          top: 0;
          left: 0;
          font-family: var(--sans-cond);
          text-transform: uppercase;
          letter-spacing: 0.5px;
          font-size: var(--text-4xl);
          line-height: calc(var(--type-baseline) * 5);
          color: var(--blue);
        }
      }

      img {
        margin: calc(var(--type-baseline) * 4) 0;
      }
    }
  }
}
</style>
