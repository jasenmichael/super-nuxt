<template>
  <div>
    <!-- if posts.length, render PostsList component -->
    <div v-if="posts">
      <Posts :posts="posts" />
      <!-- <pre> <hr> {{ $route.path.slice(1).toUpperCase() }}: {{ posts }}</pre> -->
    </div>

    <!-- if single post, render PostItem component -->
    <div v-if="post">
      <Post :post="post" />
      <!-- <pre> <hr> POST: {{ post }}</pre> -->
    </div>

    <!-- treat as a page -->
    <div v-else>
      <Page :page="page" />
      <!-- <pre> <hr> {{ page }}</pre> -->
    </div>
  </div>
</template>

<script>
import getMeta from '~/plugins/getMeta.js'

export default {
  async asyncData({ $content, $config, params, error }) {
    const isPage =
      $config.navigation.pages
        .map((page) => page.slug)
        .join(' ')
        .includes(params.type) || false
    const isPostType =
      $config.navigation.posts
        .map((post) => post.slug)
        .join(' ')
        .includes(params.type) || false
    // const type = isPage ? 'page' : isPostType ? params.type : null

    // get single post type item /type/itemSlug
    if (isPostType && params.item) {
      const post = await $content(params.type, params.item)
        .fetch()
        .catch(() => {
          error({ statusCode: 404, message: 'Post not found' })
        })
      const posts = null
      const page = null
      return { post, posts, page }
    }

    // get all of one type /type
    if (isPostType && !params.item) {
      const contentPosts = await $content(params.type)
        .fetch()
        .then((posts) => {
          return posts.map((post) => {
            // add type and content source to each post
            return { ...post, type: params.type }
          })
        })
        .catch(() => {
          return []
        })

      const tumblrPosts = await $content('tumblr')
        .where({ type: params.type })
        .fetch()
        .then((posts) => {
          return posts.map((post) => {
            // add source: 'tumblr' to each post
            return { ...post, type: params.type, source: 'tumblr' }
          })
        })
        .catch((err) => {
          return [] || err
        })

      console.log(tumblrPosts)

      const posts = [...tumblrPosts, ...contentPosts]
      const post = null
      const page = null
      return { posts, post, page }
    }

    // get all types /posts
    if (params.type === 'posts' && !params.item) {
      // get content all posts
      const postTypes = $config.navigation.posts.map((posts) => posts.type)
      const contentPosts = []
      Promise.resolve(
        postTypes.forEach(async (type) => {
          await $content(type)
            .fetch()
            .then((posts) => {
              return posts.map((post) => {
                // add type and content source to each post
                contentPosts.push({
                  ...post,
                  type,
                  source: type,
                })
              })
            })
            .catch((err) => {
              return [] || err
            })
        })
      )

      // get all tumblr posts
      const tumblrPosts = await $content('tumblr')
        .fetch()
        .then((posts) => {
          return posts.map((post) => {
            // add source: 'tumblr' to each post
            return { ...post, source: 'tumblr' }
          })
        })
        .catch((err) => {
          return [] || err
        })

      const posts = [...tumblrPosts, ...contentPosts]
      const post = null
      const page = null
      return { posts, post, page }
    }

    // is a page
    if (isPage) {
      const posts = null
      const post = null
      const page = await $content(params.type).fetch()
      return { page, posts, post }
    } else {
      error({ statusCode: 404, message: 'Post not found' })
    }
  },
  data() {
    return {
      query: this.$route.query,
    }
  },
  // computed: {
  //   canonicalUrl() {
  //     return (
  //       ((this.$config.ngrok && this.$config.ngrok.url) ||
  //         this.$config.baseUrl) + this.$route.fullPath
  //     )
  //   },
  //   meta() {
  //     const metaData = {
  //       type: 'website', // use article for blogs and such
  //       title:
  //         this.$config.siteData.name +
  //         ' | ' +
  //         this.params.type.charAt(0).toUpperCase() +
  //         this.params.type.slice(1) +
  //         ' Collection',
  //       description: this.$config.siteData.description,
  //       url: this.canonicalUrl,
  //       mainImage:
  //         ((this.$config.ngrok && this.$config.ngrok.url) ||
  //           this.$config.baseUrl) +
  //         ((this.page && this.page.cover) || '/background.jpg'),
  //     }
  //     return getMeta(metaData, this.$config.siteData, this.canonicalUrl)
  //   },
  // },
  // mounted() {},
  // head() {
  //   return {
  //     // title: this.params.type
  //     //   ? this.params.type + ' collection'
  //     //   : this.$config.siteData.name,
  //     meta: this.meta,
  //     link: [
  //       {
  //         hid: 'canonical',
  //         rel: 'canonical',
  //         href: this.canonicalUrl,
  //       },
  //     ],
  //   }
  // },
}
</script>
