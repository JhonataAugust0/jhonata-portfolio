<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: "AboutMe",
});
</script>

<template>
  <div class="about-me-container">
    <div class="content-wrapper">
      <div class="text-presentation-container">
        <h1>Sobre mim</h1>
        <p>
          Olá! Eu sou Jhonata, desenvolvedor full-stack com anos de experiência e formação em informática pelo Senac e sistemas de informação pela PUC Minas, mas entrei no mundo da tecnologia quando fui competidor da Olimpíada Brasileira de Informática e de Robótica aos 13 anos!
        </p>
        <p>
          Tenho uma história de sucesso em competições acadêmicas, incluindo também competições de iniciação científicas e torneios de Robótica, com cinco títulos nacionais, um internacional e a publicação de um artigo.
        </p>
        <p>
          Estou animado para compartilhar minhas experiências e projetos, e contribuir significativamente para inovarmos juntos! Vem comigo nessa?
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Estilos para o contêiner do componente AboutMe */
.about-me-container {
  left: 0;
  width: 100vw;
  background-color: var(--var-background-color-dark-blue);
  position: absolute; /* Define o posicionamento relativo */
  top: 50%; /* Move o contêiner para baixo 50% da altura da viewport */
  min-height: calc(60vh - 102px);
}

/* Estilo do contêiner de conteúdo */
.content-wrapper {
  max-width: 1200px; /* Define a largura máxima do contêiner de conteúdo */
  margin: 0 auto; /* Centraliza o conteúdo horizontalmente */
  padding: 20px 0; /* Adiciona preenchimento ao redor do conteúdo */
  display: flex;                                        /* Define o contêiner como um contêiner flexível */
  flex-direction: column;                               /* Define a direção dos filhos do contêiner como coluna */
  align-items: center;
}

/* Estilo do contêiner para o texto da apresentação */
.text-presentation-container {
  margin-top: 80px; /* Adiciona espaço entre os elementos acima deste contêiner */
  width: 100%; /* Define a largura mínima do contêiner para 55% da largura do contêiner pai */
}
</style>