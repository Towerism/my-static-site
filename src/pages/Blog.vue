<template>
  <Layout>
    <p>
      Articles:
    </p>
    <ul>
      <li v-for="{ node } in $page.posts.edges" :key="node.id">
        <g-link :to="node.path">
          {{node.title}}
        </g-link>
      </li>
    </ul>
  </Layout>
</template>

<page-query>
query Posts {
  posts: allContentfulBlogPost {
    edges {
      node {
        id,
        title,
        path
      }
    }
  }
}
</page-query>
