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

### Papel de cada arquivo no contexto

`perfil_usuario.json:` define quem é o usuário, seus objetivos e seu perfil financeiro

`transacoes.csv:` permite identificar padrões de entrada, saída e categorias com maior impacto no orçamento

`historico_atendimento.csv:` traz contexto sobre dúvidas e dificuldades já relatadas anteriormente

`estrategias_financeiras.json:` oferece um conjunto de orientações e ações que a FIA pode sugerir com base no cenário identificado
