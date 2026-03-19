# 🤖 Agente Financeiro Inteligente com IA Generativa

## 💡 Contexto do Projeto

Neste projeto, desenvolvi um **assistente financeiro inteligente** utilizando IA Generativa, com o objetivo de ir além de um chatbot tradicional.

A proposta foi criar um agente capaz de:

- **Antecipar necessidades**, não apenas responder perguntas
- **Personalizar** sugestões com base no contexto de cada usuário
- **Atuar de forma consultiva na organização financeira**
- **Garantir segurança** e confiabilidade nas respostas, evitando alucinações

---

## 🤖 O Que Foi Desenvolvido

Ao longo do projeto, idealizei e estruturei um agente financeiro completo, passando pelas seguintes etapas:

### 🧠 1. Documentação do Agente

Caso de uso:

O agente foi projetado para ajudar usuários a controlarem seus gastos, organizarem sua vida financeira e desenvolverem hábitos mais conscientes com o dinheiro.

Persona e tom de voz:
Criei o **Gus**, um **assistente financeiro inteligente** com comunicação informal, acessível e didático, atuando como um “professor particular” de finanças.

Arquitetura:
Estruturei o fluxo de interação entre usuário, processamento da IA e geração de respostas baseadas em contexto.

Segurança:
Defini diretrizes para evitar alucinações, garantindo que o agente responda apenas com base nos dados disponíveis e sinalize quando não houver informação suficiente.

📄 **Documentação:** [`docs/01-documentacao-agente.md`](./docs/01-documentacao-agente.md)

---

### 📊 2. Base de Conhecimento

Utilizei **dados mockados** disponíveis na pasta [`data/`](./data/) para simular o contexto financeiro do usuário, garantindo consistência nas respostas do agente.

Os dados incluem:

| Arquivo | Formato | Descrição |
|---------|---------|-----------|
| `transacoes.csv` | CSV | Histórico de transações do cliente |
| `historico_atendimento.csv` | CSV | Histórico de atendimentos anteriores |
| `perfil_investidor.json` | JSON | Perfil e preferências do cliente |
| `produtos_financeiros.json` | JSON | Produtos e serviços disponíveis |

Essas informações são utilizadas para personalizar as interações e tornar o agente mais assertivo.

📄 **Documentação:** [`docs/02-base-conhecimento.md`](./docs/02-base-conhecimento.md)

---

### 💬 3. Prompts do Agente

Desenvolvi prompts estruturados para definir o comportamento do Gus, incluindo:

- **System Prompt:** Regras, tom de voz e limitações
- **Exemplos de Interação:** Cenários reais de uso
- **Tratamento de Edge Cases:** Respostas seguras em situações ambíguas

📄 **Documentação:** [`docs/03-prompts.md`](./docs/03-prompts.md)

---

### 💻 4. Aplicação Funcional

Implementei um **protótipo funcional** do agente, com:

- Interface de chatbot interativo
- Integração com modelo de linguagem (LLM)
- Conexão com a base de conhecimento

📁 **Código:** [`src/`](./src/)

---

### 📈 5. Avaliação e Métricas

Defini critérios para avaliar a qualidade do agente, como:

- Precisão das respostas
- Segurança (redução de alucinações)
- Coerência com o perfil do usuário

📄 **Documentação:** [`docs/04-metricas.md`](./docs/04-metricas.md)

---

### 🎤 6. Pitch

Estruturei um pitch de apresentação do projeto, abordando:

- Problema resolvido
- Funcionamento do agente
- Diferenciais da solução

📄 **Roteiro:** [`docs/05-pitch.md`](./docs/05-pitch.md)

---

## Ferramentas Utilizadas

| Categoria | Ferramentas |
|-----------|-------------|
| **LLMs** | [ChatGPT](https://chat.openai.com/) |
| **Desenvolvimento** | [Google Colab](https://colab.research.google.com/) |
| **Orquestração** | [LangChain](https://www.langchain.com/), [LangFlow](https://www.langflow.org/), [CrewAI](https://www.crewai.com/) |
| **Diagramas** | [Mermaid](https://mermaid.js.org/) |

---

## Estrutura do Repositório

```
📁 lab-agente-financeiro/
│
├── 📄 README.md
│
├── 📁 data/                          # Dados mockados para o agente
│   ├── historico_atendimento.csv     # Histórico de atendimentos (CSV)
│   ├── perfil_investidor.json        # Perfil do cliente (JSON)
│   ├── produtos_financeiros.json     # Produtos disponíveis (JSON)
│   └── transacoes.csv                # Histórico de transações (CSV)
│
├── 📁 docs/                          # Documentação do projeto
│   ├── 01-documentacao-agente.md     # Caso de uso e arquitetura
│   ├── 02-base-conhecimento.md       # Estratégia de dados
│   ├── 03-prompts.md                 # Engenharia de prompts
│   ├── 04-metricas.md                # Avaliação e métricas
│   └── 05-pitch.md                   # Roteiro do pitch
│
├── 📁 src/                           # Código da aplicação
│   └── app.py                        # (exemplo de estrutura)
│
├── 📁 assets/                        # Imagens e diagramas
│   └── ...
│
└── 📁 examples/                      # Referências e exemplos
    └── README.md
```

---

## 🚀 Diferencial do Projeto

O principal diferencial deste agente está na combinação de:

- Personalização baseada em dados
- Comunicação humanizada
- Foco em educação financeira prática
- Preocupação com segurança e confiabilidade
  
---

## ✨ Considerações Finais

Este projeto demonstra a construção de um agente financeiro completo, desde a concepção até a prototipação, aplicando boas práticas de engenharia de prompt, uso de dados e experiência do usuário.
