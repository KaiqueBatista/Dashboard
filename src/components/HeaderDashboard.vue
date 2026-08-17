<template>

  <header class="header">

    <!-- Título principal do dashboard -->
    <h1>
      📦 Dashboard de Estoque
    </h1>

    <!-- Descrição do dashboard -->
    <p>
      Controle de produtos e indicadores em tempo real
    </p>

  </header>

</template>

<style scoped>

.header {
  background: #1E293B;
  color: #F8FAFC;
  padding: 24px;
  margin-bottom: 30px;
  border-radius: 12px;
  text-align: center;
}

.header h1 {
  font-size: 2rem;
  margin-bottom: 8px;
}

.header p {
  color: #CBD5E1;
  font-size: 1rem;
}

@media (max-width: 480px) {

  .header {
    padding: 20px 15px;
  }

  .header h1 {
    font-size: 1.5rem;
  }

  .header p {
    font-size: 0.9rem;
    line-height: 1.5;
  }

}

</style>