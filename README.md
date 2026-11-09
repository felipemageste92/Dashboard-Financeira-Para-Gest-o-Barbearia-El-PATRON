# Dashboard Financeiro — El Patron Barbearia

Dashboard desenvolvido no Power BI para acompanhar faturamento, gastos, resultado gerencial, ticket médio e desempenho por barbeiro.

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge)

## Base analisada

Valores conferidos no modelo aberto do Power BI, considerando toda a base, sem filtros comerciais ou de período.

- **Período com vendas:** 20/08/2025 a 16/02/2026.
- **Vendas distintas:** 4.058.
- **Atendimentos com serviço:** 2.857.
- **Unidades de serviços:** 3.137.
- **Unidades de produtos vendidas:** 2.396.
- **Clientes distintos com serviço:** 110.

Uma venda com serviço representa um atendimento. Um atendimento pode conter mais de uma unidade de serviço. Compras somente de produtos entram nas vendas, mas não nos atendimentos. Clientes distintos, atendimentos e serviços são contagens diferentes.

## Indicadores financeiros

| Indicador | Valor na base completa |
|---|---:|
| Faturamento de produtos e serviços | R$ 298.172,00 |
| Gastos fixos cadastrados | R$ 32.754,00 |
| Comissão dos barbeiros | R$ 98.465,00 |
| Custo dos produtos vendidos | R$ 34.116,00 |
| Total de gastos, comissões e custo dos produtos | R$ 165.335,00 |
| Lucro Total — resultado gerencial | R$ 132.837,00 |
| Margem de Lucro | 44,55% |
| Ticket Médio Geral — por venda | R$ 73,48 |
| Ticket Médio Serviço — por atendimento | R$ 68,93 |

O resultado gerencial desconta os gastos fixos registrados, a comissão e o custo dos produtos vendidos. Não inclui estimativa de impostos não cadastrados. A comissão preserva a regra do modelo: **50% do faturamento de serviços**.

### Custo dos produtos vendidos

Calculado pela quantidade vendida multiplicada pelo custo unitário de `dProdutos[Custo]`. Representa o custo dos itens vendidos, não um registro de pagamento de compras de estoque.

| Produto | Custo unitário | Quantidade vendida | Custo total |
|---|---:|---:|---:|
| Minoxidil 15% | R$ 11,00 | 453 | R$ 4.983,00 |
| Pomada Matte | R$ 12,00 | 375 | R$ 4.500,00 |
| Pomada Brilho | R$ 12,00 | 409 | R$ 4.908,00 |
| Pomada Teia | R$ 12,00 | 385 | R$ 4.620,00 |
| Balm | R$ 18,00 | 383 | R$ 6.894,00 |
| Pós Barba | R$ 21,00 | 391 | R$ 8.211,00 |
| **Total** | | **2.396** | **R$ 34.116,00** |

Esse custo já compõe `Total de Gastos`; não deve ser somado novamente no cálculo do resultado.

## Desempenho por barbeiro

| Barbeiro | Faturamento de produtos e serviços | Atendimentos | Participação nos atendimentos |
|---|---:|---:|---:|
| Felipe Mageste | R$ 131.906,00 | 1.258 | 44,03% |
| Thiago Augusto | R$ 89.344,00 | 879 | 30,77% |
| Guilherme Ramos | R$ 76.922,00 | 720 | 25,20% |
| **Total** | **R$ 298.172,00** | **2.857** | **100,00%** |

Felipe apresenta o maior faturamento e volume de atendimentos no período. Esses números isoladamente não demonstram diferenças de disponibilidade de agenda, capacidade ou qualidade de atendimento.

## Evolução mensal

| Mês | Faturamento | Atendimentos |
|---|---:|---:|
| Agosto/2025 — a partir do dia 20 | R$ 15.850,00 | 158 |
| Setembro/2025 | R$ 53.929,00 | 521 |
| Outubro/2025 | R$ 50.933,00 | 480 |
| Novembro/2025 | R$ 48.649,00 | 471 |
| Dezembro/2025 | R$ 47.835,00 | 473 |
| Janeiro/2026 | R$ 54.479,00 | 497 |
| Fevereiro/2026 — até o dia 16 | R$ 26.497,00 | 257 |

Agosto e fevereiro têm cobertura parcial. As medidas de comparação equivalente permitem comparar fevereiro até 16/02 com janeiro até 16/01: **R$ 26.497,00 contra R$ 28.342,00**, variação de **−6,51%**.

O histórico permite acompanhar variações mensais, mas não comprova um padrão recorrente de sazonalidade anual.

## Modelagem e organização

