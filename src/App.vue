<script setup>

import { ref, computed } from "vue"
import HeaderDashboard from "./components/HeaderDashboard.vue"
import ResumoCard from "./components/ResumoCard.vue"
import TabelaProdutos from "./components/TabelaProdutos.vue"
import FiltroProdutos from "./components/FiltroProdutos.vue"
import GraficoCategorias from "./components/GraficoCategorias.vue"
import GraficoEstoque from "./components/GraficoEstoque.vue"
import { produtosIniciais } from "./data/produtos.js"

// Guarda a lista de produtos
const produtos = ref(produtosIniciais)

// Conta o total de produtos
const totalProdutos = computed(() => {
  return produtos.value.length
})

// Conta os produtos com estoque baixo
const estoqueBaixo = computed(() => {
  return produtos.value.filter(
    produto => produto.quantidade < 5
  ).length
})

// Conta os produtos esgotados
const produtosEsgotados = computed(() => {
  return produtos.value.filter(
    produto => produto.quantidade === 0
  ).length
})

// Calcula o valor total do estoque
const valorTotalEstoque = computed(() => {
  return produtos.value.reduce((total, produto) => {
    return total + (
      produto.quantidade * produto.preco
    )
  }, 0)
})

// Guarda o texto da pesquisa
const busca = ref("")

// Guarda a categoria selecionada
const categoria = ref("")

// Filtra os produtos pela pesquisa e categoria
const produtosFiltrados = computed(() => {

  return produtos.value.filter(produto => {

    const nomeCombina = produto.nome
      .toLowerCase()
      .includes(busca.value.toLowerCase())

    const categoriaCombina =
      categoria.value === "" ||
      produto.categoria === categoria.value

    return nomeCombina && categoriaCombina

  })

})

// Limpa os filtros
function limparFiltros() {
  busca.value = ""
  categoria.value = ""
}

</script>

<template>

  <main class="container">

    <HeaderDashboard />

    <!-- Cards com os principais indicadores -->
    <section class="cards">

      <ResumoCard
        titulo="Produtos"
        :valor="totalProdutos"
        icone="📦"
      />

      <ResumoCard
        titulo="Estoque Baixo"
        :valor="estoqueBaixo"
        icone="⚠️"
      />

      <ResumoCard
        titulo="Esgotados"
        :valor="produtosEsgotados"
        icone="❌"
      />

      <ResumoCard
        titulo="Valor Total"
        :valor="valorTotalEstoque.toLocaleString('pt-BR', {
          style: 'currency',
          currency: 'BRL'
        })"
        icone="💰"
      />

    </section>

    <GraficoCategorias
      :produtos="produtos"
    />

    <GraficoEstoque
      :produtos="produtos"
    />

    <FiltroProdutos
      @buscar="busca = $event"
      @categoria="categoria = $event"
      @limpar="limparFiltros"
    />

    <TabelaProdutos
      :produtos="produtosFiltrados"
    />

  </main>

</template>

<style scoped>

.container {
  box-sizing: border-box;
  background: #0F172A;
  min-height: 100vh;
  width: 100%;
  padding: 40px;
  overflow-x: hidden;
}

.cards {
  display: grid;
  grid-template-columns: repeat(
    auto-fit,
    minmax(220px, 1fr)
  );
  gap: 20px;
}

@media (max-width: 768px) {

  .container {
    padding: 20px;
  }

  .cards {
    grid-template-columns: repeat(
      2,
      minmax(0, 1fr)
    );
    gap: 15px;
  }

}

@media (max-width: 480px) {

  .container {
    padding: 15px;
  }

  .cards {
    grid-template-columns: 1fr;
    gap: 15px;
  }

}

</style>