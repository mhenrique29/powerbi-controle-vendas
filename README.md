# Relatório de Vendas — Power BI

Relatório comercial que acompanha faturamento contra meta, compara anos, separa o que foi faturado do que foi cancelado e mostra o desempenho por vendedor e por forma de pagamento.

**Projeto de estudo com dados fictícios.** Nenhuma informação real de empresa ou de pessoa física.

## O problema

Faturamento total sozinho engana. Um mês pode fechar bem e ainda assim esconder um vendedor com taxa alta de cancelamento, uma forma de pagamento que concentra risco, ou um crescimento que só existe porque o ano anterior foi ruim. Este relatório foi montado para que essas três coisas apareçam na mesma tela do número principal.

## Páginas

| Página | O que responde |
|---|---|
| CAPA | Tela de abertura com botão de entrada no relatório |
| RELATÓRIO DE VENDAS | Faturamento por ano, faturado x cancelado por vendedor, faturamento por forma de pagamento, comparação 2017 x 2018, crescimento percentual e acompanhamento das metas de 2017, 2018 e 2019 |

## Modelo de dados

| Tabela | Papel no modelo |
|---|---|
| CONSOLIDADA | Fato: vendas, com data, vendedor, nota fiscal, forma de pagamento e recebimento |
| CALENDARIO | Dimensão de data dedicada, relacionada à tabela fato |
| MEDIDAS | Tabela criada apenas para agrupar as medidas DAX |

A tabela CALENDARIO é o ponto do modelo que vale explicar: em vez de depender da hierarquia automática de datas do Power BI, o relatório tem uma dimensão de calendário própria ligada à tabela fato. É o que permite comparar anos de forma confiável e o que evita o inchamento do modelo com tabelas de data ocultas.

## Medidas DAX

| Medida | Para que serve |
|---|---|
| FATURAMENTO | Receita faturada no período |
| CANCELADO | Valor cancelado, usado no comparativo por vendedor |
| FAT 2017, FAT 2018, FAT 2019 | Faturamento fixado por ano, para comparação lado a lado |
| META 2018, META 2019 | Metas usadas nos velocimetros |
| CRESCIMENTO % | Variação percentual entre os períodos |
| 2017 X 2018 | Diferença direta entre os dois anos |
| MAXIMO, MINIMO | Limites dos velocimetros de meta |
| TEXTO TOOGLE | Texto dinâmico que acompanha o botão de alternar visual |

## Recursos usados

Três velocimetros comparando faturamento contra meta por ano. Gráfico combinado de linha e coluna para faturamento e crescimento na mesma escala. Barras 100 por cento empilhadas para a proporção entre faturado e cancelado. Visual customizado de botão de alternar, que troca a visualização entre valor absoluto e percentual sem sair da página. Navegação por botões a partir da capa.

## Como abrir

Baixe o arquivo Controle_Vendas.pbix e abra no Power BI Desktop. O modelo já vem com os dados importados, não é preciso configurar nenhuma conexão.

## Stack

Power BI Desktop, Power Query (M), DAX, modelagem com dimensão de data.
