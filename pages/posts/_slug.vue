<template>
  <div>
    <h1>{{ post.title }}</h1>
    <p>My path is: {{ $route.path }}</p>
    <nav>
      <ul>
        <li v-for="(block, index) in post.blocks" :key="index">
          <NuxtLink :to="{ name: 'posts/slug/block', params: { slug: post.slug, block: index } }">
            {{ block.title }}
          </NuxtLink>
        </li>
      </ul>
    </nav>
    <NuxtChild />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content("posts", params.slug).fetch();

    return {
      post
    };
  }
};
</script>