# Relatório Criativo — Sales & Profit | Financial Sample

Desafio de projeto do módulo de Power BI da [DIO](https://www.dio.me/). A proposta ia além
de montar visuais: o foco era **estrutura de layout, navegação por botões e alternância de
visuais por indicadores** — construir um relatório que se opera, não apenas se lê.

O arquivo `.pbix` neste repositório contém o relatório completo, com as duas páginas.

---

## A base de dados

`Financial Sample.xlsx` — amostra financeira da Microsoft.

| | |
|---|---|
| Linhas | 700 |
| Período | setembro/2013 a dezembro/2014 |
| Países | 5 (Canadá, França, Alemanha, México, EUA) |
| Segmentos | 5 (Government, Small Business, Channel Partners, Midmarket, Enterprise) |
| Produtos | 6 |

A coluna de vendas do arquivo original se chama `" Sales"`, **com um espaço no início do nome**.
Por isso ela aparece no topo da lista de campos do Power BI, fora da ordem alfabética.

---

## Página 1 — Sales Report

Visão de vendas, com trilha lateral de navegação, faixa de topo e cinco indicadores no cabeçalho.

| Elemento | Campos |
|---|---|
| Cartões (5) | Soma de ` Sales` · `Units Sold` · `Discounts` · `Profit` · `COGS` |
| Gráfico de área | Eixo: `Date › Mês` · Valor: Soma de ` Sales` |
| Rosca / Barras *(alterna)* | `Segment` × Soma de ` Sales` |
| Barras | `Product` × Soma de ` Sales` |
| Treemap / Mapa *(alterna)* | `Country` × Soma de ` Sales` |
| Segmentação de data | `Date`, estilo Entre |
| Botão borracha | Aplica o indicador que limpa os filtros |

## Página 2 — Report de Lucro Detalhado

Visão de lucratividade, construída de forma autoral.

| Visual | Campos |
|---|---|
| Segmentação de botões | `Date › Ano` |
| Árvore hierárquica | Analisar: Soma de `Profit` · Explicar por: `Ano`, `Country` |
| Barras — Lucro por produto | `Product` × Soma de `Profit` |
| Treemap — Lucro por segmento | `Segment` × Soma de `Profit` |
| Cascata — Construção do lucro | `Date › Trimestre` × Soma de `Profit` |

---

## O mecanismo de interação

O relatório usa **cinco indicadores** e **seis botões**.

### Alternância de visuais

Dois pares de visuais ocupam exatamente a mesma posição na página 1, e um par de botões
mostra um e esconde o outro:

| Botão | Indicador | Efeito |
|---|---|---|
| Bar Chart | `Gráfico Barra` | Mostra as barras de Segment, esconde a rosca |
| Pie Chart | `Gráfico Pie` | Mostra a rosca, esconde as barras |
| Treemap | `Gráfico Treemap` | Mostra o treemap de Country, esconde o mapa |
| Map Chart | `Gráfico Map` | Mostra o mapa, esconde o treemap |

Os quatro foram criados com a opção **"Dados" desmarcada**. Esse detalhe é o que impede o
indicador de guardar também o estado dos filtros: sem ele, o usuário que escolhesse um período
na segmentação de data veria a data voltar sozinha ao trocar de visual — um defeito silencioso,
que só aparece quando alguém usa o relatório de verdade.

### Limpar filtros

O botão de borracha aplica o indicador `Limpar Filtros`, este sim criado **com "Dados" marcado**,
já que o objetivo é justamente restaurar o estado dos filtros.

### Navegação

Setas no pé da trilha lateral levam da página 1 para a 2 e de volta, por ação de Navegação de Página.

---

## Duas decisões próprias

**Corrigi um erro do relatório de referência.** No material original, o terceiro e o quarto
cartão do cabeçalho exibiam o mesmo campo — `Soma de Discounts`, ambos com 9,21 Mi. Substituí
o quarto por **Soma de Profit** (16,89 Mi), que completa a leitura do topo: vendas, unidades,
descontos, lucro e custo.

**Substituí dois visuais de terceiros por equivalentes nativos.** A referência usava Radar Chart
e Chiclet Slicer, ambos do AppSource. Visuais de terceiros não ficam embutidos no arquivo: quem
abre o relatório sem tê-los instalados vê caixas vazias pedindo que os importe. Troquei o radar
por um **gráfico de barras** e o chiclet por uma **segmentação de botões** nativa.

A troca do radar também melhora a leitura. Comparar seis produtos pela área de um polígono é
mais difícil que comparar seis barras alinhadas num eixo comum.

---

## Números de conferência

| Indicador | Valor |
|---|---|
| Sales | US$ 118.726.350,26 |
| Units Sold | 1.125.806 |
| Discounts | US$ 9.205.248,24 |
| Profit | US$ 16.893.702,26 |
| COGS | US$ 101.832.648,00 |

**Vendas por segmento** — Government 52,50 mi (44,22%) · Small Business 42,43 mi (35,74%) ·
Enterprise 19,61 mi (16,52%) · Midmarket 2,38 mi (2,01%) · Channel Partners 1,80 mi (1,52%)

**Lucro por ano** — 2013: US$ 3.878.464,51 · 2014: US$ 13.015.237,75

**Lucro por trimestre** — T1 2.632.442,94 · T2 3.232.378,45 · T3 3.501.667,37 · T4 7.527.213,50

**Lucro por produto** — Paseo 4.797.437,95 · VTT 3.034.608,02 · Amarilla 2.814.104,06 ·
Velo 2.305.992,46 · Montana 2.114.754,88 · Carretera 1.826.804,88

---

## Como abrir

Baixe o `.pbix` e abra no [Power BI Desktop](https://powerbi.microsoft.com/desktop/). O modelo
de dados já vem carregado e todos os visuais são nativos — não é necessário instalar nada.

Para testar a alternância dentro do Power BI Desktop, use **Ctrl + clique** nos botões;
clique simples apenas seleciona o objeto.

## Tecnologias

Power BI Desktop · Power Query · Microsoft Excel

## Referência

Material original do curso: [julianazanelatto/power_bi_analyst](https://github.com/julianazanelatto/power_bi_analyst)

## Autor

Diogo Basílio — Bootcamp Power BI + IA · DIO
