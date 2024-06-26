<script lang="ts">
import { defineComponent } from 'vue'
import CustomButton from '@/components/CustomButton.vue'

interface TextLanguagesInterface {
  [key: number]: string;
}

export default defineComponent({
  name: "PresentationHeader",
  components: { CustomButton },
  data() {
    const textLanguages: TextLanguagesInterface =  {
        0: '\nimport pytest\n' +
          '\n' +
          'def devName() -> str:\n' +
          '    return "Jhonata Augusto"\n' +
          '\n' +
          'def test_devName():\n' +
          '    assert devName() == "Jhonata Augusto"',
        1: '\nclass DevName extends PHPUnit\\Framework\\TestCase {\n' +
          '\n' + 'public function devName() {\n' +
          '        $nome = "Jhonata Augusto";\n' +
          '        return $nome;' + '\n' + '}\n' +
          '\npublic function testDevName() {\n' +
          '        $this->assertEquals(devName(), "Jhonata Augusto");\n' +
          '    }\n' +
          '}',
        2: '\n#include <stdio.h>\n' +
          '#include <assert.h>\n' +
          '\n' +
          'char* devName() {\n' +
          '    return "Jhonata Augusto";\n' +
          '}\n' +
          '\n' +
          'void devName() {\n' +
          '    assert(strcmp(devName(), "Jhonata Augusto") == 0);\n' +
          '}',
        3: '\nconst devName = () => {\n' +
          '    return "Jhonata Augusto";\n' +
          '}\n' +
          '\n' +
          'test(\'Verifica se o nome está correto\', () => {\n' +
          '    expect(Jhonata Augusto()).toBe("Jhonata Augusto");\n' +
          '});',
        4: '\nusing NUnit.Framework;\n' +
          '\n' +
          '[TestFixture]\n' +
          'public class DevName {\n' +
          '    [Test]\n' +
          '    public void DevName() {\n' +
          '        Assert.AreEqual(DevName(), "Jhonata Augusto");\n' +
          '    }\n' +
          '}',
        5: 'Opa, essa opção infelizmente não temos,\nmas quem sabe você não pode me sugerir isso entrando\n em contato comigo! Veja os links no avatar :)'
      }
    return {
      textLanguages,
      buttonText: "",
      intervalId: 0,
    };
  },
  methods: {
    /**
     * Altera o texto do botão gradualmente com base na chave fornecida.
     * Se a chave fornecida não existir no objeto textLanguages,
     * o texto correspondente à última chave do objeto será utilizado.
     * @param {number} key_text - A chave que indica qual o texto selecionado.
     */
    changeButtonText(key_text: number) {
      this.buttonText = "";
      let index = 0;
      if (this.intervalId) {
        clearInterval(this.intervalId);
      }

      if (!(key_text in this.textLanguages)) {
        const keys = Object.keys(this.textLanguages);
        const numericKeys = keys.map(Number).sort((a, b) => a - b);
        key_text = numericKeys[numericKeys.length - 1];
      }

      this.intervalId = setInterval(() => {
        this.buttonText += this.textLanguages[key_text].charAt(index++);
        if (index === this.textLanguages[key_text].length) clearInterval(this.intervalId);
      }, 10);
    },
  },
  mounted() {
    if (!this.buttonText) {
      this.changeButtonText(0);
    }
  },
});
</script>

<template>
  <div class="presentation-header-container">
    <div class="content-wrapper">
      <div class="text-presentation-container">
        <pre>
          <code>
            {{ buttonText }}
          </code>
        </pre>
      </div>

      <div class="programming-languages-button-container">
        <CustomButton
          buttonText="Python"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="82px"
          buttonHeight="40px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonFontSize="16px"
          buttonTextColor="var(--var-color-text-button-white)"
          @click="changeButtonText(0)"
        />
        <CustomButton
          buttonText="Php"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="82px"
          buttonHeight="40px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonFontSize="16px"
          buttonTextColor="var(--var-color-text-button-white)"
          @click="changeButtonText(1)"
        />
        <CustomButton
          buttonText="C"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="82px"
          buttonHeight="40px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonFontSize="16px"
          buttonTextColor="var(--var-color-text-button-white)"
          @click="changeButtonText(2)"
        />
        <CustomButton
          buttonText="JS"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="82px"
          buttonHeight="40px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonTextColor="var(--var-color-text-button-white)"
          buttonFontSize="16px"
          @click="changeButtonText(3)"
        />
        <CustomButton
          buttonText="C#"
          buttonColor="var(--var-background-modal-blue)"
          buttonWidth="82px"
          buttonHeight="40px"
          borderRadius="4px"
          borderColor="1px solid var(--var-background-modal-blue)"
          buttonFontSize="16px"
          buttonTextColor="var(--var-color-text-button-white)"
          @click="changeButtonText(4)"
        />
      </div>

      <div class="text-office-container">
        <h1 class="text-office">Desenvolvedor de Software</h1>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Essa classe está estilizada para definir um cabeçalho de apresentação fixado no topo da página */
