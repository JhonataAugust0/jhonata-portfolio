<template>
  <ModalContent>
    <template v-slot:content>
      <p class="a" v-html="formattedText" :style="{
        fontFamily: textFontFamily,
        fontStyle: textFontStyle,
        lineHeight: textLineHeight,
        color: textTextColor,
        fontWeight: textFontWeight,
        fontSize: textFontSize,
        textAlign: definitionTextAlign,
      }"></p>
    </template>
  </ModalContent>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ModalContent from '@/components/ModalContent.vue'

interface TextModalProps {
  text: string[];
  textFontFamily?: string;
  textFontStyle?: string;
  textLineHeight?: string;
  textAlign?: string;
  textTextColor?: string;
  textFontWeight?: string;
  textFontSize?: string;
}

export default defineComponent({
  name: 'TextContent',
  components: { ModalContent },
  props: {
    text: {
      type: Array as () => string[],
      required: true
    },
    textFontFamily: {
      type: String,
      default: 'Inter, monospace'
    },
    textFontStyle: {
      type: String,
      default: '1.5'
    },
    textLineHeight: {
      type: String,
      default: 'normal'
    },
    textAlign: {
      type: String,
      default: 'justify'
    },
    textTextColor: {
      type: String,
      default: 'var(--var-color-text-button-white)'
    },
    textFontWeight: {
      type: String,
      default: '400',
    },
    textFontSize: {
      type: String,
      default: '18px'
    },
  },
  computed: {
    formattedText(): string {
      return this.text.join('<br>');
    }
  },
  data(props: TextModalProps) {
    const definitionTextAlign: 'justify' | 'left' | 'center' | 'right' = props.textAlign ? props.textAlign as 'justify' | 'left' | 'center' | 'right' : 'justify';
    return {
      definitionTextAlign,
    };
  }
});
</script>