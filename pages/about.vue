<template>
  <div class="container container--lg">
    <h1 class="childPageTitle">About Me</h1>
    <section id="links" class="sectionPrimary">
      <h2>Profile</h2>
      <p>
        佐藤桂一郎、1999年生まれ。ものづくりが好きです。Webのフロントエンドを書きます。
      </p>
    </section>
    <section id="links" class="sectionPrimary">
      <h2>Skills</h2>
      <skillList></skillList>
    </section>
    <section id="contact" class="sectionPrimary">
      <h2>Contact</h2>
      <p>keisatoh999@gmail.com</p>
    </section>
  </div>
</template>

<script></script>

<style lang="scss" scoped>
.sectionPrimary {
  h2 {
    font-family: $font-base;
    font-size: rem(22);
  }
  p {
    margin-top: 1rem;
  }
}
</style>