<template>
  <div class="container">
    <div>
      <h1 class="title">Nuxt working example</h1>
      <h3 class="sub-title">
        This page demoes the usage of "fetch" hook to fetch the data from an
        API.
      </h3>
      <br />
      <h4>
        "fetch" is a hook called during server-side rendering after the
        component instance is created, and on the client when navigating. The
        fetch hook should return a promise (whether explicitly, or implicitly
        using async/await) that will be resolved:<br /><br />
        - On the server, before the initial page is rendered<br />
        - On the client, some time after the component is mounted.
      </h4>
      <br />
      <div v-for="article in articles" :key="article.id">
        <p>
          {{ article.title }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: [],
    };
  },

  async fetch() {
    this.articles = await fetch(
      "https://jsonplaceholder.typicode.com/posts"
    ).then((res) => res.json());
  },
};
</script>

<style>
.container {
  margin-left: 20px;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
.sub-title {
  margin-bottom: 20px;
}
</style>
