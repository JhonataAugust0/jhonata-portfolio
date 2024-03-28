<template>
  <div class="container-description" :style="{
    borderRadius: modalBorderRadius,
    backgroundColor: modalBackgroundColor,
    padding: modalPadding,
    border: modalBorderColor,
  }">
    <template v-if="isImage">
      <img :src="content" alt="Imagem" :style="{ width: imageWidth, height: imageHeight }" />
    </template>
    <template v-else>
      <div>
        <slot name="content">{{ content }}</slot></div>
    </template>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface ModalContentProps {
  modalBorderRadius?: string;
  modalBackgroundColor?: string;
  modalPadding?: string;
  modalBorderColor?: string;
  imageWidth?: string;
  imageHeight?: string;
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
      default: 'var(--var-background-modal-blue)'
    },
    modalPadding: {
      type: String,
      default: '12px 28px 12px 28px'
    },
    modalBorderColor: {
      type: String,
      default: '1px solid var(--var-background-modal-blue)'
    },
    content: {
      type: String,
      default: ''
    },
    imageWidth: {
      type: String,
      default: 'auto'
    },
    imageHeight: {
      type: String,
      default: 'auto'
    }
  },
  computed: {
    isImage(): boolean {
      return typeof this.content === 'string' && /\.(jpg|jpeg|png|gif|svg|ico)$/.test(this.content);
    }
  },
});
</script>

<style scoped>
.container-description {
  display: flex;
  margin-top: 6px;
  left: 0;
}

@media only screen and (max-width: 768px) {
  .container-description {
    width: 95%;
    justify-content: center;
    align-items: center;
  }
}
</style>
