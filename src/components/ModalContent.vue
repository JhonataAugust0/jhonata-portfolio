<template>
  <div class="container-description" :style="{
    borderRadius: modalBorderRadius,
    backgroundColor: modalBackgroundColor,
    padding: modalPadding,
    border: modalBorderColor,
  }">
    <slot name="content"></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface ModalContentProps {
  modalBorderRadius?: string;
  modalBackgroundColor?: string;
  modalPadding?: string;
  modalBorderColor?: string;
}

export default defineComponent({
  name: 'ModalContent',
  props: {
    modalBorderRadius: {
      type: String,
      default: '8px'
    },
    modalBackgroundColor: {
      type: String,
      default: 'var(--var-background-color-cian)'
    },
    modalPadding: {
      type: String,
      default: '12px 28px 12px 28px'
    },
    modalBorderColor: {
      type: String,
      default: '1px solid var(--var-color-code-block-blue)'
    },
  },
});
</script>

<style scoped>
.container-description {
  display: flex;
  margin-top: 6px;
  left: 0;
}
</style>