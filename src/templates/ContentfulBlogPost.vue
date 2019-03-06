<template>
  <Layout>
    <g-image class="hero-image" :src="$page.post.heroImage.file.url" />
    <h1>
      {{$page.post.title}}
    </h1>
    <div v-html="body" />
  </Layout>
</template>

<page-query>
query Post ($path: String!) {
  post: contentfulBlogPost (path: $path) {
    title,
    heroImage {
      file {
        url
      }
    },
    body
  }
}
</page-query>

<script>
import MarkdownIt from 'markdown-it'

export default {
  computed: {
    body() {
      const md = new MarkdownIt()

      return md.render(this.$page.post.body)
    }
  }
}
</script>

<style scoped>
.hero-image {
  width: 100%;
}
</style>
