<template>
  <article class="home-page">
    <div class="title-container">
      <h1 class="title">
        DatoCms + Nuxt + Netlify
      </h1>
    </div>
    <ul v-if="posts" class="posts-list">
      <li v-for="post in posts" :key="`post-${post.slug}`" class="post-item">
        <nuxt-link :to="routes.post(post.slug)">{{post.title}}</nuxt-link>
      </li>
    </ul>
  </article>
</template>

<script>
import {request, gql} from '@/cms/datocms';
import {pageMeta} from '@/mixins/pageMeta';

export default {
  mixins: [pageMeta],
  async asyncData() {
    const data = await request({
      query: gql`
        {
          page: homePage {
            title
          }

          posts: allPosts(first: 3) {
            slug
            title
            description
          }
        }
      `,
    });

    return {ready: !!data, ...data};
  },
};
</script>

<style lang="scss" scoped>
.home-page {
  background-color: #000;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 4.44vw;
}

.title-container {
  width: fit-content;
}

.title {
  margin: 0;
  max-width: 9ex;
  font-size: 20vw;
  font-weight: 600;
  line-height: 1;
  text-align: center;

  @media (min-width: 900px) {
    font-size: 200px;
  }
}

.dotcom {
  display: block;
}
</style>
