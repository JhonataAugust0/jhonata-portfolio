<template>
  <div class="experiences-container">
    <ExperienceContent
      :text="'Desenvolvedor full-stack — SESI Alagoas'"
      :textPeriod="'Abr 2022 — jan 2024'"
      :experience-description-prop="experienceSesi"
      :technologies-prop="[{'link': 'https://fastapi.tiangolo.com', 'name': 'FastAPI'}, {'link': 'https://vuejs.org', 'name': 'Vue'}, {'link': 'https://docs.docker.com', 'name': 'Docker'}, {'link': 'https://learn.microsoft.com/pt-br/sql/?view=sql-server-ver16', 'name': 'Microsoft SQL Server'}, {'link': 'https://www.rabbitmq.com', 'name': 'RabbitMQ'}]"
    />
    <ExperienceContent
      :text="'Desenvolvedor full-stack — Nexa Brasil'"
      :textPeriod="'Mai 2023 — aug 2024'"
      :experience-description-prop="nexaExperience"
      :technologies-prop="[{'link': 'https://react.dev', 'name': 'React'}, {'link': 'https://docs.nestjs.com', 'name': 'NestJS'}, {'link': 'https://docs.docker.com', 'name': 'Docker'}, {'link': 'https://typeorm.io', 'name': 'TypeORM'}, {'link': 'https://mariadb.org', 'name': 'MariaDB'}]"
    />
    <ExperienceContent
      :text="'Pesquisador — CNPq'"
      :textPeriod="'Mai 2021 — mai 2022'"
      :experience-description-prop="cnpqExperience"
    />
    <ExperienceContent
      :text="'Competidor de robótica — SESI Alagoas'"
      :textPeriod="'Sep 2018 — jul 2021'"
      :experience-description-prop="roboticExperience"
      :technologies-prop="[{'link': 'https://dev.java', 'name': 'Java'}, {'link': 'https://git-scm.com/doc', 'name': 'Git'}]"
    />
  </div>
</template>

<script>

import { defineComponent } from 'vue'
import ExperienceContent from '@/components/ExperienceContent.vue'

export default defineComponent({
  name: 'ExperiencesSection',
  components: { ExperienceContent },
  data () {
    return {
      experienceSesi: 'Atuei ativamente no desenvolvimento de um sistema precursor de automatização e dinamização de processos pioneiro dentro do SESI  utilizando FastAPI. Realizei a migração de sistemas legados do PHP 5.1 para PHP 8.2 com Symfony e o frontend com Vue e Typescript, buscando maior estabilidade, segurança e praticidade. Além disso, fui responsável pelo entendimento de requisitos em projetos impactantes produtiva e financeiramente, colaborei com outros times para otimizar sprints. Ainda, tive a oportunidade de iniciar e desenvolver um projeto voltado para IOT, utilizando tecnologias como RabbitMQ e comunicação RPC. Minha atuação foi marcada por inovação, eficiência e suporte interdisciplinar.',
      nexaExperience: 'Me voluntariei a trabalhar temporariamente na Coordenação de Transformação Digital do Nexa Brasil, colaborei ativamente com um time de desenvolvedores na criação de uma plataforma de gestão abrangente para todos os núcleos regionais da organização. Fui responsável pela criação endpoints, criação de componentes, definição de regras de negócio e pela dockerização da soluão frontend. Meu envolvimento visava contribuir para a eficiência operacional e fortalecimento da missão do Nexa Brasil.',
      roboticExperience: 'Competi na etapa nacional e internacional do torneio First Tech Challenge, representando o estado de Alagoas. Atuei como desenvolvedor de software criando algoritmos para o controle autônomo de protótipos robóticos usando Java. Além disso, em meu período de atuação colaborei para a conquista de dois prêmios inéditos para Alagoas na etapa nacional da temporada de 2020 do First Tech Challenge: o Motivate Award e o Compass Award. E, na temporada de 2021, contribuí para a conquista de mais um prêmio inédito, o Connect Award na etapa nacional e a classificação para o torenio internacional Remote Asia Pacific Championship (Austrália) na mesma temporada, na qual primeiro conquistamos o primeiro lugar do Connect Award no internacional, trazendo um prêmio inédito, dessa vez, para o Brasil.',
      cnpqExperience: 'Como pesquisador do CNPq, trabalhei com uma equipe na concepção e execução de um projeto de arquitetura e urbanismo. O objetivo central foi promover a acessibilidade para pessoas com deficiência visual. A pesquisa não apenas ampliou o entendimento sobre as necessidades específicas desse público, mas também contribuiu para o desenvolvimento de soluções inovadoras visando a inclusão e aprimoramento do ambiente construído. Tivemos a oportunidade de constatar a eficácia da solução ao implantá-la no bloco de sistemas de informação no campus de Penedo da Universidade Federal de Alagoas e na escola estadual Cyro Accioly.'
    }
  }
})
</script>

<style scoped>
.experiences-container {
  left: 0;
  width: 100%;
  position: relative;
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  justify-content: center;
  padding-bottom: 8rem;
  margin-top: calc(10px + 1rem);
}

/* Responsividade para dispositivos móveis */
@media only screen and (max-width: 768px) {
  .experiences-container {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    padding: 10px;                                      /* Reduz o preenchimento do cabeçalho para 10 pixels */
    //top: 230%;                                                 /* Define a distância do topo da janela do navegador como 50% */
    min-height: calc(55vh - 102px);
    left: 0;
    width: 100vw;
  }
}

@media only screen and (max-width: 420px) {
  .experiences-container {
    //top: 296%;
    left: 0;
  }
}
</style>