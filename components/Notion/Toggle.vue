<template>
    <div class="mx-auto my-8 md:w-1/3 toggle">
        <div class="mx-auto my-4 flex justify-between cursor-pointer" @click="visible=!visible">
            <h5 class="inline-block text-leaf font-sans text-lg font-semibold">
                {{ block.toggle.rich_text[0].plain_text }}
            </h5>
            <Chevron class="inline-block text-leaf transform" :class="[visible ? 'rotate-90' :'']" />
        </div>
        <div  :class="visible ? 'block' : 'hidden'">
            <p class="toggle-text" v-for="element in this.block.children.results" :key="element.id">{{ element.paragraph.rich_text[0].plain_text }}</p>
        </div>
    </div>
</template>

<script>
import Chevron from './Chevron.vue'

export default {
    name: 'Toggle',
    components: { Chevron},
    props: {
        block: Object
    },
    data () {
        return {
            visible: false
        }
    }
}
</script>
