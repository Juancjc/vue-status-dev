# StatusBadge

Componente Vue para exibir status com ícone animado (Font Awesome).

## Instalação

```sh
npm install status-badge @fortawesome/fontawesome-free
```

## Uso

```vue
<template>
  <!-- Exemplo com posição customizada -->
  <StatusBadge status="finalizado" :size="44" position="right-bottom" />
</template>

<script setup>
import StatusBadge from "status-badge/StatusBadge.vue";
</script>
```

## Props

- `status`: string (ex: `finalizado`, `desenvolvimento`, `finalizando`, `aguardando_aprovacao`, `em_pausa`, `cancelado`)
- `size`: número (tamanho do badge em px)
- `position`: string (define a posição do badge na tela)
  - Opções:
    - `left-top`
    - `middle-top`
    - `right-top`
    - `left-center`
    - `middle-center`
    - `right-center`
    - `left-bottom`
    - `middle-bottom`
    - `right-bottom`
  - Exemplo: `<StatusBadge position="middle-center" />`

## Licença

MIT
