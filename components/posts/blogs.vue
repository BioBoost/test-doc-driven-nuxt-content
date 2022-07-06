<template>
  <main>
    <h1>components/posts/blogs.vue</h1>
    <pre>
      {{ blogs }}
    </pre>
    <ul>
      <li v-for="blog in blogs.data" :key="blog._path"><a :href="blog._path">{{blog.title}}</a> </li>
    </ul>

  </main>
</template>


<script>
export default {
  name: 'Blogs',
  data() {
    return {
      blogs: [],
      loading: true,
    }
  },
  async mounted() {
    this.loading = true;
    this.blogs = await this.fetchBlogs();
    this.loading = false;
  },
    methods: {
      async fetchBlogs() {
        return useAsyncData('home', () => queryContent('/blogs/').only(['_path', 'title', 'description']).find())
      }
    },
}
</script>
