# Dashboard de Estoque

Um dashboard simples para acompanhar produtos e informações de estoque de forma visual e organizada.

O projeto foi desenvolvido como uma forma de praticar Vue.js, JavaScript, componentização e criação de interfaces responsivas.

## Sobre o projeto

O dashboard mostra algumas informações importantes do estoque, como quantidade de produtos, produtos com estoque baixo, produtos esgotados e o valor total armazenado.

Também é possível pesquisar produtos pelo nome e filtrar os resultados por categoria.

## Funcionalidades

- Visualização do total de produtos
- Identificação de produtos com estoque baixo
- Identificação de produtos esgotados
- Cálculo do valor total do estoque
- Pesquisa de produtos pelo nome
- Filtro por categoria
- Limpeza dos filtros
- Lista de produtos cadastrados
- Status de cada produto
- Indicador visual do nível de estoque
- Quantidade de produtos por categoria
- Valores formatados em Real brasileiro
- Layout adaptado para celular, tablet e computador

## Tecnologias

- Vue.js
- TypeScript
- JavaScript
- HTML5
- CSS3
- Vite

## Como funciona

Cada produto possui algumas informações básicas:

- Nome
- Categoria
- Quantidade em estoque
- Preço

Com esses dados, o dashboard calcula automaticamente os indicadores apresentados na tela.

O status do produto é definido de acordo com a quantidade disponível:

- **Disponível:** 5 ou mais unidades
- **Estoque Baixo:** menos de 5 unidades
- **Esgotado:** 0 unidades

## Categorias

Atualmente o projeto possui as seguintes categorias:

- Periféricos
- Monitores
- Armazenamento
- Notebook

## Estrutura do projeto

```text
dashboard/
├── public/
│   └── favicon.svg
│
├── src/
│   ├── components/
│   │   ├── FiltroProdutos.vue
│   │   ├── GraficoCategorias.vue
│   │   ├── GraficoEstoque.vue
│   │   ├── HeaderDashboard.vue
│   │   ├── ResumoCard.vue
│   │   └── TabelaProdutos.vue
│   │
│   ├── data/
│   │   └── produtos.js
│   │
│   ├── App.vue
│   ├── main.ts
│   └── style.css
│
├── index.html
├── package.json
├── tsconfig.json
└── vite.config.ts