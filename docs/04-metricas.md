# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação da Clara AI pode ser feita de duas formas complementares:

1. **Testes estruturados:** São definidos cenários de perguntas que simulam interações reais de um usuário com o agente. As respostas do agente são comparadas com o comportamento esperado;
2. **Feedback de Usuários:** Pessoas podem testar o agente e avaliar a utilidade, clareza e coerência das respostas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | Verifica se o agente respondeu corretamente com base nos dados disponíveis | Perguntar em qual categoria o cliente mais gasta e verificar se o agente identifica corretamente com base no transacoes.csv |
|  **Segurança** | Avalia se o agente evita inventar informações quando não possui dados suficientes | Perguntar algo fora do contexto financeiro e verificar se o agente informa que não possui essa informação |
| **Coerência** | Verifica se as recomendações financeiras estão alinhadas ao perfil do investidor | Perguntar sobre investimentos e verificar se as sugestões respeitam o perfil de risco do cliente |

> [!TIP]
>Para tornar a avaliação mais confiável, diferentes pessoas podem testar o agente simulando perguntas comuns de usuários. Cada participante pode atribuir notas de 1 a 5 para critérios como clareza da resposta, utilidade da recomendação e coerência com o contexto financeiro do cliente fictício.

---

## Exemplos de Cenários de Teste

A seguir estão alguns cenários utilizados para validar o comportamento da Clara AI.

### Teste 1: Consulta de gastos
- **Pergunta:** "Onde estou gastando mais dinheiro?"
- **Resposta esperada: **Identificação da categoria com maior valor de gastos com base no arquivo`transacoes.csv`
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 2: Recomendação de investimento
- **Pergunta:** "Qual investimento combina com meu perfil?"
- **Resposta esperada:** Sugestão de investimentos compatíveis com o perfil definido no arquivo `perfil_investidor.json`
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo para amanhã?"
- **Resposta esperada:** O agente informa que seu foco é auxiliar com planejamento financeiro.
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Qual o rendimento anual do produto XYZ?"
- **Resposta esperada:** O agente informa que não possui essa informação na base de conhecimento
- **Resultado:** [ ] Correto  [ ] Incorreto

---

## Resultados

Após a execução dos testes, foram observados os seguintes pontos:

**O que funcionou bem:**
- O agente conseguiu responder perguntas relacionadas ao histórico financeiro do cliente utilizando os dados disponíveis
- As respostas foram claras e apresentaram linguagem acessível para usuários sem conhecimento técnico em finanças.
- O agente demonstrou comportamento seguro ao informar quando não possuía dados suficientes para responder determinadas perguntas.

**O que pode melhorar:**
- O tempo de resposta pode variar devido à execução do modelo de linguagem localmente.
- O agente ainda depende exclusivamente da base de dados mockada, podendo ser expandido futuramente para integrar outras fontes de informação financeira.
- O sistema pode evoluir para incluir análises financeiras mais detalhadas e alertas proativos.


---

## Métricas Avançadas (Opcional)

Para este protótipo acadêmico, não foram implementadas ferramentas avançadas de observabilidade. Entretanto, algumas métricas que poderiam ser utilizadas em versões futuras incluem:

- Latência: tempo necessário para gerar uma resposta após a pergunta do usuário.
- Taxa de erros: número de respostas que não conseguem ser geradas corretamente.
- Qualidade da resposta: avaliação qualitativa baseada no feedback de usuários.

Ferramentas especializadas em monitoramento de aplicações com LLM, como LangWatch e LangFuse, poderiam ser utilizadas em versões futuras do agente para acompanhar essas métricas de forma mais detalhada.
