<script setup>
  const { data } = await useAsyncData('home', () => queryContent('/blogs/').only(['_path', 'title', 'description']).find())
</script>

<template>
  <main>
    <h1>pages/blogs/index.vue</h1>
    <pre>
      {{ data }}
    </pre>
    <section v-if="data" class="w-full max-w-5xl mx-auto">
      <blogs post-type="blog" :amount="10" />
    </section>
  </main>
</template>

<script>
import Blogs from '@/components/posts/blogs.vue';

export default {
  components: { Blogs },
  // async setup() {
  //   const { data } = await useAsyncData('home', () => queryContent('/blogs/').only(['_path', 'title', 'description']).find())
  // },
}
</script>
