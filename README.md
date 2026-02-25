# Dsahboard-Financeira-Para-Gest-o-Barbearia-El-PATRON
Dashboard financeiro desenvolvido no Power BI para análise estratégica da El Patron Barbearia. O projeto consolida KPIs como faturamento, lucro, margem, ticket médio e desempenho por barbeiro, utilizando modelagem de dados e DAX para transformar dados operacionais em insights que apoiam a tomada de decisão.



 📊 Dashboard Financeiro – El Patron Barbearia

 📌 Visão Geral

Projeto de Business Intelligence desenvolvido no Power BI com foco em análise financeira e operacional da barbearia **El Patron**.

O objetivo do dashboard é fornecer uma visão estratégica da performance do negócio, permitindo acompanhamento de faturamento, lucro, margem, produtividade por barbeiro e eficiência operacional.



 🎯 Objetivos do Projeto

 Monitorar KPIs financeiros essenciais
 Avaliar desempenho individual dos barbeiros
 Identificar tendências mensais de serviços
 Analisar margem de lucro e estrutura de custos
 Apoiar tomada de decisão baseada em dados



 🛠️ Etapas do Desenvolvimento

 1️- Coleta e Estruturação dos Dados

Os dados utilizados incluem:

 Data do atendimento
 Tipo de serviço
 Valor do serviço
 Barbeiro responsável
 Custos operacionais
 Forma de pagamento

Foi realizada organização e padronização dos dados para garantir integridade e consistência.


 2️- Modelagem de Dados

Aplicação de boas práticas de modelagem:

* Modelo relacional estruturado
* Tabela fato de vendas/atendimentos
* Tabela dimensão de datas (Calendário)
* Relacionamentos 1:N
* Uso de DAX para métricas financeiras

Exemplo de medidas criadas:

```DAX
Faturamento Total = SUM(fVendas_servicos[Faturamento Produto]) + [Soma Faturamento Serviço]
Lucro Total = [Faturamento Total Produto/Serviço] * 0.9 - [Total de Gastos]
Margem de Lucro = DIVIDE([Lucro Total], [Faturamento Total Produto/Serviço], 0)
Ticket Médio = DIVIDE([Faturamento Total Produto/Serviço], [Qtd Serviços], 0)
```



 3️- Construção dos KPIs Estratégicos

 📈 Indicadores Principais:

Faturamento Total:** R$ 298,17 Mil
Lucro Total:** R$ 142,19 Mil
Margem de Lucro:** 47,69%
Ticket Médio:** R$ 95,05
Total de Gastos:** R$ 126,16 Mil

Esses indicadores permitem avaliar sustentabilidade financeira e eficiência operacional.



 4️- Análises Desenvolvidas

 📅 Quantidade de Serviços por Mês

Insight:

Houve queda significativa nos últimos meses.
Pode indicar sazonalidade ou redução na demanda.
Necessário investigar campanhas de marketing ou retenção.



💈 Faturamento por Barbeiro

Felipe Mageste – R$ 131,91 Mil
Thiago Augusto – R$ 89,34 Mil
Guilherme Ramos – R$ 76,92 Mil

Insight:

 Existe concentração de receita em um profissional.
 Oportunidade de equilibrar agenda ou replicar estratégias de venda.



 📊 % de Atendimento por Barbeiro

Insight:

 Distribuição desigual de atendimentos.
 Pode impactar motivação e produtividade da equipe.
 Avaliar redistribuição de agenda.



 🏆 Produto Carro-Chefe

Corte é o serviço mais rentável.

Insight:

 Estratégia pode focar em combos ou upsell com esse serviço.
 Possibilidade de aumentar margem com serviços complementares.



 5️- Filtros e Interatividade

 Segmentação por período (Data inicial e final)
 Análise dinâmica conforme intervalo selecionado
 Experiência visual moderna com foco em clareza e contraste



 📊 Principais Insights Estratégicos

✔ Margem de lucro saudável (47,69%)
✔ Alta dependência de um único barbeiro para maior faturamento
✔ Queda recente no volume de serviços
✔ Ticket médio consistente
✔ Estrutura de custos controlada



 🚀 Possíveis Melhorias Futuras

 Implementação de análise preditiva
 Dashboard de metas mensais
 Análise de retenção de clientes
 Indicador de taxa de retorno
 Comparativo ano contra ano (YoY)



 💡 Tecnologias Utilizadas

 Power BI
 DAX
 Modelagem Relacional
 Análise Exploratória de Dados



 Sobre o Projeto

Este dashboard foi desenvolvido como projeto real aplicado à gestão da barbearia, com foco em transformar dados operacionais em informação estratégica para tomada de decisão.