.presentation-header-container {
  position: absolute;                                   /* Define a posição do cabeçalho como fixa */
  top: 0;                                               /* Alinha o cabeçalho no topo da janela do navegador */
  left: 0;                                              /* Alinha o cabeçalho à esquerda da janela do navegador */
  width: 100%;                                          /* Define a largura do cabeçalho para ocupar toda a largura da janela */
  background-color: var(--var-background-color-blue);   /* Define a cor de fundo do cabeçalho */
  z-index: 5;
  box-shadow: var(--var-background-color-dark-blue) 2px 2px 2px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  padding-bottom: 1rem;
}

/* Esta classe define o contêiner de conteúdo, que envolve o conteúdo da apresentação */
.content-wrapper {
  max-width: 1200px;                                    /* Define a largura máxima do contêiner para evitar que o conteúdo fique muito largo em telas grandes */
  margin: 0 auto;                                       /* Centraliza o contêiner horizontalmente */
  display: flex;                                        /* Define o contêiner como um contêiner flexível */
  flex-direction: column;                               /* Define a direção dos filhos do contêiner como coluna */
  align-items: center;                                  /* Centraliza os filhos verticalmente dentro do contêiner */
  padding: 20px 0;                                      /* Adiciona preenchimento ao redor do conteúdo */
}

/* Esta classe define o contêiner para o texto da apresentação */
.text-presentation-container {
  margin-bottom: 2px;                                  /* Adiciona espaço entre os elementos abaixo deste contêiner */
  min-width: 55%;                                       /* Define a largura mínima do contêiner para 55% da largura do contêiner pai */
  overflow: hidden;
}

/* Este estilo define a formatação para o bloco de código */
pre {
  padding: 18px 18px 4px 18px;                          /* Adiciona preenchimento ao redor do bloco de código */
  border-radius: 8px;                                   /* Adiciona cantos arredondados ao bloco de código */
  white-space: pre-wrap;                                /* Define como o espaço em branco deve ser tratado dentro do bloco de código */
  min-height: 355px;
  max-height: 480px;
  width: 100%;
  overflow: hidden;
}

/* Este estilo define a formatação para o texto dentro do bloco de código */
code {
  font-size: 22px;                                      /* Define o tamanho da fonte do texto */
  color: var(--var-color-code-text-white);              /* Define a cor do texto */
  font-family: 'Source Code Pro', Inter, monospace;     /* Define a fonte do bloco de código */
  font-weight: 400;                                     /* Define a espessura da fonte como 300 (leve) */
  overflow: hidden;
}

/* Esta classe define o contêiner para os botões de linguagens de programação */
.programming-languages-button-container {
  display: flex;                                        /* Define o contêiner dos botões como um contêiner flexível */
  justify-content: center;                              /* Centraliza os botões horizontalmente dentro do contêiner */
  gap: 12px;                                            /* Define o espaço entre os botões */
}

/* Esta classe define o estilo do contêiner do texto de cargo */
.text-office-container {
  display: flex;                                        /* Torna o contêiner um contêiner flexível */
  align-items: center;                                  /* Centraliza verticalmente */
  justify-content: center;                              /* Centraliza horizontalmente */
  margin-top: 8px;
}

/* Estilos para o texto da função */
.text-office {
  color: var(--var-color-text-button-white);            /* Define a cor do texto como branco */
  font-family: Inter, monospace;                        /* Define a fonte do texto */
  font-size: 28px;                                      /* Define o tamanho da fonte como 28 pixels */
  font-weight: 500;                                     /* Define a espessura da fonte como 300 (leve) */
  font-style: normal;                                   /* Define o estilo da fonte como normal */
}

/* Responsividade para dispositivos móveis */
@media only screen and (max-width: 768px) {
  .presentation-header-container {
    padding: 10px; /* Reduz o preenchimento do cabeçalho para 10 pixels */
    left: 0;
  }

  .content-wrapper {
    padding: 10px; /* Reduz o preenchimento do conteúdo para 10 pixels */
  }

  .programming-languages-button-container {
    flex-direction: column; /* Altera a direção dos botões para coluna */
  }

  pre {
    min-height: 400px;
    max-height: 630px;
  }

  code {
    font-size: 20px;
  }

  .text-office {
    margin-top: 10px;
    font-size: 24px;
  }
}


@media only screen and (max-width: 420px) {
  .text-presentation-container pre {
    margin-bottom: 16px;
  }

  code {
    font-size: 20px;
  }

  .text-office {
    font-size: 20px;
  }
}
</style>