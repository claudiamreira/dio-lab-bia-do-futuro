# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que serve na FIA? |
|---------|---------|------------------------|
| `historico_atendimento.csv` | CSV | Fornecer contexto sobre interações anteriores do usuário |
| `perfil_usuario.json` | JSON | Personalizar respostas com base no perfil e no comportamento financeiro |
| `estrategias_financeiras.json` | JSON | Sugerir estratégias e boas práticas de organização financeira |
| `transacoes.csv` | CSV | Analisar padrões de gastos e identificar hábitos de consumo |

---

## Adaptações nos Dados

Os dados mockados foram adaptados para refletir o contexto da **FIA (Financial Intelligence Assistant)**, com foco em controle de gastos, organização financeira e educação financeira prática.

Foram realizadas as seguintes adaptações:

- Ajuste do `historico_atendimento.csv` para incluir interações relacionadas a controle de gastos, orçamento e metas financeiras
- Substituição do arquivo `perfil_investidor.json` por `perfil_usuario.json`, com foco em comportamento e rotina financeira
- Transformação de `produtos_financeiros.json` em `estrategias_financeiras.json`, reunindo ações e boas práticas em vez de produtos bancários
- Manutenção do `transacoes.csv` para análise de padrões de consumo e identificação de categorias com maior impacto financeiro

Essas adaptações permitem que a FIA gere respostas mais consistentes, contextualizadas e alinhadas ao perfil e aos objetivos do usuário.

---

## Estratégia de Integração

### Como os dados são carregados?

Os dados podem ser integrados de duas formas:

- Inclusão direta no prompt, ideal para prototipagem e validação inicial do agente
- Carregamento via código, permitindo maior escalabilidade, reaproveitamento e controle do contexto

```python
import pandas as pd
import json

# Carregando arquivos CSV
transacoes = pd.read_csv("data/transacoes.csv")
historico = pd.read_csv("data/historico_atendimento.csv")

# Carregando arquivos JSON
with open("data/perfil_usuario.json", "r", encoding="utf-8") as f:
    perfil_usuario = json.load(f)

with open("data/estrategias_financeiras.json", "r", encoding="utf-8") as f:
    estrategias = json.load(f)
```
Após o carregamento, esses dados podem ser organizados e enviados como contexto ao modelo, permitindo que a FIA personalize suas respostas com base no perfil, no histórico e nos padrões financeiros do usuário.

---

## Como os Dados São Usados no Prompt

Para fins de simplificação, os dados da base de conhecimento são incorporados diretamente ao contexto enviado ao modelo. Dessa forma, a FIA consegue responder com maior precisão, utilizando informações estruturadas sobre o usuário, suas transações, histórico de interações e estratégias financeiras disponíveis.

Essa abordagem permite simular o comportamento de um agente contextualizado. Em cenários mais robustos, o ideal é que esses dados sejam consultados dinamicamente e incorporados ao prompt de forma seletiva, garantindo maior escalabilidade, flexibilidade e controle sobre o volume de contexto enviado ao modelo.

---

### Papel de cada arquivo no contexto

`perfil_usuario.json:` define quem é o usuário, seus objetivos e seu perfil financeiro

`transacoes.csv:` permite identificar padrões de entrada, saída e categorias com maior impacto no orçamento

`historico_atendimento.csv:` traz contexto sobre dúvidas e dificuldades já relatadas anteriormente

`estrategias_financeiras.json:` oferece um conjunto de orientações e ações que a FIA pode sugerir com base no cenário identificado

---

### Exemplo de Dados Utilizados no Contexto


> DADOS DO USUÁRIO (data/perfil_usuario.json):
```
{
  "nome": "João Silva",
  "idade": 32,
  "profissao": "Analista de Sistemas",
  "renda_mensal": 5000.0,
  "perfil_financeiro": {
    "nivel_organizacao": "baixo",
    "controle_gastos": false,
    "costuma_planejar": false
  },
  "objetivo_principal": "Controlar gastos e criar uma reserva de emergência",
  "situacao_atual": {
    "saldo_medio_mensal": 500.0,
    "categorias_com_maior_gasto": ["alimentacao", "lazer"],
    "possui_dividas": false
  },
  "metas": [
    {
      "meta": "Criar reserva de emergência",
      "valor_necessario": 10000.0,
      "prazo": "2026-06"
    },
    {
      "meta": "Reduzir gastos com lazer",
      "descricao": "Diminuir despesas com restaurantes e streaming"
    }
  ]
}
```

> TRANSAÇÕES DO USUÁRIO (data/transacoes.csv):
```
data,descricao,categoria,valor,tipo
2025-10-01,Salario,receita,5000.00,entrada
2025-10-02,Aluguel,moradia,1200.00,saida
2025-10-03,Supermercado,alimentacao,450.00,saida
2025-10-05,Netflix,lazer,55.90,saida
2025-10-07,Farmacia,saude,89.00,saida
2025-10-10,Restaurante,alimentacao,120.00,saida
2025-10-12,Uber,transporte,45.00,saida
2025-10-15,Conta de Luz,moradia,180.00,saida
2025-10-20,Academia,saude,99.00,saida
2025-10-25,Combustivel,transporte,250.00,saida
2025-10-28,Streaming de Musica,lazer,21.90,saida
2025-10-29,Delivery,alimentacao,78.50,saida
```

