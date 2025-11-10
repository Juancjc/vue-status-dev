# vue-status-dev

Um componente Vue para exibir o status de desenvolvimento de uma página ou sistema.

Para começar:

```sh
npm install
npm run dev

# if using yarn:
yarn
yarn dev

# if using pnpm:
pnpm install
pnpm run dev
```

## Sobre

Este projeto fornece um badge/component para indicar visualmente que determinada página, funcionalidade ou sistema está em desenvolvimento. Ideal para times de desenvolvimento, homologação ou ambientes de staging.

## Instalação via NPM

Para instalar o componente em seu projeto Vue 3:

```sh
npm install vue-status-badge
```

## Como usar

Importe e utilize o componente no seu projeto:

```vue
<template>
  <StatusBadge status="desenvolvimento" size="44" />
</template>

<script setup>
import StatusBadge from "vue-status-badge/StatusBadge.vue";
</script>
```

### Props disponíveis

- `status`: string (ex: `finalizado`, `desenvolvimento`, `finalizando`, `aguardando_aprovacao`, `em_pausa`, `cancelado`)
- `size`: número (tamanho do badge em px)

> **Nota:** O pacote depende do `@fortawesome/fontawesome-free` para os ícones. Certifique-se de instalar essa dependência.

## Funcionalidades

- Badge de status customizável
- Fácil integração em projetos Vue
- Visual moderno

## Licença

MIT

---

> Feito para facilitar a comunicação visual do status de desenvolvimento em projetos Vue.
