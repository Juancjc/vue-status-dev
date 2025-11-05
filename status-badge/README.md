# StatusBadge

Componente Vue para exibir status com ícone animado (Font Awesome).

## Instalação

```sh
npm install status-badge @fortawesome/fontawesome-free
```

## Uso

```vue
<template>
  <StatusBadge status="finalizado" size="44" />
</template>

<script setup>
import StatusBadge from 'status-badge/StatusBadge.vue'
</script>
```


## Props

- `status`: string (ex: `finalizado`, `desenvolvimento`, `finalizando`, `aguardando_aprovacao`, `em_pausa`, `cancelado`)
- `size`: número (tamanho do badge em px)



## Licença

MIT
