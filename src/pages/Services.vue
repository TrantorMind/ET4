<template>
  <Layout>

    <div class="container">
      <div class="journal-hero">
        <h1 class="journal-header">
         It is not just BLACK and WHITE. <br>
         Discover our services: 
        </h1>
      </div>
    </div>

    <g-link 
      :to="item.node.path"
      v-for="item in $page.posts.edges" 
      :key="item.node.id"
      class="journal-post"
    >
      <div class="container journal">
        <h2 class="journal-title">{{ item.node.title }}</h2>
        <p class="journal-excerpt">{{ item.node.excerpt }}</p>
      </div>
      </g-link>

    <div class="container">
      <div class="journal-hero">
        <h2 class="journal-header">
         ...but not limited to.
        </h2>
      </div>
    </div>
      
  </Layout>
</template>

<page-query>
query Journal {
	posts: allJournalPost {
    edges {
      node {
        id
        path
        title
        excerpt
      }
    }
  }
}
</page-query>

<script>
export default {
}
</script>

<style scoped>
.container.journal {
  max-width: 720px;
}
.journal-hero {
  padding: 1rem 0;
  text-align: left;
  color: black;
}
.journal-header {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.journal-post {
  display: block;
  max-block-size: 400px;
  padding: 3rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.journal-post > * {
  transition: transform 0.5s ease;
}
.journal-post:hover {
  background-color: var(--color-base-1);
}
.journal-post:hover > * {
  transform: translateX(4rem);
}
.journal-post h1,
.journal-post h2 {
  margin: 0;
  padding: 0;
}
.journal-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.journal-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .journal-post {
    padding: 1rem 0;
  }
}

@media (min-width: 860px) {
  .journal-post {
    padding: 1rem 0;
  }
}
</style>
