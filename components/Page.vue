<template>
  <div>
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
