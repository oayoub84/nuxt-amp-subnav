<template>
  <div>
    <h1>BLOCK: {{ block.title }}</h1>
    <p>My path is: {{ $route.path }}</p>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content("posts", params.slug).fetch();
    const block = post.blocks[params.block];

    return {
      post,
      block
    };
  }
};
</script>