> HISTÓRICO DE ATENDIMENTO DO USUÁRIO (data/historico_atendimento.csv):
```
data,canal,tema,resumo,estrategia_sugerida,perfil_detectado,resolvido
2025-09-15,chat,Gastos com alimentação,"Cliente pediu ajuda para reduzir despesas com delivery e alimentação fora de casa",Redução gradual de despesas,usuario_com_excesso_em_delivery,sim
2025-09-22,chat,Controle financeiro,"Cliente relatou dificuldade para identificar para onde o dinheiro estava indo ao longo do mês",Controle de gastos por categoria,usuario_sem_clareza_financeira,sim
2025-10-01,chat,Gastos com lazer,"Cliente percebeu excesso de gastos com streaming, restaurantes e outras despesas de lazer",Identificação de gastos supérfluos,usuario_com_gastos_desnecessarios,sim
2025-10-12,chat,Metas financeiras,"Cliente demonstrou interesse em criar uma meta de economia mensal para melhorar sua organização financeira",Definição de meta de economia mensal,usuario_sem_meta_financeira,sim
2025-10-18,chat,Orçamento mensal,"Cliente pediu apoio para estruturar um orçamento mensal mais equilibrado e funcional",Organização entre gastos fixos e variáveis,usuario_sem_planejamento,sim
2025-10-25,chat,Controle de gastos,"Cliente solicitou orientação para acompanhar as despesas do dia a dia com mais frequência",Acompanhamento semanal de gastos,usuario_em_reeducacao_financeira,sim
```

> ESTRATÉGIAS FINANCEIRAS (data/estrategias_financeiras.json):
```
[
  {
    "nome": "Controle de gastos por categoria",
    "descricao": "Organizar os gastos em categorias para entender com clareza para onde o dinheiro está indo.",
    "quando_usar": "Quando o usuário não tem visibilidade sobre os próprios gastos ou sente que o dinheiro acaba sem explicação.",
    "beneficio": "Ajuda a identificar excessos, melhorar o planejamento e aumentar o controle financeiro."
  },
  {
    "nome": "Definir limite de gastos mensais",
    "descricao": "Estabelecer um valor máximo de gasto para cada categoria do orçamento mensal.",
    "quando_usar": "Quando o usuário costuma gastar acima do planejado ou tem dificuldade para manter disciplina financeira.",
    "beneficio": "Evita descontrole, facilita decisões de consumo e contribui para a economia no fim do mês."
  },
  {
    "nome": "Redução gradual de despesas",
    "descricao": "Diminuir gastos aos poucos, de forma realista, em vez de fazer cortes bruscos difíceis de manter.",
    "quando_usar": "Quando o usuário tem gastos elevados em categorias como lazer, delivery ou compras não essenciais.",
    "beneficio": "Promove mudança sustentável de hábitos sem gerar sensação de restrição extrema."
  },
  {
    "nome": "Criação de reserva de emergência",
    "descricao": "Separar mensalmente uma parte do dinheiro para formar uma reserva destinada a imprevistos.",
    "quando_usar": "Quando o usuário não possui proteção financeira para emergências, como problemas de saúde, desemprego ou despesas inesperadas.",
    "beneficio": "Aumenta a segurança financeira e reduz a necessidade de recorrer a dívidas em situações inesperadas."
  },
  {
    "nome": "Acompanhamento semanal de gastos",
    "descricao": "Revisar os gastos uma vez por semana para acompanhar a evolução do orçamento ao longo do mês.",
    "quando_usar": "Quando o usuário quer manter controle contínuo e evitar surpresas no fechamento do mês.",
    "beneficio": "Melhora a previsibilidade financeira e permite corrigir excessos antes que se tornem um problema maior."
  }
]
```
> Exemplo de Contexto Montado

```
Contexto do Usuário:

PERFIL
- Nome: João Silva
- Idade: 32 anos
- Profissão: Analista de Sistemas
- Renda mensal: R$ 5.000
- Nível de organização financeira: baixo
- Possui controle de gastos: não

Situação Atual:
- Saldo médio mensal: R$ 500
- Principais categorias de gasto: alimentação e lazer
- Possui dívidas: não

Metas:
- Criar reserva de emergência de R$ 10.000 até 2026-06
- Reduzir gastos com lazer

Resumo de Gastos (último período):
- Moradia: R$ 1.380,00
- Alimentação: R$ 648,50
- Transporte: R$ 295,00
- Lazer: R$ 77,80
- Saúde: R$ 188,00

Histórico de Interações:
- O usuário já pediu ajuda para reduzir gastos com alimentação
- Já demonstrou dificuldade em controlar despesas mensais
- Já buscou organizar o orçamento
- Já recebeu sugestões relacionadas a acompanhamento de gastos e definição de metas

Estratégias Disponíveis:
- Controle de gastos por categoria
- Definir limite de gastos mensais
- Redução gradual de despesas
- Criação de reserva de emergência
- Acompanhamento semanal de gastos
```

> Entrada do Usuário
```
Como posso economizar mais no fim do mês?
```

### Interpretação Esperada da FIA
Com base nesse contexto, a FIA pode identificar que o usuário apresenta baixa organização financeira, possui gastos relevantes em alimentação e lazer e tem como objetivo principal formar uma reserva de emergência. Assim, a resposta tende a priorizar orientações como categorização de despesas, redução gradual de gastos não essenciais e acompanhamento frequente do orçamento ao longo do mês.
