<script setup>

// Define as propriedades recebidas pelo componente
defineProps({

  // Título exibido no card
  titulo: String,

  // Valor exibido no card
  valor: [String, Number],

  // Ícone exibido no card
  icone: String

})

</script>

<template>

  <div class="card">

    <!-- Exibe o ícone do indicador -->
    <div class="icone">
      {{ icone }}
    </div>

    <!-- Exibe as informações do indicador -->
    <div class="informacoes">

      <h3>
        {{ titulo }}
      </h3>

      <h2>
        {{ valor }}
      </h2>

    </div>

  </div>

</template>

<style scoped>

.card {
  background: #1E293B;
  border-radius: 12px;
  padding: 20px;
  display: flex;
  align-items: center;
  gap: 18px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
  transition: 0.3s;
  min-width: 0;
}

.card:hover {
  transform: translateY(-6px);
}

.icone {
  font-size: 40px;
  flex-shrink: 0;
}

.informacoes {
  min-width: 0;
}

.informacoes h3 {
  margin: 0;
  color: #CBD5E1;
  font-size: 16px;
}

.informacoes h2 {
  margin-top: 6px;
  color: #FFFFFF;
  font-size: clamp(18px, 2vw, 30px);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

@media (max-width: 480px) {

  .card {
    padding: 18px;
    gap: 14px;
  }

  .icone {
    font-size: 34px;
  }

  .informacoes h3 {
    font-size: 14px;
  }

}

</style>