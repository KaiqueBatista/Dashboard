<script setup>

import { ref } from "vue"

// Guarda o texto da pesquisa
const textoBusca = ref("")

// Guarda a categoria selecionada
const categoriaSelecionada = ref("")

// Define os eventos enviados ao App.vue
const emit = defineEmits([
  "buscar",
  "categoria",
  "limpar"
])

// Envia o texto da pesquisa
function pesquisar() {
  emit("buscar", textoBusca.value)
}

// Envia a categoria selecionada
function selecionarCategoria() {
  emit("categoria", categoriaSelecionada.value)
}

// Limpa os filtros
function limpar() {
  textoBusca.value = ""
  categoriaSelecionada.value = ""

  emit("limpar")
}

</script>

<template>

  <section class="filtro">

    <!-- Campo de pesquisa -->
    <input
      v-model="textoBusca"
      placeholder="Pesquisar produto..."
      @input="pesquisar"
    />

    <!-- Lista de categorias -->
    <select
      v-model="categoriaSelecionada"
      @change="selecionarCategoria"
    >

      <option value="">
        Todas as categorias
      </option>

      <option value="Periféricos">
        Periféricos
      </option>

      <option value="Monitores">
        Monitores
      </option>

      <option value="Armazenamento">
        Armazenamento
      </option>

      <option value="Notebook">
        Notebook
      </option>

    </select>

    <!-- Botão de pesquisa -->
    <button @click="pesquisar">
      Buscar
    </button>

    <!-- Botão para limpar -->
    <button @click="limpar">
      Limpar
    </button>

  </section>

</template>

<style scoped>

.filtro {
  display: flex;
  gap: 10px;
  margin: 30px 0;
  width: 100%;
}

input,
select,
button {
  box-sizing: border-box;
}

input,
select {
  padding: 12px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
}

input {
  flex: 1;
  min-width: 0;
}

select {
  min-width: 180px;
}

button {
  padding: 12px 20px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
  white-space: nowrap;
}

button:hover {
  opacity: 0.9;
}

@media (max-width: 768px) {

  .filtro {
    flex-direction: column;
  }

  input,
  select,
  button {
    width: 100%;
  }

  select {
    min-width: 0;
  }

}

</style>