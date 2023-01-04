<template>
  <div>
    <h3
      v-if="isValidHeading3(this.block)"
    >
      {{ this.block.heading_3.rich_text[0].plain_text }}
    </h3>
    <paragraph
      v-if="isValidParagraph(this.block)"
      class="my-2"
      v-bind:block="this.block"
    >
    </paragraph>
    <li v-if="isValidBulletedListItem(this.block)">
      {{ this.block.bulleted_list_item.rich_text[0].plain_text }}
    </li>
    <toggle v-if="isValidToggleItem(this.block)" :block="this.block" />
    <Table v-if="isValidTableItem(this.block)" :block="this.block" />
  </div>
</template>

<script>
import Paragraph from "./Paragraph.vue";
import Toggle from "./Toggle.vue"
import Table from "./Table.vue"

export default {
  name: 'Block',
  components: { Paragraph, Toggle, Table },
  props: {
    block: Object,
  },
  methods: {
    isValidParagraph(block) {
      if (block.type !== "paragraph") {
        return false;
      }

      if (block.paragraph.rich_text.length == 0) {
        return false;
      }

      if (block.paragraph.rich_text[0].plain_text.length == 0) {
        return false;
      }
      return true;
    },
    isValidHeading3(block) {
      if (block.type !== "heading_3") {
        return false;
      }
      if (block.heading_3.rich_text.length == 0) {
        return false;
      }

      if (block.heading_3.rich_text[0].plain_text.length == 0) {
        return false;
      }
      return true;
    },
    isValidBulletedListItem(block) {
      if (block.type !== "bulleted_list_item") {
        return false;
      }

      if (block.bulleted_list_item.rich_text.length == 0) {
        return false;
      }

      if (block.bulleted_list_item.rich_text[0].plain_text.length == 0) {
        return false;
      }
      return true;
    },
    isValidToggleItem(block) {
      if (block.type !== "toggle") {
        return false;
      }
      
      if (block.toggle.rich_text.length == 0) {
        return false;
      }

      if (block.toggle.rich_text[0].plain_text.length == 0) {
        return false;
      }
      return true;
    },
    isValidTableItem(block) {
      if (block.type !== "table") {
        return false;
      }
      // if (block.table.rich_text.length == 0) {
      //   return false;
      // }

      // if (block.toggle.rich_text[0].plain_text.length == 0) {
      //   return false;
      // }
      return true;
    },
  },
};
</script>