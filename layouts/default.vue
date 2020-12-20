<template>
  <div
    class="flex flex-col mx-auto min-h-screen px-3 md:w-10/12 lg:max-w-screen-lg"
  >
    <!-- header -->
    <header>
      <Nav />
    </header>
    <!-- header -->

    <main class="flex-grow">
      <hr />
      <Nuxt />
    </main>

    <footer>
      <hr />
      <p class="copyright">Copyright 2019 Super Nuxt!</p>
    </footer>
  </div>
</template>

<script>
import netlifyIdentity from 'netlify-identity-widget'

export default {
  mounted() {
    if (window.netlifyIdentity) {
      window.netlifyIdentity.on('init', (user) => {
        if (!user) {
          window.netlifyIdentity.on('login', () => {
            document.location.href = '/admin/'
          })
        }
      })
    }
  },
}
</script>
