<script lang="ts">
import { defineComponent } from 'vue'
import TextContent from '@/components/TextContent.vue'
import ModalContent from '@/components/ModalContent.vue'

export default defineComponent({
  name: "AboutMe",
  components: { ModalContent, TextContent },
  data () {
    const textAboutMe = [
      "Olá! Me chamo Jhonata, sou desenvolvedor full-stack com 3 anos de experiência e formação em informática pelo Senac e em sistemas de informação pela PUC Minas, mas entrei no mundo da tecnologia quando fui competidor da Olimpíada Brasileira de Informática e de Robótica aos 13 anos!",
      "Tenho uma história de sucesso em competições acadêmicas, incluindo também competições de iniciação científicas e torneios de Robótica, com cinco títulos nacionais, um internacional e a publicação de um artigo.",
      "Estou animado para compartilhar minhas experiências e projetos, e contribuir significativamente para inovarmos juntos! Vem comigo nessa?"
    ]
    return {
      textAboutMe,
      avatarImage: "../../public/avatar-2.jpg",
    }
  },
});
</script>

<template>
  <div class="about-me-container">
    <div class="content-wrapper">
      <div class="text-presentation-container">
        <h1>Sobre mim</h1>
        <div class="content">
          <ModalContent
            :content="avatarImage"
            :imageWidth="'240px'"
            :imageHeight="'216px'"
            modalPadding="12px"
            modalBorderRadius="8px"
            modalBackgroundColor="var(--var-background-modal-blue)"
          />
          <TextContent :text=textAboutMe />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Estilos para o contêiner do componente AboutMe */
.about-me-container {
  left: 0;
  width: 100vw;                                             /* Define a largura do contêiner como 100% da largura da janela do navegador */
  background-color: var(--var-background-color-dark-blue);  /* Define a cor de fundo do container*/
  position: absolute;                                       /* Define o contêiner como uma posição absoluta */
  display: inline-flex;
  flex-wrap: wrap;
  gap: 12px;
  top: 45%;                                                 /* Define a distância do topo da janela do navegador como 50% */
    min-height: calc(55vh - 102px);                         /* Define a altura mínima do contêiner como 60% da altura da janela do navegador, menos 102 pixels */
}

/* Estilo do contêiner de conteúdo */
.content-wrapper {
  max-width: 1200px;                                        /* Define a largura máxima do contêiner de conteúdo */
  margin: 0 auto;                                           /* Centraliza o conteúdo horizontalmente */
  padding: 20px 0;                                          /* Adiciona preenchimento ao redor do conteúdo */
  display: flex;                                            /* Define o contêiner como um contêiner flexível */
  flex-direction: column;                                   /* Define a direção dos filhos do contêiner como coluna */
  align-items: center;                                      /* Centraliza os filhos verticalmente dentro do contêiner */
  z-index: 5;                                               /* Define a ordem de empilhamento do elemento como 5 */
}

/* Estilo do container que comporta o avatar e o texto de apresentação */
.content{
  display: flex;                                            /* Define o contêiner como um contêiner flexível */
  gap: 12px;                                                /* Define  o espaçço entre os itens de um container flexivel como 12px*/
  overflow: hidden;
}

/* Estilo do contêiner para o texto da apresentação */
.text-presentation-container {
  margin-top: 80px;                                         /* Adiciona espaço entre os elementos acima deste contêiner */
  width: 100%;                                              /* Define a largura mínima do contêiner para 55% da largura do contêiner pai */
  display: flex;                                            /* Define o contêiner como um contêiner flexível */
  flex-wrap: wrap;                                          /* Permite que os itens flexíveis sejam dispostos em várias linhas */
  flex-direction: row;                                      /* Define a direção dos itens flexíveis como linha */
  overflow: hidden;
}


/* Estilo do título */
h1 {
  color: var(--var-color-text-button-white);                /* Define a cor do texto como branco */
  font-family: Inter, monospace;                            /* Define a fonte do texto */
  font-size: 22px;                                          /* Define o tamanho da fonte como 28 pixels */
  font-weight: 400;                                         /* Define a espessura da fonte como 300 (leve) */
  font-style: normal;                                       /* Define o estilo da fonte como normal */
}

/* Responsividade para dispositivos móveis */
@media only screen and (max-width: 768px) {
  .about-me-container {
    padding: 10px;                                      /* Reduz o preenchimento do cabeçalho para 10 pixels */
    top: 70%;                                           /* Define a distância do topo da janela do navegador como 68% */
  }

  .content-wrapper {
    padding: 10px;                                      /* Reduz o preenchimento do conteúdo para 10 pixels */
  }

  .text-presentation-container {
    font-size: 16px;                                    /* Reduz o tamanho da fonte do texto para 16 pixels */
  }

  .content {
    display: flex;
    flex-wrap: wrap;
  }
}
</style>