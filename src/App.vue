<script setup>
import { computed, ref } from "vue";
import StatusBadge from "../status-badge/StatusBadge.vue";

const statusOptions = [
  "desenvolvimento",
  "finalizando",
  "aguardando_aprovacao",
  "em_pausa",
  "cancelado",
  "finalizado",
];

const positionOptions = [
  "left-top",
  "middle-top",
  "right-top",
  "left-center",
  "middle-center",
  "right-center",
  "left-bottom",
  "middle-bottom",
  "right-bottom",
];

const selectedStatus = ref("desenvolvimento");
const selectedPosition = ref("right-top");
const selectedSize = ref(48);

const installSnippet = computed(
  () =>
    `<StatusBadge\n  status="${selectedStatus.value}"\n  :size="${selectedSize.value}"\n  position="${selectedPosition.value}"\n/>`,
);
</script>

<template>
  <main class="playground">
    <section class="controls-card">
      <h1>Playground · vue-status-badge</h1>
      <p>Edite as opções abaixo para testar o componente.</p>

      <div class="controls-grid">
        <label>
          Status
          <select v-model="selectedStatus">
            <option v-for="status in statusOptions" :key="status" :value="status">
              {{ status }}
            </option>
          </select>
        </label>

        <label>
          Posição
          <select v-model="selectedPosition">
            <option
              v-for="position in positionOptions"
              :key="position"
              :value="position"
            >
              {{ position }}
            </option>
          </select>
        </label>

        <label>
          Tamanho ({{ selectedSize }}px)
          <input v-model.number="selectedSize" type="range" min="28" max="88" step="2" />
        </label>
      </div>

      <p class="snippet-title">Snippet para copiar:</p>
      <pre><code>{{ installSnippet }}</code></pre>
    </section>

    <section class="preview-card">
      <p>Pré-visualização</p>
      <div class="preview-area">
        <StatusBadge
          :status="selectedStatus"
          :size="selectedSize"
          :position="selectedPosition"
        />
      </div>
    </section>
  </main>
</template>

<style scoped>
.playground {
  min-height: 100vh;
  display: grid;
  gap: 20px;
  grid-template-columns: minmax(280px, 380px) 1fr;
  padding: 24px;
  background: linear-gradient(160deg, #eef3ff 0%, #f9fafb 100%);
  box-sizing: border-box;
  font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
}

.controls-card,
.preview-card {
  background: #fff;
  border-radius: 16px;
  border: 1px solid #e5e7eb;
  box-shadow: 0 12px 24px rgba(15, 23, 42, 0.08);
  padding: 20px;
}

.controls-grid {
  display: grid;
  gap: 12px;
  margin-top: 16px;
}

label {
  display: grid;
  gap: 6px;
  font-weight: 600;
  color: #111827;
}

select,
input[type="range"] {
  width: 100%;
}

.snippet-title {
  margin: 18px 0 8px;
  font-weight: 600;
}

pre {
  margin: 0;
  padding: 12px;
  border-radius: 12px;
  background: #0f172a;
  color: #e2e8f0;
  overflow: auto;
}

.preview-area {
  position: relative;
  height: min(70vh, 560px);
  border-radius: 14px;
  background: radial-gradient(circle at center, #ffffff 0%, #f3f4f6 100%);
  border: 1px dashed #cbd5e1;
}

@media (max-width: 900px) {
  .playground {
    grid-template-columns: 1fr;
  }
}
</style>
