<template>
    <div class="container">
    <section id="about" class="sectionPrimary">
        <!-- <h2 class="headingPrimary">about</h2> -->
        <div class="profile">
          <figure class="profile__image">
            <img src="~/assets/images/prof.jpg" alt="Keiichiro Sato" />
          </figure>
          <h1 class="profile__name">keisatoh</h1>
          <p class="profile__message">Software Engineer(見習い)</p>
        </div>
    </section>
    <section id="links" class="sectionPrimary">
        <div class="links">
          <h2 class="links__name"><a href="https://twitter.com/passincat">Twitter</a></h2>
          <p class="links__message">@passincat</p>
        </div>
        <div class="links">
          <h2 class="links__name"><a href="https://github.com/keisatoh">GitHub</a></h2>
          <p class="links__message">@keisatoh</p>
        </div>
        <div class="links">
          <h2 class="links__name">Blog(実装中)</h2>
          <p class="links__message">blog.keisatoh.net</p>
        </div>
        <div class="links">
          <h2 class="links__name"><nuxt-link to="/about">About</nuxt-link></h2>
          <p class="links__message">Brief introduction about me</p>
        </div>
        <div class="links">
          <h2 class="links__name"><nuxt-link to="/works">Works</nuxt-link></h2>
          <p class="links__message">My works</p>
        </div>
    </section>
      </div>
</template>

<script>
</script>

<style lang="scss" scoped>
.profile {
  margin-top: 2rem;
  @include mq() {
    margin-top: 4rem;
  }
  .profile__name {
    font-size: rem(24);

    &::before {
      content: '@';
      margin: 0 0.1em;
      color: #959595;
    }
  }

  .profile__image {
    width: 100px;
    margin-bottom: 1em;

    img {
      border-radius: 50%;
    }
  }

  .profile__message {
    color: #959595;
    margin-top: 0.5em;
  }
}

.links {
  margin-top: 2.5rem;
  .links__name {
    font-size: rem(20);
  }

  .links__message {
    color: #959595;
    font-size: rem(14);
  }
}
</style>