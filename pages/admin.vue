<template>
  <div></div>
</template>

<script>
// if (process.client) {
//   const NetlifyCmsApp = require('netlify-cms-app')
// }

export default {
  layout: 'cms',
  data: () => {
    return {}
  },
  mounted() {
    if (process.client) {
      // eslint-disable-line
      // NetlifyCmsApp.init()
      NetlifyCmsApp.init({
        // merge config with static/admin/config.yml
        config: {
          site_url:
            (this.$config.ngrok && this.$config.ngrok.url) ||
            this.$config.baseUrl,
        },
      })
    }
  },
  head: {
    script: [
      { src: 'https://unpkg.com/react@^16/umd/react.production.min.js' },
      {
        src: 'https://unpkg.com/react-dom@^16/umd/react-dom.production.min.js',
      },
      { src: 'https://unpkg.com/netlify-cms-app/dist/netlify-cms-app.js' },
      // { src: 'https://unpkg.com/netlify-cms@^2.0.0/dist/netlify-cms.js' },
    ],
  },
}
</script>
