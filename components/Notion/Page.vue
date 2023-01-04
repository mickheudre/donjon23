<template>
    <div>
        <block v-for="content in this.page.results" :key="content.id" :block="content"></block>
    </div>
</template>

<script>
import Block from './Block.vue'

export default {
    components: { Block },
    name: 'Page',
    props : {
        page: Object
    }
}
</script>