<script setup>
import { computed } from 'vue'

const props = defineProps({
  status: { type: String, default: 'finalizado' },
  size: { type: Number, default: 44 } // agora é maior
})

const statusMap = {
  desenvolvimento: { emoji: '🧑‍💻', color: '#3B82F6', label: 'Em Desenvolvimento' },
  finalizando: { emoji: '🏗️', color: '#F59E0B', label: 'Finalizando' },
  aguardando_aprovacao: { emoji: '⏳', color: '#9CA3AF', label: 'Aguardando Aprovação' },
  finalizado: { emoji: '✅', color: '#079637', label: 'Finalizado' }
}

const current = computed(() => statusMap[props.status] ?? statusMap.finalizado)

const styleVars = computed(() => ({
  '--size': `${props.size}px`,
  '--status-color': current.value.color
}))

const emoji = computed(() => current.value.emoji)
const label = computed(() => current.value.label)
</script>

<template>
  <span class="status-badge" :style="styleVars" :title="label">
    <span class="emoji">{{ emoji }}</span>
  </span>
</template>

<style scoped>
.status-badge {
  position: absolute;
  top: 8px;
  left: 8px;
  width: var(--size);
  height: var(--size);
  border-radius: 50%;
  display: grid;
  place-items: center;
  cursor: pointer;

  background: var(--status-color);

  /* sombra suave + profundidade */
  box-shadow:
    0 0 8px rgba(0,0,0,.25),
    0 0 14px rgba(0,0,0,.18),
    inset 0 0 6px rgba(255,255,255,.35);

  transition: all .25s ease;
}

.emoji {
  font-size: calc(var(--size) * 0.5);
  line-height: 1;
}

/* Hover com anel verde + brilho sutil */
.status-badge:hover {
  transform: scale(1.12);


}

/* contorno suave estilo “anel de aprovação” */
.status-badge::after {
  content: "";
  position: absolute;
  inset: -4px;
  border-radius: 50%;
  opacity: 0;
  transition: .25s;
}

.status-badge:hover::after {
  box-shadow: 0 0 16px color-mix(in oklab, var(--status-color) 30%, white);
  opacity: 1;
}
</style>
