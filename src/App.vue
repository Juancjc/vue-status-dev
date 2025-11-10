<script setup>
import StatusBadge from "./StatusBadge.vue";
</script>

<template>
  <div style="display: flex; gap: 20px; flex-wrap: wrap">
    <StatusBadge status="desenvolvimento" :size="50" position="left-top" />
    <StatusBadge status="finalizando" :size="50" position="middle-top" />
    <StatusBadge status="finalizado" :size="50" position="right-top" />
    <StatusBadge status="em_pausa" :size="50" position="left-center" />
    <StatusBadge
      status="aguardando_aprovacao"
      :size="50"
      position="middle-center"
    />
    <StatusBadge status="cancelado" :size="50" position="right-center" />
    <StatusBadge status="finalizando" :size="50" position="left-bottom" />
    <StatusBadge status="desenvolvimento" :size="50" position="middle-bottom" />
    <StatusBadge status="finalizado" :size="50" position="right-bottom" />
  </div>
</template>
