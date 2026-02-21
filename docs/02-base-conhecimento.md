# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização da Ana-AFP |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores e identificar interesses financeiros do cliente |
| `perfil_investidor.json` | JSON | Personalizar explicações e adaptar a comunicação ao perfil financeiro |
| `produtos_financeiros.json` | JSON | Sugerir "soluções" adequados ao perfil financeiro  e objetivos do cliente visando uma melhor UX e CX |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente , fluxo de caixa e identificar possíveis riscos de inadimplência |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

## Adaptações nos Dados

Os dados mockados fornecidos foram utilizados com pequenas adaptações para facilitar a simulação do comportamento financeiro do cliente no protótipo da Ana - AFP.

As principais adequações realizadas foram:

- Organização das categorias de transações para permitir análise de gastos
- Uso do histórico financeiro para cálculo de saldo estimado
- Utilização do perfil do investidor para personalização das respostas do agente
- Associação dos produtos financeiros ao perfil do cliente para recomendações coerentes

Não houve alteração estrutural significativa nos arquivos originais, sendo utilizados principalmente para fins de simulação e demonstração do funcionamento do agente.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Os arquivos CSV e JSON serão carregados no início da execução da aplicação utilizando Python.

Bibliotecas utilizadas:

Pandas para leitura e manipulação de dados CSV

Json para leitura dos arquivos estruturados

Após o carregamento, os dados são armazenados em memória e utilizados tanto para cálculos determinísticos quanto para contextualização das respostas do modelo de linguagem.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Os dados não são inseridos diretamente no prompt completo para evitar excesso de informações.

A estratégia adotada é híbrida com processamento determinístico em Python visando : 

Cálculo de saldo e identificação de risco financeiro

Resumo de gastos e informações do perfil

Como forma de prevenção o envio será apenas do contexto relevante para o LLM como : 

Nome do cliente

Perfil financeiro

Situação identificada (ex: risco de saldo insuficiente)

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Exemplo de informações enviadas ao agente durante uma interação:

Dados do Cliente:

Nome: João Silva

Idade: 32 anos

Perfil de Investidor: Moderado

Renda Mensal: R$ 5.000

Saldo estimado após despesas: R$ 2.511

Resumo Financeiro:

Total de despesas no mês: R$ 2.489

Principais categorias: Moradia, Alimentação e Transporte

Meta atual: Construção de reserva de emergência

Situação Identificada:

Possível redução de liquidez nas próximas semanas

Necessidade de organização financeira preventiva

Opções Disponíveis:

Parcelamento de compromisso financeiro

Ajuste temporário de orçamento

Avaliar contratos atuais (cartão, cheque especial, empréstimos)

Propor migração para linhas com taxas menores antes de virar inadimplência . Objetivo: reduzir pressão financeira e evitar atraso futuro.

Uso planejado de alternativas como Pix no crédito, antecipação de recebíveis ou limite disponível, com simulação de impacto

Definição de prioridade de pagamentos essenciais.(por prioridade de taxa e juros mensais..etc)

Com base nesse contexto, o agente gera uma resposta personalizada, empática e orientada à solução.

```
