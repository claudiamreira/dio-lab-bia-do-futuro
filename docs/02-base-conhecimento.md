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

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Os dados mockados foram adaptados para refletir o contexto do agente Gus, que tem como foco o controle de gastos e a educação financeira.

Foram realizadas as seguintes alterações:

- Ajuste do `historico_atendimento.csv` para incluir interações relacionadas a controle de gastos e organização financeira  
- Substituição do arquivo `perfil_investidor.json` por `perfil_usuario.json`, com foco em comportamento financeiro  
- Transformação de `produtos_financeiros.json` em `estrategias_financeiras.json`, contendo ações e boas práticas ao invés de produtos bancários  
- Manutenção e uso do `transacoes.csv` para análise de padrões de consumo  

Essas adaptações permitem que o agente gere respostas mais consistentes, contextualizadas e alinhadas ao comportamento financeiro do usuário.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Existem duas possibilidades, injetar os dados diretamente no prompt (Ctrl C + Ctrl V) ou carregar os arquivos via código, como no exemplo abaixo.

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
> Os dados vão no system prompt? São consultados dinamicamente?

[Sua descrição aqui]

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
