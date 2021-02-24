# nuxt-datocms-starter

This is a simple starter repository for a skeleton structured web application that is
integrated with DatoCMS.  It leverages basic UI components from the @zaneray/vue-components
package, as well as includes a number of other Vue packages/modules that are preferred for
building out a site with a rich UI.  It is meant to be deployed static to any static web host like Netlify.

## Environment Setup
Copy the `.env-sample` file into a local `.env`, and swap in your own datoCMS API token.

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# generate static project
$ yarn generate

# build for production
$ npm run build
$ npm run start
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
