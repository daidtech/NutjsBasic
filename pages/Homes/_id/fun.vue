<template>
  <div id="test" class="text-center">
    <h1>
      {{ test }}
    </h1>
  </div>
</template>

<script>
export default {
  name: "Fun",
  layout: "fun",
  head() {
    return {
      title: "test",
    };
  },
  data() {
    return {
      test: "Hello",
    };
  },
  beforeCreate: function () {
    console.log("beforeCreate");
  },
  created: function () {
    console.log("created");
  },
  destroyed: function () {
    console.log("destroyed");
  },
  async asyncData(context) {
    const id = context.params.id;
    try {
      // Using the nuxtjs/http module here exposed via context.app
      const post = await context.app.$http.$get(
        `https://api.nuxtjs.dev/posts/${id}`
      );
      return { post };
    } catch (e) {
      context.error(e); // Show the nuxt error page with the thrown error
    }
  },
};
</script>

<style>
</style>