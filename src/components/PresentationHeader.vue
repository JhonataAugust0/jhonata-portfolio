<script setup lang="ts">
import { defineComponent, onMounted, ref } from 'vue'

const textLanguages = {
  'Python': '\nimport pytest\n' +
    '\n' +
    'def devName() -> str:\n' +
    '    return "Jhonata Augusto"\n' +
    '\n' +
    'def test_devName():\n' +
    '    assert devName() == "Jhonata Augusto"',
  'Php': '\nclass DevName extends PHPUnit\\Framework\\TestCase {\n' +
    '\n' + 'public function devName() {\n' +
    '        $nome = "Jhonata Augusto";\n' +
    '        return $nome;' + '\n' +
    '\npublic function testDevName() {\n' +
    '        $this->assertEquals(devName(), "Jhonata Augusto");\n' +
    '    }\n' +
    '}',
  'C': '\n#include <stdio.h>\n' +
    '#include <assert.h>\n' +
    '\n' +
    'char* devName() {\n' +
    '    return "Jhonata Augusto";\n' +
    '}\n' +
    '\n' +
    'void devName() {\n' +
    '    assert(strcmp(devName(), "Jhonata Augusto") == 0);\n' +
    '}',
  'JS': '\nconst devName() {\n' +
    '    return "Jhonata Augusto";\n' +
    '}\n' +
    '\n' +
    'test(\'Verifica se o nome está correto\', () => {\n' +
    '    expect(Jhonata Augusto()).toBe("Jhonata Augusto");\n' +
    '});',
  'C#': '\nusing NUnit.Framework;\n' +
    '\n' +
    '[TestFixture]\n' +
    'public class DevName {\n' +
    '    [Test]\n' +
    '    public void DevName() {\n' +
    '        Assert.AreEqual(DevName(), "Jhonata Augusto");\n' +
    '    }\n' +
    '}',
};
const buttonText = ref('');

const changeButtonText = (text: string) => {
  buttonText.value = '';
  let index = 0;
  const intervalId = setInterval(() => {
    buttonText.value += textLanguages[text].charAt(index++);
    if (index === textLanguages[text].length) clearInterval(intervalId);
  }, 15);
};

onMounted(() => {
  if (!buttonText.value) {
    changeButtonText('Python'); // Define Python como o texto padrão
  }
});

defineComponent({
  name: "CodeText",
  setup() {
    return {
      buttonText,
      changeButtonText
    };
  }
});
</script>

<template>
  <div class="presentation-container">
    <div class="name-presentation-container">
      <pre>
        <code>
          {{ buttonText }}
        </code>
      </pre>
    </div>

    <div class="programming-languages-button-container">
      <button class="language-programming-button" @click="changeButtonText('Python')">Python</button>
      <button class="language-programming-button" @click="changeButtonText('Php')">Php</button>
      <button class="language-programming-button" @click="changeButtonText('C')">C</button>
      <button class="language-programming-button" @click="changeButtonText('JS')">JS</button>
      <button class="language-programming-button" @click="changeButtonText('C#')">C#</button>
    </div>
    <div class="office-container"></div>
    <div>
    </div>
  </div>
</template>

<style scoped>
.presentation-container{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 620px;
  left: 0;
  right: 0;
  top: 0;
  position: fixed;
  box-sizing: border-box;
  padding-left: 24px;
  padding-right: 24px;
  background-color: var(--var-background-color-blue);
}

.name-presentation-container{
  width: 720px;
  position: fixed;
  top: 30%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 100;
}

pre {
  padding: 16px;
  overflow: auto;
  border-radius: 8px;
  white-space: pre-wrap;
  background-color: #3d5264;
  font-family: monospace;
}

code {
  font-size: 18px;
  color: #ffffff;
}

.hljs-keyword {
  color: #0077ff;
}

.hljs-string {
  color: #a31515;
}

.hljs-comment {
  color: #888;
}

.programming-languages-button-container {
  display: flex;
  justify-content: center;
  position: absolute;
  top: 80%;
  left: 0;
  width: 100%;
  flex-wrap: wrap;
  margin-top: 34px;
}

.language-programming-button {
  margin: 0 6px;
  background-color: #3d5264;
  box-shadow: #1F3547;
  font-family: monospace;
  color: #FFFFFF;
  width: 68px;
  height: 28px;
  border-radius: 4px;
  border-width: 1px;
  border-style: solid;
  border-image: initial;
  border-color: #3d5264;
  text-decoration: none;
  padding: 0px 12px;
  gap: 8px;
  transition: color 80ms cubic-bezier(0.65, 0, 0.35, 1) 0s, fill, background-color, border-color;
}

.language-programming-button:hover {
  background-color: #4A6277;
  transition-delay: 60ms;
}
</style>