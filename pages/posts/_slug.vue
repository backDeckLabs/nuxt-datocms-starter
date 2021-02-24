<template>
  <article class="post">
    <page-wrapper spacing>
      <layout-container>
        <base-link :url="routes.home()">Back Home</base-link>
        <h1>{{post.title}}</h1>
      </layout-container>
    </page-wrapper>
  </article>
</template>

<script>
import { request, gql } from '@/cms/datocms';
import PageWrapper from '~/components/layout/PageWrapper';
import LayoutContainer from '~/components/layout/LayoutContainer';
import BaseLink from '~/components/base/BaseLink';

export default {
  components: {BaseLink, LayoutContainer, PageWrapper},
  async asyncData({ params }) {
    const data = await request({
      query: gql`
        query BlogPostQuery($slug: String!) {
          post(filter: { slug: { eq: $slug } }) {
            title
            description
            publicationDate: _firstPublishedAt
          }
        }
      `,
      variables: {
        slug: params.slug
      }
    })

    return { ready: !!data, ...data }
  }
}
</script>
