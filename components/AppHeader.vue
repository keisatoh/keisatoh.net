<template>
  <header class="header">
    <div class="headerContainer">
      <component :is="isTopPage ? 'h1' : 'p'" class="siteName">
        <nuxt-link to="/">Keiichiro Sato</nuxt-link>
      </component>

      <!-- メニュー -->
      <nav>
        <ul class="menu">
          <li>
            <nuxt-link to="/about" class="menu__link">about</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/works" class="menu__link">works</nuxt-link>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  computed: {
    // TOPページかどうか
    isTopPage() {
      if (this.$route.name === 'index') return true
      return false
    },
  },
}
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  background-color: $base-color-primary;
}

.headerContainer {
  margin: 0 auto;
  max-width: 780px;
  padding: 1rem 2rem 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.siteName {
  color: $text-color-primary;
  font-family: $font-base;
  font-size: rem(20);
  font-weight: 500;
  letter-spacing: 0;
}

.menu {
  list-style: none;
  display: flex;
  margin-right: -0.75em;

  &__link {
    font-family: $font-base;
    font-weight: 500;
    text-transform: capitalize;
    line-height: 64px;
    display: inline-block;
    padding: 0 0.25em;
    position: relative;

    @include mq() {
      padding: 0 0.75em;
    }

    &::after {
      content: '';
      display: block;
      width: 0;
      height: 2px;
      background-color: $key-color-black;
      transition: all 0.3s ease-in-out;
      position: absolute;
      left: 0;
      bottom: 0;
    }

    &:hover {
      &::after {
        width: 100%;
      }
    }
  }
}
</style>