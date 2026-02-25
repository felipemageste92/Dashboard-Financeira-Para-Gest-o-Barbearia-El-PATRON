# Dashboard-Financeira-Para-Gest-o-Barbearia-El-PATRON
Dashboard financeiro desenvolvido no Power BI para análise estratégica da El Patron Barbearia. O projeto consolida KPIs como faturamento, lucro, margem, ticket médio e desempenho por barbeiro, utilizando modelagem de dados e DAX para transformar dados operacionais em insights que apoiam a tomada de decisão.



📊 Dashboard Financeiro – El Patron Barbearia
📌 Visão Geral

Projeto de Business Intelligence desenvolvido no Power BI com foco em análise financeira e operacional da barbearia El Patron.

O objetivo do dashboard é fornecer uma visão estratégica da performance do negócio, permitindo acompanhamento de faturamento, lucro, margem, produtividade por barbeiro, sazonalidade de clientes e eficiência operacional.

🎯 Objetivos do Projeto

✔ Monitorar KPIs financeiros essenciais
✔ Avaliar desempenho individual dos barbeiros
✔ Identificar tendências mensais de serviços e clientes
✔ Analisar margem de lucro e estrutura de custos
✔ Apoiar tomada de decisão baseada em dados

🛠️ Etapas do Desenvolvimento
1️- Coleta e Estruturação dos Dados

Os dados utilizados incluem:

Data do atendimento

Tipo de serviço

Valor do serviço

Custo / Valor do Produto

Dados dos Clientes



Foi realizada organização, tratamento e padronização dos dados para garantir integridade, consistência e confiabilidade analítica.


2️- Modelagem de Dados

Aplicação de boas práticas de modelagem:

Modelo relacional estruturado

Tabela fato de vendas/atendimentos

Tabela dimensão de datas (Calendário)

Relacionamentos 1:N

Uso de DAX para métricas financeiras

Exemplo de medidas criadas:

Faturamento Total = SUM(fVendas_servicos[Faturamento Produto]) + [Soma Faturamento Serviço]
Lucro Total = [Faturamento Total Produto/Serviço] * 0.9 - [Total de Gastos]
Margem de Lucro = DIVIDE([Lucro Total], [Faturamento Total Produto/Serviço], 0)
Ticket Médio = DIVIDE([Faturamento Total Produto/Serviço], [Qtd Serviços], 0)

3️- Construção dos KPIs Estratégicos

📈 Indicadores Principais:

Faturamento Total: R$ 298,17 Mil

Lucro Total: R$ 142,19 Mil

Margem de Lucro: 47,69%

Ticket Médio: R$ 95,05

Total de Gastos: R$ 126,16 Mil

Esses indicadores permitem avaliar sustentabilidade financeira, rentabilidade e eficiência operacional.

4️- Análises Desenvolvidas
📅 Quantidade de Serviços e Clientes por Mês

A análise temporal revelou comportamento sazonal relevante no volume de atendimentos.

Em outubro de 2025 houve uma retração no número de clientes.

Já em novembro de 2025 ocorreu recuperação consistente do fluxo.

A barbearia saiu de 176 clientes mensais e atingiu um pico de 575 atendimentos, mantendo estabilidade nos meses seguintes.

Em fevereiro de 2026 ocorreu nova queda, reduzindo o volume para 285 clientes.

Insight estratégico:

✔ Existe padrão claro de sazonalidade.
✔ O negócio demonstra forte capacidade de crescimento (176 → 575 clientes).
✔ Períodos de retração exigem ações estratégicas (campanhas, fidelização, promoções).
✔ Monitoramento mensal via BI permite antecipar movimentos de queda.

💈 Faturamento por Barbeiro

Felipe Mageste – R$ 131,91 Mil

Thiago Augusto – R$ 89,34 Mil

Guilherme Ramos – R$ 76,92 Mil

Insight:

✔ Concentração de receita em um profissional.
✔ Oportunidade de balanceamento de agenda.
✔ Possibilidade de replicar estratégias comerciais do barbeiro com maior performance.

📊 % de Atendimento por Barbeiro

Insight:

✔ Distribuição desigual de atendimentos.
✔ Impacto potencial em produtividade e motivação.
✔ Necessidade de otimização na gestão de agenda.

🏆 Produto Carro-Chefe

O serviço de Corte é o mais rentável.

Insight:

✔ Possibilidade de criação de combos estratégicos.
✔ Estratégias de upsell com serviços complementares.
✔ Potencial aumento de margem média por cliente.

5️- Filtros e Interatividade

Segmentação por período (data inicial e final)

Análise dinâmica conforme intervalo selecionado

Experiência visual moderna com foco em clareza e contraste

Tooltips com métricas percentuais e comparativos

📊 Principais Insights Estratégicos

✔ Margem de lucro saudável (47,69%)
✔ Alta dependência de um único barbeiro
✔ Forte crescimento histórico de clientes
✔ Comportamento sazonal identificado
✔ Queda pontual em fevereiro de 2026
✔ Ticket médio consistente
✔ Estrutura de custos controlada

🚀 Possíveis Melhorias Futuras

Implementação de análise preditiva

Dashboard de metas mensais

Análise de retenção de clientes

Indicador de taxa de retorno

Comparativo Year over Year (YoY)

Clusterização de clientes por comportamento

💡 Tecnologias Utilizadas

Power BI

DAX

Modelagem Relacional

Análise Exploratória de Dados

 Sobre o Projeto

Este dashboard foi desenvolvido como projeto real aplicado à gestão da barbearia, com foco em transformar dados operacionais em informação estratégica para tomada de decisão.

