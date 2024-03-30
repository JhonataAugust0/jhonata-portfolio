<template>
  <div class="skills-container">
    <div class="content-wrapper">
      <div class="text-skills-container">
        <TextContent
          :text=text
          :textFontSize="'22px'"
          :textBackgroundColor="'transparent'"
          :textBorderColor="'transparent'"
        />
      </div>

      <div v-if="skillsIconsPaths[skillText]" class="abilities-container">
        <img v-for="(icon, index) in skillsIconsPaths[skillText]" :src="icon" :key="index" class="skill-icon fade-in" alt="Skills">
      </div>
      <div v-else class="abilities-container">
        <p>{{ skillsIconsPaths[3][0] }}</p>
      </div>

      <div class="programming-skills-button-container">
        <CustomButton
          buttonText="Linguagens de programação"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="176px"
          buttonHeight="58px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonTextColor="var(--var-color-text-button-white)"
          buttonFontSize="16px"
          @click="changeSkillIcon(0)"
        />

        <CustomButton
          buttonText="Bancos de dados"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="176px"
          buttonHeight="58px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonTextColor="var(--var-color-text-button-white)"
          buttonFontSize="16px"
          @click="changeSkillIcon(1)"
        />

        <CustomButton
          buttonText="Ferramentas"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="176px"
          buttonHeight="58px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonTextColor="var(--var-color-text-button-white)"
          buttonFontSize="16px"
          @click="changeSkillIcon(2)"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TextContent from '@/components/TextContent.vue'
import CustomButton from '@/components/CustomButton.vue'

interface SkillsIconsPathsInterface {
  [key: number]: string[];
}

export default defineComponent({
  name: "SkillsSection",
  components: { CustomButton, TextContent },
  data () {
    const text = ["Aqui vai uma lista das tecnologias e", "ferramentas que possuo experiência!"]
    const skillsIconsPaths: SkillsIconsPathsInterface = {
      0: [
        '/icons/python-icon.svg',
        '/icons/js-icon.svg',
        '/icons/ts-icon.svg',
        '/icons/php-icon.svg',
        '/icons/c-sharp-icon.svg'
      ],
      1: [
        '/icons/postgres-icon.svg',
        '/icons/mssql-icon.svg',
        '/icons/mysql-icon.svg'
      ],
      2: [
        '/icons/git-icon.svg',
        '/icons/docker-icon.svg',
        '/icons/linux-icon.svg',
        '/icons/aws-icon.svg',
        '/icons/rabbitmq-icon.svg'
      ],
      3: ['Opa, essa habilidade eu não desenvolvi ainda, haha 😅'],
    }
    return {
      text,
      skillsIconsPaths,
      skillText: 0,
      showAbilities: false,
    }
  },
  methods: {
    /**
     * Altera o texto do botão gradualmente com base na chave fornecida.
     * Se a chave fornecida não existir no objeto textLanguages,
     * o texto correspondente à última chave do objeto será utilizado.
     * @param {number} key_text - A chave que indica qual o texto selecionado.
     */
    changeSkillIcon(key_text: number) {
      if (!(key_text in this.skillsIconsPaths)) {
        const keys = Object.keys(this.skillsIconsPaths);
        const numericKeys = keys.map(Number).filter(Number.isInteger).sort((a, b) => a - b);
        key_text = numericKeys[numericKeys.length - 1]
      }
      this.skillText = key_text;
      this.showAbilities = false;
      setTimeout(() => {
        this.showAbilities = true;
      }, 50);
    }
  },
  mounted() {
    if (!this.skillText) {
      this.changeSkillIcon(0);
    }
  },
});
</script>

<style scoped>
.skills-container {
  left: 0;
  top: 0;
  position: relative;                                   /* Define a posição do cabeçalho como fixa */
  width: 100%;                                         /* Define a largura do cabeçalho para ocupar toda a largura da janela */
  background-color: var(--var-background-color-blue);   /* Define a cor de fundo do cabeçalho */
  z-index: 5;
  box-shadow: var(--var-background-color-dark-blue) 2px 2px 2px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

/* Estilo do contêiner de conteúdo */
.content-wrapper {
  max-width: 1200px;                                    /* Define a largura máxima do contêiner para evitar que o conteúdo fique muito largo em telas grandes */
  margin: 0 auto;                                       /* Centraliza o contêiner horizontalmente */
  display: flex;                                        /* Define o contêiner como um contêiner flexível */
  flex-direction: column;                               /* Define a direção dos filhos do contêiner como coluna */
  align-items: center;                                  /* Centraliza os filhos verticalmente dentro do contêiner */
  padding: 20px 0;                                      /* Adiciona preenchimento ao redor do conteúdo */
  z-index: 5;
}

/* Estilo do contêiner para o texto da apresentação */
.text-skills-container {
  justify-content: center;                              /* Centraliza os botões horizontalmente dentro do contêiner */
  gap: 12px;                                            /* Define o espaço entre os botões */                                 /* Define a direção dos itens flexíveis como linha */
  min-width: 55%;
  overflow: hidden;
}

.programming-skills-button-container {
  display: flex;                                        /* Define o contêiner dos botões como um contêiner flexível */
  justify-content: center;                              /* Centraliza os botões horizontalmente dentro do contêiner */
  gap: 12px;                                            /* Define o espaço entre os botões */
}

.abilities-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding: 24px;
  gap: 64px;
  transition: opacity 0.5s ease;
}

.skill-icon {
  max-width: 128px;
}

.fade-in {
  opacity: 1;
}

/* Responsividade para dispositivos móveis */
@media only screen and (max-width: 768px) {
  .skills-container {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    padding: 10px;                                      /* Reduz o preenchimento do cabeçalho para 10 pixels */
    top: 160%;                                                 /* Define a distância do topo da janela do navegador como 50% */
    min-height: calc(55vh - 102px);
    left: 0;
  }

  .content-wrapper {
    padding: 10px;                                      /* Reduz o preenchimento do conteúdo para 10 pixels */
  }

  .text-skills-container:first-child {
    font-size: 16px;                                    /* Reduz o tamanho da fonte do texto para 16 pixels */
  }

  .programming-skills-button-container {
    flex-direction: column;                             /* Altera a direção dos botões para coluna */
  }

  .abilities-container {
    gap: 20px
  }
}

@media only screen and (max-width: 420px) {
  .skills-container {
    //top: 208%;
      min-height: calc(55vh - 102px);
    left: 0;
  }
}
</style>