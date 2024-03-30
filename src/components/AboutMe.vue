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
      avatarImage: "/avatar-2.jpg",
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
        <div class="contact">
          <ul class="contact-icons">
            <li>
              <a href="https://github.com/JhonataAugust0" target="_blank" rel="noopener noreferrer" >
                <img src="/icons/github-icon.svg" alt="Github" height="38px" width="48"/>
              </a>
            </li>
            <li>
              <a href="https://www.linkedin.com/in/jhonata-augusto-2301541b5/" target="_blank" rel="noopener noreferrer" >
                <img src="/icons/linkedin-icon.svg" alt="LinkedIn" height="42px" width="42px"/>
              </a>
            </li>
            <li>
              <a href="mailto:jhon.augustosilva@gmail.com" target="_blank" rel="noopener noreferrer" >
                <img src="/icons/gmail-icon.svg" alt="Email" height="38px" width="48"/>
              </a>
            </li>
            <li>
              <a href="https://wa.me/5582982136275?text=Ol%C3%A1%2C+vim+do+seu+portf%C3%B3lio+e+gostaria+de+falar+com+voc%C3%AA%21" target="_blank" rel="noopener noreferrer" >
                <img src="/icons/whatsapp-icon.svg" alt="WhatsApp" height="42px" width="38"/>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Estilos para o contêiner do componente AboutMe */
.about-me-container {
  left: 0;
  top: 0;
  width: 100%;             /* Define a largura do contêiner como 100% */
  background-color: var(--var-background-color-dark-blue);
  position: relative;      /* Alterado para "relative" para alinhar com base no corpo da página */
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center; /* Centraliza o conteúdo horizontalmente */
  align-items: center;                        /* Centraliza o conteúdo verticalmente */
  margin-top: calc(100px + 28rem);            /* Ajusta a margem superior para começar abaixo do PresentationHeader */
}

.content-wrapper {
  max-width: 1200px;       /* Define a largura máxima do conteúdo */
  width: 100%;             /* Garante que o conteúdo se ajuste à largura do contêiner pai */
  padding: 20px;           /* Adiciona preenchimento ao redor do conteúdo */
  box-sizing: border-box;  /* Inclui preenchimento e borda no cálculo da largura */
}

/* Estilo do container que comporta o avatar e o texto de apresentação */
.content{
  display: flex;                                            /* Define o contêiner como um contêiner flexível */
  gap: 12px;                                                /* Define  o espaçço entre os itens de um container flexivel como 12px*/
  overflow: hidden;
}

/* Estilo do contêiner para o texto da apresentação */
.text-presentation-container {
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
  font-size: 24px;                                          /* Define o tamanho da fonte como 28 pixels */
  font-weight: 400;                                         /* Define a espessura da fonte como 300 (leve) */
  font-style: normal;                                       /* Define o estilo da fonte como normal */
}

.contact {
  position: relative;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.contact-icons {
  list-style: none;
  padding: 0;
  margin: 12px 0 0; /* Espaçamento superior para separar do ModalContent */
  display: flex;
  gap: 9px
}

.contact-icons ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  gap: 32px
}

.contact-icons li {
  margin-right: 20px;
}

.contact-icons li:last-child {
  margin-right: 0;
}

.contact-icons li a {
  display: block;
  text-decoration: none;
  background-color: transparent;
}

.contact-icons img {
  align-items: center;
  justify-content: center;
}

/* Responsividade para dispositivos móveis */
@media only screen and (max-width: 768px) {
  .about-me-container {
    padding: 10px;                                      /* Reduz o preenchimento do cabeçalho para 10 pixels */
    margin-top: calc(100px + 54em);                                          /* Define a distância do topo da janela do navegador como 68% */
  }

  .content-wrapper {
    padding: 10px;                                      /* Reduz o preenchimento do conteúdo para 10 pixels */
  }

  .text-presentation-container h1 {
    font-size: 22px;                                    /* Reduz o tamanho da fonte do texto para 16 pixels */
  }

  .content {
    display: flex;
    flex-wrap: wrap;
  }

  .contact-icons {
    gap: 16px;
    flex-wrap: wrap;
  }
}

@media only screen and (max-width: 420px) {
  .about-me-container {
    padding: 10px;                                      /* Reduz o preenchimento do cabeçalho para 10 pixels */
    left: 0;
  }
}
</style>