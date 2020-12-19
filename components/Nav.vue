<template>
  <div>
    <DevPanel v-if="$config.dev" />
    <nav class="flex mx-6 py-2 items-center">
      <nuxt-link to="/" class="exact-link text-2xl mr-auto my-auto">
        {{ $config.siteData ? $config.siteData.name : 'Site Name Here' }}
        <!-- <span class="text-sm truncate overflow-ellipsis">
        {{ $config.siteData.description }}
      </span> -->
      </nuxt-link>
      <nuxt-link
        v-for="page in $config.navigation.pages"
        :key="page.title"
        :to="page.path"
        class="px-2 hover:shadow-md rounded-sm border-solid border-2 border-grey-400"
      >
        {{ page.title }}
      </nuxt-link>
    </nav>
    <div class="flex justify-evenly text-center">
      <nuxt-link
        v-for="(postType, i) in $config.navigation.posts"
        :key="i"
        :to="postType.path"
      >
        {{ postType.title }}
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {}
  },
}
</script>
