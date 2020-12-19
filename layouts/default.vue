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
