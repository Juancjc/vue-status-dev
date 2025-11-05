<template>
  <span class="status-badge" :style="styleVars" :title="label">
    <i :class="iconClass" aria-hidden="true"></i>
  </span>
</template>

<script setup>
import { computed } from "vue";
import "@fortawesome/fontawesome-free/css/all.min.css";
const props = defineProps({
  status: { type: String, default: "finalizado" },
  size: { type: Number, default: 44 },
});

const statusMap = {
  desenvolvimento: {
    icon: "fas fa-laptop-code",
    color: "#dc3333",
    label: "Em Desenvolvimento",
  },
  finalizando: {
    icon: "fas fa-tools",
    color: "#F59E0B",
    label: "Finalizando",
  },
  aguardando_aprovacao: {
    icon: "fas fa-hourglass-half",
    color: "#F59E0B",
    label: "Aguardando Aprovação",
  },
  em_pausa: {
    icon: "fas fa-pause-circle",
    color: "#c026d3",
    label: "Em Pausa",
  },
  cancelado: {
    icon: "fas fa-times-circle",
    color: "#dc2626",
    label: "Cancelado",
  },
  finalizado: {
    icon: "fas fa-check-circle",
    color: "#079637",
    label: "Finalizado",
  },
};

const current = computed(() => statusMap[props.status] ?? statusMap.finalizado);

const styleVars = computed(() => ({
  "--size": `${props.size}px`,
  "--status-color": current.value.color,
}));

const iconClass = computed(() => current.value.icon);
const label = computed(() => current.value.label);
</script>

<style scoped>
.status-badge {
  width: var(--size);
  height: var(--size);
  border-radius: 50%;
  display: grid;
  place-items: center;
  cursor: pointer;
  background: var(--status-color);
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25), 0 0 14px rgba(0, 0, 0, 0.18),
    inset 0 0 6px rgba(255, 255, 255, 0.35);
  transition: all 0.25s ease;
  animation: pulse 1.2s infinite;
  z-index: 9999;
  position: fixed;
  top: 16px;
  left: 50%;
}

@keyframes pulse {
  0% {
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.25), 0 0 14px rgba(0, 0, 0, 0.18),
      inset 0 0 6px rgba(255, 255, 255, 0.35), 0 0 0 0 rgba(7, 150, 55, 0.5);
  }
  70% {
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.25), 0 0 14px rgba(0, 0, 0, 0.18),
      inset 0 0 6px rgba(255, 255, 255, 0.35), 0 0 0 12px rgba(7, 150, 55, 0);
  }
  100% {
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.25), 0 0 14px rgba(0, 0, 0, 0.18),
      inset 0 0 6px rgba(255, 255, 255, 0.35), 0 0 0 0 rgba(7, 150, 55, 0);
  }
}

.status-badge i {
  font-size: calc(var(--size) * 0.6);
  color: #fff;
}

.status-badge:hover {
  transform: scale(1.12);
}
</style>
