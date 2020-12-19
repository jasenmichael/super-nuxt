Nuxt + Tailwind + NuxtContent + Netlify + Netlify Identity + NetlifyCms + Tumblr-api + SEO optimization + Open Graph and Twitter head tags.

## Features:

- flat-file site settings using @nuxt/content and netlifyCms(locally or in production)
- at build run tumblr.js to:
  - fetch all Tumblr posts as json
  - download (and add local image paths to json) for all Tumblr(type "photo") to static/img(skip existing)
  - save to nuxt content dir as content/tumblr.json
- all posts by type routes are available at /[type] or /posts?type=[type] (see routes below)
- all posts and all types route is available at /posts (see routes below)
- all styling done in components

---

### Routes

/[type]/[item] >> pages/\_type/\_item.vue

- /posts - pass all posts(all types) to >> PostList.vue
- /[type] - if posts && !item, pass posts(only type) to >> PostList.vue
- /posts?types=[types] - if query.type pass posts(only [types]) to >> PostList.vue (TODO)
- /[type]/[item] - if post && item >> PostItem.vue

/ - (overrides pages/\_type/\_item.vue) >> pages/index.vue

---

### Directory Structure

components/

- Nav.vue
- Footer.vue
- DevPanel.vue
- Page.vue
- Post.vue
- Posts.vue
- =============
- PostsListView.vue
- PostsListViewItemMusic.vue
- PostsListViewItemVideo.vue
- PostsListViewItemPhoto.vue
- PostsListViewItemBlog.vue
- PostsListViewItemArticle.vue
- =============
- PostsMasonryView.vue
- PostsMasonryViewItemMusic.vue
- PostsMasonryViewItemVideo.vue
- PostsMasonryViewItemPhoto.vue
- PostsMasonryViewItemBlog.vue
- PostsMasonryViewItemArticle.vue
- ==============
- PostsGridView.vue
- PostsGridViewItemMusic.vue
- PostsGridViewItemVideo.vue
- PostsGridViewItemPhoto.vue
- PostsGridViewItemBlog.vue
- PostsGridViewItemArticle.vue

content/

- \*.md (for pages) <<-- all .md files in content folder creates a page in navigation.json
- \*/ (for post types) <<-- all folders create a post type in navigation.json
- \_/\_/ (for post content)
- siteData.json <<-- all site settings (configurable via cms)
- navigation.json <<-- generated/updated at build (configurable via cms)
