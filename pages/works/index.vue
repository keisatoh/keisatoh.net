<template>
  <div class="container container--lg">
    <h1 class="childPageTitle">Works</h1>
    <ol class="works">
      <li v-for="work in works.contents" :key="work.id" class="works__item">
        <div class="works_name">
          <nuxt-link :to="`/works/${work.id}/`">
            <h2>{{ work.title }}</h2>
          </nuxt-link>
          <p>{{ work.description }}</p>
        </div>
        <figure class="works__image">
          <nuxt-link :to="`/works/${work.id}/`">
            <img :src="work.thumbnail.url" :alt="work.title" />
          </nuxt-link>
        </figure>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  async asyncData({ $microcms }) {
    const works = await $microcms.get({
      endpoint: 'works',
    })
    return {
      works,
    }
  },
}
</script>

<style lang="scss" scoped>
li + li {
  border-top: 1px solid #BBBBBB;
  padding: 1em 0;
  @include mq() {
    padding: 2em 0;
  }
}
.works {
  list-style: none;

  .works__item {
    display: grid;
    grid-template-columns: 1fr;
    margin: 2em auto 0 auto;
    gap: 20px;

    @include mq(sm) {
      grid-template-columns: 1fr 1fr;
    }
  }
  .works_name {
    // background-color: red;
    h2 {
      font-size: rem(16);
      font-weight: 600;
    }
    p {
      font-size: rem(14);
      margin-top: 1em;
      color: $text-color-secondary;
    }
  }

  .works__image {
    // background-color: blue;
    img {
      height: 0;
      width: 100%;
      min-height: 200px;
      object-fit: cover;
      max-height: 400px;
    }
  }
}
</style>
