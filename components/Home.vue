<template>
  <div>
    <nuxt-content :document="page"></nuxt-content>
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
