<template>
  <div class="grid-container">
    <div class="articles-container">
      <h1 class="articles-head">Thinking loudly</h1>
      <ul>
        <li
          v-for="article of articles"
          :key="article.slug"
          class="article-container"
        >
          <NuxtLink :to="`/words/${article.slug}`" class="content-container">
            <div class="text">
              <div class="title-container">
                <h2 class="title">{{ article.title }}</h2>
                <p class="date">{{ formatDate(article.published) }}</p>
              </div>
              <p>{{ article.description }}</p>
            </div>
            <div class="arrow">
              <icon-base size="32" viewbox="32"><arrow-right /></icon-base>
            </div>
          </NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content('articles', params.slug)
      .only(['title', 'description', 'img', 'slug', 'published'])
      .sortBy('published', 'desc')
      .fetch()

    return {
      articles,
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'short', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
  },
}
</script>

<style scoped lang="scss">
@use '@/assets/_base/mixins';

div.grid-container {
  padding: 0 0.5rem;

  @include mixins.respond(md) {
    padding: 0 4.25rem;
  }

  div.articles-container {
    width: 100%;
    margin: auto;
    padding: 6rem 0.5rem;

    @include mixins.respond(md) {
      padding: 1.75rem 0.75rem;
    }

    h1.articles-head {
      font-family: var(--sans-wide);
      font-size: var(--text-sm);
      text-transform: uppercase;
      letter-spacing: 2px;
      margin-bottom: 2rem;

      @include mixins.respond(lg) {
        margin-bottom: 5.25rem;
      }
    }

    li.article-container {
      width: 100%;
      border-bottom: 1px solid var(--white);
      transition: background 0.375s cubic-bezier(0.22, 1, 0.36, 1);

      &:first-of-type {
        border-top: 1px solid var(--white);
      }

      .content-container {
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        padding: 1.5rem 0;

        @include mixins.respond(lg) {
          flex-direction: row;
        }

        .text {
          position: relative;
          flex: 1;
          transition: transform 0.375s cubic-bezier(0.22, 1, 0.36, 1);
          margin-bottom: var(--type-baseline);

          .title-container {
            display: flex;
            flex-direction: column;

            width: 100%;
            margin-bottom: 0.5rem;

            @include mixins.respond(lg) {
              flex-direction: row;
              align-items: flex-end;
            }

            h2.title {
              font-family: var(--sans-wide);
              font-size: var(--text-xl);
              text-transform: uppercase;
              letter-spacing: 2px;
              margin-right: 1rem;
              margin-bottom: 0.5rem;
              transition: color 0.25s;

              @include mixins.respond(lg) {
                margin-bottom: 0;
              }
            }

            p.date {
              font-size: var(--text-sm);
              opacity: 0.5;

              @include mixins.respond(lg) {
                margin-bottom: 0.4rem;
              }
            }
          }
        }

        .arrow {
          display: flex;
          justify-content: flex-start;
          align-items: center;
          width: 2.5rem;
          transition: transform 0.375s cubic-bezier(0.22, 1, 0.36, 1),
            color 0.375s cubic-bezier(0.22, 1, 0.36, 1);

          @include mixins.respond(lg) {
            justify-content: flex-end;
          }
        }
      }

      &:hover {
        background: rgba(94, 50, 255, 0.2);

        img.img-bg {
          opacity: 0.5;
        }

        .text {
          transform: translateX(1.5rem);

          h2.title {
            color: var(--blue);
          }
        }

        .arrow {
          transform: translateX(1.5rem);
          color: var(--blue);
        }
      }

      @include mixins.respond(lg) {
        &:hover {
          background: rgba(94, 50, 255, 0.2);

          img.img-bg {
            opacity: 0.5;
          }

          .text {
            transform: translateX(1.5rem);

            h2.title {
              color: var(--blue);
            }
          }

          .arrow {
            transform: translateX(-1.5rem);
          }
        }
      }
    }
  }
}
</style>
