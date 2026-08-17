<script setup>

// Recebe a lista de produtos
defineProps({
  produtos: Array
})

// Formata o preço para reais
function formatarPreco(valor) {
  return valor.toLocaleString("pt-BR", {
    style: "currency",
    currency: "BRL"
  })
}

// Define o status do produto
function statusProduto(quantidade) {

  // Produto sem estoque
  if (quantidade === 0) {
    return {
      texto: "Esgotado",
      classe: "esgotado"
    }
  }

  // Produto com estoque baixo
  if (quantidade < 5) {
    return {
      texto: "Estoque Baixo",
      classe: "baixo"
    }
  }

  // Produto com estoque disponível
  return {
    texto: "Disponível",
    classe: "disponivel"
  }
}

</script>

<template>

  <section class="lista">

    <h2>
      Produtos cadastrados
    </h2>

    <!-- Permite rolagem horizontal da tabela -->
    <div class="tabela-container">

      <table>

        <thead>

          <tr>

            <th>Produto</th>
            <th>Categoria</th>
            <th>Quantidade</th>
            <th>Preço</th>
            <th>Status</th>

          </tr>

        </thead>

        <tbody>

          <tr
            v-for="produto in produtos"
            :key="produto.id"
          >

            <td>
              {{ produto.nome }}
            </td>

            <td>
              {{ produto.categoria }}
            </td>

            <td>
              {{ produto.quantidade }}
            </td>

            <td>
              {{ formatarPreco(produto.preco) }}
            </td>

            <td>

              <span
                class="status"
                :class="statusProduto(produto.quantidade).classe"
              >
                {{ statusProduto(produto.quantidade).texto }}
              </span>

            </td>

          </tr>

        </tbody>

      </table>

    </div>

  </section>

</template>

<style scoped>

.lista {
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

.tabela-container {
  width: 100%;
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}

table {
  width: 100%;
  min-width: 650px;
  border-collapse: collapse;
}

th {
  text-align: left;
  color: #94A3B8;
  padding: 12px;
  white-space: nowrap;
}

td {
  color: #E2E8F0;
  padding: 12px;
  border-top: 1px solid #334155;
}

.status {
  display: inline-block;
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: bold;
  white-space: nowrap;
}

.disponivel {
  background: #166534;
  color: #DCFCE7;
}

.baixo {
  background: #854D0E;
  color: #FEF3C7;
}

.esgotado {
  background: #991B1B;
  color: #FEE2E2;
}

@media (max-width: 480px) {

  .lista {
    padding: 18px;
  }

  h2 {
    font-size: 20px;
  }

}

</style>