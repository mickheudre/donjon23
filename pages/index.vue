<template>
  <div class="bg-black min-h-screen ">
    <div class="sm:max-w-md sm:mx-auto mx-8"> 
      <h1 class="font-heading text-white text-5xl pt-24 pb-8">Donjon23</h1>
      <Page :page="content" class="text-white pb-24"/>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Page from '@/components/Notion/Page.vue'

export default Vue.extend({
  name: 'IndexPage',
  components: { Page },
  
  async asyncData({ $axios }) {
    const content = await $axios.$get('https://api.notion.com/v1/blocks/7a9a8aac13114b76964ec6cdced3f7bb/children', {
    })
    for await (const results of content.results) {
      if (results.has_children) {
        const child = await $axios.$get(
        `https://api.notion.com/v1/blocks/${results.id}/children`,
        {}
        )
        results.children = child
      }
    }
    
    return { content }

  }
})
</script>

<style lang="css">
h3 {
  @apply italic text-sm mt-16;
}

table {
  @apply w-full;
}
tr, td, th {
  @apply border text-center;
}
</style>