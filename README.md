# Vue Calculadora

Calculadora aritmética simples, construída com Vue 3 e TypeScript, que calcula o resultado automaticamente conforme os valores são digitados.

## Funcionalidades

- Operações: adição, subtração, multiplicação, divisão, resto da divisão (módulo) e potência
- Resultado calculado em tempo real, sem precisar clicar em um botão
- Tratamento de erros para divisão e módulo por zero

## Tecnologias

- [Vue 3](https://vuejs.org/) (Composition API + `<script setup>`)
- [TypeScript](https://www.typescriptlang.org/)
- [Vite](https://vitejs.dev/)

## Como rodar

```bash
npm install
npm run dev
```

Outros comandos disponíveis:

```bash
npm run build    # gera a versão de produção
npm run preview  # visualiza a build de produção localmente
```

## Estrutura do projeto

```text
src/
├── App.vue     # componente principal com a lógica da calculadora
└── main.ts     # ponto de entrada da aplicação
```
