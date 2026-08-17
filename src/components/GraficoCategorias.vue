<script setup>

import { computed } from "vue"

// Recebe a lista de produtos
const props = defineProps({
  produtos: Array
})

// Conta os produtos de cada categoria
const categorias = computed(() => {

  const resultado = {}

  // Percorre todos os produtos
  props.produtos.forEach(produto => {

    if (resultado[produto.categoria]) {
      resultado[produto.categoria]++
    } else {
      resultado[produto.categoria] = 1
    }

  })

  return resultado

})

</script>

<template>

  <section class="grafico">

    <h2>
      Produtos por categoria
    </h2>

    <!-- Exibe cada categoria e sua quantidade -->
    <div
      v-for="(quantidade, categoria) in categorias"
      :key="categoria"
      class="linha"
    >

      <span>
        {{ categoria }}
      </span>

      <strong>
        {{ quantidade }}
      </strong>

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

.linha {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 15px;
  background: #334155;
  padding: 12px;
  margin-top: 10px;
  border-radius: 8px;
  color: white;
}

.linha span {
  min-width: 0;
  overflow: hidden;
  text-overflow: ellipsis;
}

.linha strong {
  flex-shrink: 0;
}

@media (max-width: 480px) {

  .grafico {
    padding: 18px;
  }

  h2 {
    font-size: 20px;
  }

  .linha {
    padding: 10px;
  }

}

</style>