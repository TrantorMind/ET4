<template>
  <Layout>

    <div class="container">
      <div class="projects-hero">
        <h1 class="projects-header">
          OUR PROJECT PORTFOLIO
        </h1>
      </div>
    </div>

    <g-link :to="item.node.path" v-for="item in $page.posts.edges" :key="item.node.id"
      class="projects-post">
      <div class="container projects">
       
        <h2 class="project-title">{{ item.node.title }}</h2>
        <p class="project-excerpt">{{ item.node.excerpt }}</p>
        <g-image
                :src="item.node.thumbnail"
                :alt="item.node.title"
                class="thumbnail"
        />
        
      </div>
    </g-link>
      
  </Layout>
</template>

<page-query>
query Project {
	posts: allProjectPost {
    edges {
      node {
        id
        path
        thumbnail
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
.container.projects {
  display: inline-grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 4rem;
  /* max-width: 720px;*/
}
.projects-hero {
  padding: 4rem 0;
  text-align: center;
  color: var(--color-base-1);
}
.projects-header {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.projects-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.projects-post > * {
  transition: transform 0.5s ease;
}
.projects-post:hover {
  background-color: var(--color-base-1);
}
.projects-post:hover > * {
  transform: translateX(4rem);
}
.thumbnail {
  height: 320px;
  object-fit: cover;
  transition: all 0.15s ease;
  box-shadow: 0 0 40px -20px rgba(0,0,0,0.25);
}
.projects-post h1,
.projects-post h2 {
  margin: 0;
  padding: 0;
}
.project-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.project-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .projects-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .projects-post {
    padding: 5rem 0;
  }
}
</style>
