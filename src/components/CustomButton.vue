<script lang="ts">
import { defineComponent } from 'vue';

interface CustomButtonProps {
  buttonText: string;
  buttonColor: string;
  buttonHeight: string;
  buttonWidth: string;
  buttonBorderColor: string;
  buttonBorderRadius?: string;
  buttonTextColor?: string;
  buttonFontWeight?: string;
  buttonFontSize?: string;
  handleClick?: Function;
}

export default defineComponent({
  name: 'CustomButton',
  props: {
    buttonText: {
      type: String,
      required: true
    },
    buttonColor: {
      type: String,
      default: 'var(--var-color-code-block-blue)'
    },
    buttonHeight: {
      type: String,
      default: '38px'
    },
    buttonWidth: {
      type: String,
      default: '72px'
    },
    buttonBorderRadius: {
      type: String,
      default: '4px'
    },
    buttonBorderColor: {
      type: String,
      default: '1px solid var(--var-color-code-block-blue)'
    },
    buttonTextColor: {
      type: String,
      default: '#3d5264'
    },
    buttonFontWeight: {
      type: String,
      default: '500',
    },
    buttonFontSize: {
      type: String,
      default: '14px',
    },
    handleClick: {
      type: Function,
      required: false,
    },
  },
  data (props: CustomButtonProps) {
    const buttonProps = props;
    return {
      buttonProps,
    }
  },
});
</script>

<template>
  <button
    class="custom-button"
    :style="{
      backgroundColor: buttonProps.buttonColor,
      height: buttonProps.buttonHeight,
      width: buttonProps.buttonWidth,
      borderRadius: buttonProps.buttonBorderRadius,
      border: buttonProps.buttonBorderColor,
      color: buttonTextColor,
      fontWeight: buttonFontWeight,
      fontSize: buttonFontSize,
    }"
    @click="buttonProps.handleClick"
  >
    {{ buttonText }}
  </button>
</template>

<style>
.custom-button {
  display: flex;                                        /* Define os botões como elementos flexíveis */
  align-items: center;                                  /* Centraliza o texto verticalmente dentro dos botões */
  justify-content: center;                              /* Centraliza o texto horizontalmente dentro dos botões */
  padding: 8px 16px;                                    /* Adiciona preenchimento aos botões */
  font-family: Inter, monospace;                        /* Define a fonte dos botões */
  cursor: pointer;                                      /* Altera o cursor para um ponteiro ao passar sobre os botões */
  transition: background-color 0.3s ease;               /* Adiciona uma transição suave à cor de fundo dos botões */
}
</style>