<template>
  <div>
    <h1>{{ page.title }}</h1>
    <h3>{{ page.description }}</h3>
    <nuxt-content :document="page" />
  </div>
</template>

<script>
export default {
  props: {
    page: {
      type: Object,
      default: null,
    },
  },
}
</script>
