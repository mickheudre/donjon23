<template>
    <p ref="paragraph"> 
        <StyledText v-for="(element, index) in this.block.paragraph.rich_text" :key="index" :text="element"></StyledText>
    </p>
</template>

<script>
import StyledText from './StyledText.vue'

export default {
    components: { StyledText }, 
    props: {
        block: Object
    }
}
</script>