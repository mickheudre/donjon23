<template>
  <div class="bg-black min-h-screen"> 
    <h1>Donjon28</h1>
    <Page :page="content" class="text-white "/>
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
    console.log(content)
    return { content }
  },
})
</script>
