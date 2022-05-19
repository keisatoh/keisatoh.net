<template>
  <div class="container container--lg">
    <div class="works">
      <h1 class="childPageTitle">{{ work.title }}</h1>
      <dl v-if="work.release" class="works__date">
        <dd>
          <time
            :datetime="work.release"
            v-text="$dateFns.format(new Date(work.release), 'yyyy.MM.dd')"
          />
        </dd>
      </dl>
      <figure class="works__thumbnail">
        <img
          :width="work.thumbnail.width"
          :height="work.thumbnail.height"
          :src="work.thumbnail.url"
          :alt="work.title"
        />
      </figure>
      <div class="worksItem">
        <h2 class="worksItem__title">Abstract</h2>
        <p class="worksItem__contents">{{ work.abstract }}</p>
      </div>
      <div class="worksItem">
        <h2 class="worksItem__title">Links</h2>
        <p class="worksItem__contents">
          <a :href="work.links" target="_blank">{{ work.links }}</a>
        </p>
      </div>
      <div class="worksItem">
        <h2 class="worksItem__title">Stack</h2>
        <p class="worksItem__contents">
          <span
            v-for="(skill, skillIndex) in work.stack"
            :key="skillIndex"
            v-text="skill"
          />
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $microcms, params }) {
    const work = await $microcms.get({
      endpoint: `works/${params.id}`,
    })
    return {
      work,
    }
  },
}
</script>

<style lang="scss" scoped>
a {
  text-decoration: underline;
}
.works {
  padding: 3em 0;

  .works__thumbnail {
    width: 100%;
    margin-top: 2rem;

    @include mq() {
      margin-top: 5rem;
    }
    img {
      width: 100%;
    }
  }

  .works__date {
    margin-top: 0.125em;
    text-align: center;
  }
}

.worksItem {
  .worksItem__title {
    font-size: rem(20);
    margin-top: 2em;
  }

  .worksItem__contents {
    white-space: pre-wrap;
    margin-top: 1em;

    span + span {
      &::before {
        content: '/';
        display: inline-block;
        margin: 0 0.5em;
      }
    }
  }
}
</style>
