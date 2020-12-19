<template>
  <div></div>
</template>

<script>
export default {
  layout: 'cms',
  data: () => {
    return {
      url: 'http://localhost:3000',
    }
  },
  mounted() {
    if (process.client) {
      // eslint-disable-line
      NetlifyCmsApp.init({
        // merge config with static/admin/config.yml
        config: {
          site_url: this.url,
        },
      })

      setTimeout(() => {
        // gotta wait for react to be done taking over
        const selector = document.querySelectorAll("a[href='" + this.url + "']")
        selector[2].target = '_self'
        // selector.forEach((el) => {
        //   el.target = '_self'
        // })
      }, 4000)
    }
  },
  head: {
    script: [
      { src: 'https://unpkg.com/react@^16/umd/react.production.min.js' },
      {
        src: 'https://unpkg.com/react-dom@^16/umd/react-dom.production.min.js',
      },
      { src: 'https://unpkg.com/netlify-cms-app/dist/netlify-cms-app.js' },
    ],
  },
}
</script>
