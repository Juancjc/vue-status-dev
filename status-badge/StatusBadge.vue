<template>
  <div class="status-wrapper" :style="styleVars" :title="label">
    <span class="status-badge">
      <i :class="iconClass" aria-hidden="true"></i>
    </span>
    <p class="status-label-mobile">{{ label }}</p>
  </div>
</template>

<script setup>
import { computed } from "vue";
import "@fortawesome/fontawesome-free/css/all.min.css";

const props = defineProps({
  status: { type: String, default: "finalizado" },
  size: { type: Number, default: 44 },
  position: { type: String, default: "middle-top" }, // left-top, middle-top, right-top
});

const statusMap = {
  desenvolvimento: {
    icon: "fas fa-laptop-code",
    color: "#dc3333",
    label: "Em Desenvolvimento",
  },
  finalizando: { icon: "fas fa-tools", color: "#F59E0B", label: "Finalizando" },
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

const positionStyles = {
  "left-top": {
    top: "16px",
    left: "16px",
    right: "auto",
    bottom: "auto",
    transform: "none",
  },
  "middle-top": {
    top: "16px",
    left: "50%",
    right: "auto",
    bottom: "auto",
    transform: "translateX(-50%)",
  },
  "right-top": {
    top: "16px",
    left: "auto",
    right: "16px",
    bottom: "auto",
    transform: "none",
  },
  "left-center": {
    top: "50%",
    left: "16px",
    right: "auto",
    bottom: "auto",
    transform: "translateY(-50%)",
  },
  "middle-center": {
    top: "50%",
    left: "50%",
    right: "auto",
    bottom: "auto",
    transform: "translate(-50%, -50%)",
  },
  "right-center": {
    top: "50%",
    left: "auto",
    right: "16px",
    bottom: "auto",
    transform: "translateY(-50%)",
  },
  "left-bottom": {
    top: "auto",
    left: "16px",
    right: "auto",
    bottom: "16px",
    transform: "none",
  },
  "middle-bottom": {
    top: "auto",
    left: "50%",
    right: "auto",
    bottom: "16px",
    transform: "translateX(-50%)",
  },
  "right-bottom": {
    top: "auto",
    left: "auto",
    right: "16px",
    bottom: "16px",
    transform: "none",
  },
};

const styleVars = computed(() => {
  const base = {
    "--size": `${props.size}px`,
    "--status-color": current.value.color,
  };
  const pos = positionStyles[props.position] || positionStyles["middle-top"];
  return { ...base, ...pos };
});

const iconClass = computed(() => current.value.icon);
const label = computed(() => current.value.label);
</script>

<style scoped>
/* Wrapper prende os dois (badge + label) e centraliza */
.status-wrapper {
  position: fixed;
  /* top, left, right, transform agora são dinâmicos via styleVars */
  display: grid;
  justify-items: center;
  gap: 6px; /* espaço entre badge e label */
  z-index: 9999;
}

/* Badge */
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
  transition: transform 0.25s ease;
  animation: pulse 1.2s infinite;
}

.status-badge i {
  font-size: calc(var(--size) * 0.6);
  color: #fff;
}

.status-badge:hover {
  transform: scale(1.12);
}

/* Label: escondido por padrão (desktop), aparece só no mobile */
.status-label-mobile {
  display: none;
  background-color: aliceblue;
  border-radius: 12px;
  text-align: center;
  padding: 1px 8px;
  font-size: 0.75rem;
  color: #333;
  font-weight: 400;
  line-height: 1;
  white-space: nowrap;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

/* Mostra no mobile */
@media (max-width: 768px) {
  .status-label-mobile {
    display: inline-block;
  }
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
</style>
