<template>
  <div>
    <h1>I am the posts view</h1>
    <nav>
      <ul>
        <li v-for="post in posts" :key="post.slug">
          <NuxtLink :to="{ name: 'posts/slug', params: { slug: post.slug } }">{{ post.title }}</NuxtLink>
        </li>
      </ul>
    </nav>
    <NuxtChild />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const posts = await $content("posts").only(["title", "slug"]).fetch();

    return {
      posts
    };
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
}
li {
  margin: 0 0.5rem;
  padding: 0.25rem;
  font-size: 1rem;
}
</style>