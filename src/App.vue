<script setup>
import StatusBadge from './StatusBadge.vue'
</script>

<template>
  <div style="display:flex; gap:20px;">

    <div class="card" style="width: 180px; height: 120px; position: relative; border:1px solid #ccc;">
      <StatusBadge status="desenvolvimento" />
      <div style="padding:40px;">
        <strong>Máquina A</strong><br>
        Desenvolvendo...
      </div>
    </div>

    <div class="card" style="width: 180px; height: 120px; position: relative; border:1px solid #ccc;">
      <StatusBadge status="finalizando" />
      <div style="padding:40px;">
        <strong>Máquina B</strong><br>
        Finalizando ajustes
      </div>
    </div>

    <div class="card" style="width: 180px; height: 120px; position: relative; border:1px solid #ccc;">
      <StatusBadge status="aguardando_aprovacao" />
       <div style="padding:40px;">
        <strong>Máquina C</strong><br>
        Aguardando aprovação
      </div>
    </div>

    <div class="card" style="width: 180px; height: 120px; position: relative; border:1px solid #ccc;">
      <StatusBadge status="finalizado" />
      <div style="padding:40px;">
        <strong>Máquina D</strong><br>
        Finalizada ✅
      </div>
    </div>

  </div>
</template>
