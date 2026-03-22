# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que serve no Gus? |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Fornecer contexto sobre interações anteriores do usuário |
| `perfil_usuario.json` | JSON | Personalizar respostas com base no perfil e comportamento financeiro |
| `estrategias_financeiras.json` | JSON | Sugerir estratégias e boas práticas de controle financeiro |
| `transacoes.csv` | CSV | Analisar padrões de gastos e identificar hábitos financeiros |



---

## Adaptações nos Dados

Os dados mockados foram adaptados para refletir o contexto da **FIA (Financial Intelligent Assistant)**, com foco em controle de gastos e educação financeira.

Foram realizadas as seguintes alterações:

- Ajuste do `historico_atendimento.csv` para incluir interações relacionadas a controle de gastos e organização financeira  
- Substituição do arquivo `perfil_investidor.json` por `perfil_usuario.json`, com foco em comportamento financeiro  
- Transformação de `produtos_financeiros.json` em `estrategias_financeiras.json`, contendo ações e boas práticas ao invés de produtos bancários  
- Manutenção e uso do `transacoes.csv` para análise de padrões de consumo  

Essas adaptações permitem que a FIA gere respostas mais consistentes, contextualizadas e alinhadas ao comportamento financeiro do usuário.

---

## Estratégia de Integração

### Como os dados são carregados?

Os dados podem ser integrados de duas formas:

- Injeção direta no prompt (para prototipagem e validação do agente)  
- Carregamento via código, permitindo maior escalabilidade e reutilização

```
import pandas as pd
import json

# Carregando CSVs
transacoes = pd.read_csv("data/transacoes.csv")
historico = pd.read_csv("data/historico_atendimento.csv")

# Carregando JSONs
with open("data/perfil_usuario.json", "r", encoding="utf-8") as f:
    perfil_usuario = json.load(f)

with open("data/estrategias_financeiras.json", "r", encoding="utf-8") as f:
    estrategias = json.load(f)
```

### Como os dados são usados no prompt?

Para fins de simplificação, os dados da base de conhecimento são injetados diretamente no prompt, garantindo que a **FIA** tenha acesso ao contexto necessário para gerar respostas mais precisas e personalizadas.

Essa abordagem permite simular o comportamento de um agente contextualizado, utilizando informações estruturadas sobre o usuário, suas transações, histórico de interações e estratégias financeiras.

Em cenários mais robustos, o ideal é que esses dados sejam consultados dinamicamente e incorporados ao prompt de forma seletiva, permitindo maior escalabilidade, flexibilidade e controle sobre o contexto enviado ao modelo.

Abaixo está um exemplo de como os dados são estruturados e utilizados no prompt:

```
DADOS DO USUÁRIO (data/perfil_usuario.json):
{
  "nome": "João Silva",
  "idade": 32,
  "profissao": "Analista de Sistemas",
  "renda_mensal": 5000.00,

  "perfil_financeiro": {
    "nivel_organizacao": "baixo",
    "controle_gastos": false,
    "costuma_planejar": false
  },

  "objetivo_principal": "Controlar gastos e criar uma reserva de emergência",

  "situacao_atual": {
    "saldo_medio_mensal": 500,
    "gastos_maiores_categorias": ["alimentacao", "lazer"],
    "possui_dividas": false
  },

  "metas": [
    {
      "meta": "Criar reserva de emergência",
      "valor_necessario": 10000.00,
      "prazo": "2026-06"
    },
    {
      "meta": "Reduzir gastos com lazer",
      "descricao": "Diminuir despesas com restaurantes e streaming"
    }
  ]
}

TRANSAÇÕES DO USUÁRIO (data/transacoes.csv):
data,descricao,categoria,valor,tipo
2025-10-01,Salário,receita,5000.00,entrada
2025-10-02,Aluguel,moradia,1200.00,saida
2025-10-03,Supermercado,alimentacao,450.00,saida
2025-10-05,Netflix,lazer,55.90,saida
2025-10-07,Farmácia,saude,89.00,saida
2025-10-10,Restaurante,alimentacao,120.00,saida
2025-10-12,Uber,transporte,45.00,saida
2025-10-15,Conta de Luz,moradia,180.00,saida
2025-10-20,Academia,saude,99.00,saida
2025-10-25,Combustível,transporte,250.00,saida

HISTÓRICO DE ATENDIMENTO DO USUÁRIO (data/historico_atendimento.csv):
data,canal,tema,resumo,resolvido
2025-09-15,chat,Gastos com alimentação,Usuário pediu ajuda para reduzir gastos com delivery,sim
2025-09-22,chat,Controle financeiro,Usuário não sabia para onde o dinheiro estava indo,sim
2025-10-01,chat,Gastos com lazer,Usuário percebeu excesso em streaming e restaurantes,sim
2025-10-12,chat,Metas financeiras,Usuário quer criar meta de economia mensal,sim
2025-10-18,chat,Orçamento mensal,Usuário pediu ajuda para organizar orçamento,sim
2025-10-25,chat,Controle de gastos,Usuário quer acompanhar despesas no dia a dia,sim

ESTRATÉGIAS FINANCEIRAS (data/estrategias_financeiras.json):
[
  {
    "nome": "Controle de gastos por categoria",
    "descricao": "Separar seus gastos por categorias para entender para onde seu dinheiro está indo",
    "quando_usar": "Quando o usuário não tem clareza sobre seus gastos",
    "beneficio": "Maior controle financeiro e identificação de excessos"
  },
  {
    "nome": "Definir limite de gastos mensais",
    "descricao": "Estabelecer um valor máximo para cada categoria de gasto",
    "quando_usar": "Quando o usuário gasta mais do que deveria",
    "beneficio": "Evita descontrole financeiro e ajuda a economizar"
  },
  {
    "nome": "Redução gradual de despesas",
    "descricao": "Diminuir gastos aos poucos ao invés de cortar tudo de uma vez",
    "quando_usar": "Quando há excesso em categorias como lazer ou alimentação",
    "beneficio": "Mudança sustentável de hábitos"
  },
  {
    "nome": "Criação de reserva de emergência",
    "descricao": "Guardar uma parte do dinheiro mensalmente para imprevistos",
    "quando_usar": "Quando o usuário não possui segurança financeira",
    "beneficio": "Maior tranquilidade em situações inesperadas"
  },
  {
    "nome": "Acompanhamento semanal de gastos",
    "descricao": "Revisar gastos semanalmente para evitar surpresas no fim do mês",
    "quando_usar": "Para manter controle contínuo",
    "beneficio": "Maior previsibilidade financeira"
  }
]
```

---

## Exemplo de Contexto Montado

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
- Principais categorias de gasto: alimentação, lazer
- Possui dívidas: não

Metas:
- Criar reserva de emergência (R$ 10.000 até 2026-06)
- Reduzir gastos com lazer

Resumo de Gastos (último período):
- Moradia: R$ 1.380
- Alimentação: R$ 570
- Transporte: R$ 295
- Lazer: R$ 55,90
- Saúde: R$ 188

Histórico de Interações:
- Usuário já solicitou ajuda para reduzir gastos com alimentação
- Já demonstrou dificuldade em controlar despesas mensais
- Já buscou organizar orçamento

Estratégias Disponíveis:
- Controle de gastos por categoria
- Definição de limites mensais
- Redução gradual de despesas
- Acompanhamento semanal de gastos
```
**Entrada do Usuário:**
``` 
"Como posso economizar mais no fim do mês?"
```
