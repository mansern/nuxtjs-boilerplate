<template>
  <div class="container">
    <div>
      <h1 class="title">Nuxt working example</h1>
      <h3 class="sub-title">
        This page demoes the usage of "asyncData" hook to fetch the data from an
        API.<br />
        It waits for its promise to be resolved before rendering the page and
        directly merges the return value to the local state.
      </h3>
      <br />
      <h4>
        This means that:<br /><br />
        - There are no placeholders you can set up<br />
        - If an error occurs, you will be redirected to the error page instead
        of showing an error message on the page route you’re supposed to land
        in<br />
        - You can fetch data using asyncData only in page components.
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
  async asyncData({ params, $http }) {
    const articles = await $http.$get(
      "https://jsonplaceholder.typicode.com/posts"
    );
    return { articles };
  },
};
</script>
