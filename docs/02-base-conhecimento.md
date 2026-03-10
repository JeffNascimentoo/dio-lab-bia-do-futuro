# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que serve na Clara? |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores do cliente com o agente, permitindo respostas mais personalizadas. |
| `perfil_investidor.json` | JSON | Identificar características financeiras do cliente e seu perfil de risco para personalizar recomendações |
| `produtos_financeiros.json` | JSON | Disponibilizar produtos financeiros que podem ser sugeridos ao usuário de acordo com seu perfil |
| `transacoes.csv` | CSV | Permitir análise do histórico financeiro do cliente e identificação de padrões de gastos |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Os dados mockados fornecidos no repositório foram utilizados sem alterações estruturais.

Eles representam um conjunto de informações financeiras simuladas que permitem testar o funcionamento do agente sem a necessidade de acessar dados reais de clientes.

A utilização desses dados permite que a Clara AI:

- analise padrões de consumo do cliente;

- compreenda seu perfil financeiro;

- consulte interações anteriores;

- ofereça recomendações financeiras contextualizadas.

Essa abordagem garante segurança no desenvolvimento e evita o uso de informações sensíveis.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Os arquivos da base de conhecimento são carregados no início da execução da aplicação utilizando bibliotecas padrão da linguagem Python.

Os arquivos no formato CSV são carregados utilizando a biblioteca Pandas, enquanto os arquivos no formato JSON são carregados utilizando o módulo json.

Após o carregamento, os dados são armazenados em memória e ficam disponíveis para consulta durante a interação do usuário com o agente.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Quando o usuário realiza uma pergunta, o agente consulta os dados relevantes da base de conhecimento para construir um contexto que será enviado ao modelo de linguagem.

As informações mais relevantes são selecionadas, como:

- resumo das transações financeiras;

- perfil do investidor;

- possíveis produtos financeiros adequados;

- histórico recente de atendimentos.

Esses dados são então incluídos no prompt enviado ao modelo de linguagem, permitindo que a resposta seja gerada com base em informações reais do cliente.

Esse processo segue o conceito de RAG (Retrieval Augmented Generation), no qual a geração de respostas é enriquecida com dados externos confiáveis.

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Idade: 35 anos
- Perfil de Investidor: Moderado
- Renda mensal: R$ 6.000
- Objetivo financeiro: Construção de reserva financeira e investimento de longo prazo

Resumo de Gastos Recentes:
- Alimentação: R$ 950
- Transporte: R$ 420
- Lazer: R$ 380
- Moradia: R$ 1.500

Últimas Transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
- 05/11: Restaurante - R$ 120
- 06/11: Transporte - R$ 60

Produtos Financeiros Disponíveis:
- Tesouro Direto (baixo risco)
- Fundo de renda fixa
- Fundo multimercado
```
Esse contexto é enviado ao modelo de linguagem para que ele possa gerar respostas mais precisas, personalizadas e alinhadas à situação financeira do cliente.
