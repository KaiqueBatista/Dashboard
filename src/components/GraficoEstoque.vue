<script setup>

// Recebe a lista de produtos
defineProps({
  produtos: Array
})

// Calcula a largura da barra
function largura(quantidade) {
  return Math.min(quantidade * 4, 100) + "%"
}

</script>

<template>

  <section class="grafico">

    <h2>
      Nível de estoque
    </h2>

    <div
      v-for="produto in produtos"
      :key="produto.id"
      class="produto"
    >

      <div class="informacao">

        <span class="nome-produto">
          {{ produto.nome }}
        </span>

        <strong>
          {{ produto.quantidade }} unidades
        </strong>

      </div>

      <!-- Barra visual do estoque -->
      <div class="barra">

        <div
          class="progresso"
          :style="{ width: largura(produto.quantidade) }"
        >
        </div>

      </div>

    </div>

  </section>

</template>

<style scoped>

.grafico {
  background: #1E293B;
  padding: 25px;
  border-radius: 12px;
  margin-top: 30px;
  min-width: 0;
}

h2 {
  color: white;
  margin-bottom: 20px;
}

.produto {
  margin-bottom: 20px;
}

.informacao {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 15px;
  color: #E2E8F0;
  margin-bottom: 8px;
}

.nome-produto {
  min-width: 0;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.informacao strong {
  flex-shrink: 0;
  white-space: nowrap;
}

.barra {
  width: 100%;
  height: 12px;
  background: #334155;
  border-radius: 10px;
  overflow: hidden;
}

.progresso {
  height: 100%;
  background: #3B82F6;
  border-radius: 10px;
  transition: width 0.3s ease;
}

@media (max-width: 480px) {

  .grafico {
    padding: 18px;
  }

  h2 {
    font-size: 20px;
  }

  .informacao {
    flex-direction: column;
    align-items: flex-start;
    gap: 5px;
  }

  .nome-produto {
    width: 100%;
    white-space: normal;
    overflow: visible;
    text-overflow: unset;
  }

}

</style>