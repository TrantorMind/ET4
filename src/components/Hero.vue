<template>
    <div class="hero">
        <h1 class="hero-title" v-html="settings.hero_title" />
        <h2 class="hero-subtitle" v-html="settings.hero_subtitle" />
    </div>
    <form class="contact-form" name="contact">

        <div class="sender-info">
          <div>
            <label for="name" class="label">Your name</label>
            <input type="text" name="name" />
          </div>
          <div>
            <label for="email" class="label">Your email</label>
            <input type="email" name="email" />
          </div>
        </div>

        <div class="message">
          <label for="message" class="label">Message</label>
          <textarea name="message"></textarea>
        </div>

        <button class="button">Submit form</button>

   </form>
</template>

<script>
export default {
  data() {
    return {
      settings: require("../../data/theme.json")
    }
  }
}
</script>

<style>
.hero {
    text-align: center;
    width: 480px;
    max-width: 100%;
    margin: 0 auto;
    padding: 4rem 0 8rem 0;
}

.hero-title {
    font-size: 3rem;
    font-weight: 700;
    padding: 0;
    margin: 0 0 2rem 0;
}
.hero-title p,
.hero-subtitle p {
    margin: 0;
    padding: 0;
}
.hero-subtitle {
    font-size: 1.15em;
    font-weight: 400;
    line-height: 1.68;
    padding: 0;
    margin: 0;
    opacity: 0.6;
}
</style>