- `fVendas_servicos`: registros de vendas, quantidades de produtos e serviços e valores calculados.
- `dClientes`, `dBarbeiros`, `dProdutos` e `dServicos`: dimensões relacionadas às vendas.
- `dCalendario`: calendário diário contínuo, relacionado às vendas e às despesas por data de pagamento.
- `dGastos_fixos_1`: despesas cadastradas.
- `Medidas DAX`: medidas com descrições e organização em pastas por assunto.

O relacionamento direto entre despesas e vendas foi removido. As duas tabelas usam o calendário para filtrar o período, evitando que a seleção de um barbeiro reduza indevidamente os gastos fixos registrados.

As pastas abrangem atendimentos e serviços, faturamento, médias e tickets, evolução no tempo, gastos e lucro, participações, contagens de tipos, equipe, produtividade e clientes.

## Exemplos de medidas DAX

### Vendas e atendimentos

```dax
Qtd Vendas =
CALCULATE(
    DISTINCTCOUNT(fVendas_servicos[id_venda]),
    KEEPFILTERS(NOT ISBLANK(fVendas_servicos[id_venda]))
)

QTD DE ATENDIMENTOS =
CALCULATE(
    [Qtd Vendas],
    KEEPFILTERS(fVendas_servicos[quantidade_servico] > 0)
)
```

### Faturamento e tickets

```dax
Faturamento Total Produto/Serviço =
SUM(fVendas_servicos[Faturamento Produto])
    + [Soma Faturamento Serviço]

Ticket Médio Geral =
DIVIDE(
    [Faturamento Total Produto/Serviço],
    [Qtd Vendas]
)

Receita de Serviços por Atendimento =
DIVIDE(
    [Faturamento Serviços],
    [QTD DE ATENDIMENTOS]
)
```

### Gastos, lucro e margem

```dax
Gasto com Produtos Vendidos =
SUM(fVendas_servicos[Custo Total Produtos]) + 0

Total de Gastos =
[Gastos Fixos]
    + [Comissao Barbeiros]
    + [Custo dos Produtos Vendidos]
    + 0

Lucro Total =
[Faturamento Total Produto/Serviço] - [Total de Gastos] + 0

Margem de Lucro =
DIVIDE(
    [Lucro Total],
    [Faturamento Total Produto/Serviço],
    0
)

Margem de Contribuição =
[Faturamento Total Produto/Serviço]
    - [Comissao Barbeiros]
    - [Custo dos Produtos Vendidos]
```

## Análises adicionais disponíveis no modelo

- Faturamento e atendimentos do mês anterior.
- Comparação com o mesmo trecho do mês anterior, com validação de seleção contínua desde o dia 1.
- Acumulados no mês e no ano, limitados à última venda da base.
- Participação de receita e atendimentos por barbeiro, preservando o período selecionado.
- Ranking de atendimentos, atendimentos por dia ativo e serviços por atendimento.
- Clientes com dois ou mais atendimentos dentro do período selecionado e seu percentual entre clientes com serviço.

Repetição dentro da seleção não equivale à retenção entre meses. A existência dessas medidas não significa que todos os visuais de uma segunda página já tenham sido construídos.

## Limitações de interpretação

- **Sem rateio de gastos fixos:** ao filtrar um barbeiro, `Lucro Total` e `Margem de Lucro` descontam todos os gastos fixos da barbearia no período. Para comparar profissionais antes dessas despesas, usar `Margem de Contribuição` e `% Margem de Contribuição`. Os lucros individuais não devem ser somados como parcelas do lucro geral.
- **Preços e custos de cadastro:** receitas e custos são calculados com os valores cadastrados nas dimensões. Não há preço ou custo histórico por venda nessas fórmulas.
- **Despesas por pagamento:** os gastos seguem a data de pagamento registrada, sem apropriação mensal automática por competência.
- **Períodos parciais:** agosto/2025 e fevereiro/2026 não representam meses completos de vendas.
- **Fontes de dados:** foi identificado um caminho de CSV ausente no ambiente de origem. O calendário foi tornado independente desse arquivo; a disponibilidade das demais fontes para uma atualização completa precisa ser verificada.

## Arquivos do repositório

- [Capa](1%20-%20Capa.png).
- [Imagem do dashboard](2-%20Dashboard.png).

A imagem do dashboard foi atualizada com a captura enviada. O cartão intitulado “Lucro Líquido” na imagem corresponde ao resultado gerencial descrito neste README, sem estimativa de impostos não cadastrados.

![Dashboard financeiro da El Patron Barbearia](2-%20Dashboard.png)

## Tecnologias verificadas

Power BI, Power Query (M), DAX e modelagem relacional.
