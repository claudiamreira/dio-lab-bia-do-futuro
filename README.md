# 🤖 FIA — Agente Financeiro Inteligente com IA Generativa

A **FIA (Financial Intelligence Assistant)** é uma assistente financeira desenvolvida com foco em **organização financeira, personalização e segurança nas respostas**.

Mais do que um chatbot tradicional, a proposta deste projeto é simular um agente capaz de interpretar contexto, sugerir estratégias práticas e apoiar o usuário na construção de hábitos financeiros mais conscientes, utilizando **IA generativa** e uma **base de conhecimento estruturada**.

---

## 💡 Objetivo do Projeto

Este projeto foi criado com o objetivo de desenvolver uma assistente financeira inteligente capaz de:

- Antecipar necessidades do usuário, e não apenas responder perguntas
- Personalizar sugestões com base em contexto e perfil financeiro
- Atuar de forma consultiva na organização da vida financeira
- Garantir respostas mais seguras e confiáveis, reduzindo alucinações

---

## ✨ Funcionalidades

A FIA foi idealizada para oferecer:

- Análise de transações financeiras mockadas
- Sugestões personalizadas com base no perfil do usuário
- Respostas contextualizadas com histórico de atendimento
- Orientações financeiras em linguagem simples e didática
- Tratamento seguro para cenários ambíguos ou com falta de informação

---

## 🧠 O Que Foi Desenvolvido

O projeto foi estruturado em cinco frentes principais:

### 1. Documentação do Agente
Definição do caso de uso, persona, tom de voz, arquitetura e diretrizes de segurança da FIA.

📄 **Documentação:** [`docs/01-documentacao-agente.md`](./docs/01-documentacao-agente.md)

---

### 2. Base de Conhecimento
Construção de uma base com dados mockados para simular o contexto financeiro do usuário e permitir respostas mais personalizadas.

📄 **Documentação:** [`docs/02-base-conhecimento.md`](./docs/02-base-conhecimento.md)

---

### 3. Prompts do Agente
Desenvolvimento dos prompts que orientam comportamento, tom de voz, limites e exemplos de interação da assistente.

📄 **Documentação:** [`docs/03-prompts.md`](./docs/03-prompts.md)

---

### 4. Aplicação Funcional
Desenvolvimento de um protótipo funcional com interface de chatbot, integração com modelo de linguagem e conexão com a base de conhecimento.

📁 **Código:** [`src/`](./src/)

---

### 5. Avaliação e Métricas
Definição de critérios para avaliar qualidade, segurança e coerência das respostas geradas.

📄 **Documentação:** [`docs/04-metricas.md`](./docs/04-metricas.md)

---

### 6. Pitch do Projeto
Estruturação de um roteiro de apresentação destacando problema, solução e diferenciais da FIA.

📄 **Roteiro:** [`docs/05-pitch.md`](./docs/05-pitch.md)

---

## 🔄 Fluxo da Solução

O funcionamento da FIA segue a seguinte lógica:

1. O usuário envia uma pergunta ou solicitação
2. A aplicação consulta os dados disponíveis na base de conhecimento
3. O modelo interpreta o contexto com base no perfil e histórico do usuário
4. A FIA gera uma resposta personalizada, didática e segura

---

## 🗂️ Base de Conhecimento

Os dados utilizados no projeto estão organizados na pasta [`data/`](./data/) e simulam informações relevantes para o contexto financeiro do usuário.

| Arquivo | Formato | Descrição |
|---------|---------|-----------|
| `transacoes.csv` | CSV | Histórico de transações do cliente |
| `historico_atendimento.csv` | CSV | Histórico de atendimentos anteriores |
| `perfil_usuario.json` | JSON | Perfil de comportamento financeiro |
| `estrategias_financeiras.json` | JSON | Ações, dicas e estratégias financeiras |

Essas informações ajudam a tornar as interações mais contextualizadas e assertivas.

---

## 🛠️ Tecnologias e Ferramentas

| Categoria | Ferramentas |
|-----------|-------------|
| **LLM** | ChatGPT |
| **Desenvolvimento** | Google Colab, Python |
| **Estruturação e experimentação** | LangChain, LangFlow, CrewAI |
| **Diagramas** | Mermaid |

> **Observação:** algumas ferramentas foram utilizadas para apoio na estruturação, exploração de arquitetura e organização do projeto.

---

## 📁 Estrutura do Repositório

```bash
lab-agente-financeiro/
│
├── README.md
│
├── data/
│   ├── historico_atendimento.csv
│   ├── perfil_usuario.json
│   ├── estrategias_financeiras.json
│   └── transacoes.csv
│
├── docs/
│   ├── 01-documentacao-agente.md
│   ├── 02-base-conhecimento.md
│   ├── 03-prompts.md
│   ├── 04-metricas.md
│   └── 05-pitch.md
│
├── src/
│   └── app.py
│
├── assets/
│   └── ...
│
└── examples/
    └── README.md
```

## ▶️ Como Executar o Projeto

> Ajuste esta seção conforme a estrutura real do seu projeto.

### Pré-requisitos
- Python 3.10 ou superior
- Ambiente com suporte à instalação de dependências
- Chave de API do modelo de linguagem, se aplicável

### Instalação

```
bash
git clone <URL_DO_REPOSITORIO>
cd lab-agente-financeiro
pip install -r requirements.txt
```

### Execução

```
python src/app.py
```

## 📌 Limitações Atuais

Este projeto possui caráter educacional e prototipado. Atualmente:

- Utiliza dados mockados para simulação
- Não realiza integração com APIs bancárias reais
- Não substitui orientação financeira profissional
- O foco está na experiência do agente, estruturação da solução e qualidade das respostas

## 🚀 Diferenciais do Projeto

Os principais diferenciais da FIA são:

Personalização baseada em dados
Comunicação humanizada e didática
Foco em educação financeira prática
Preocupação com segurança e confiabilidade
Estrutura orientada à redução de alucinações

## 🔮 Próximos Passos

Como evolução do projeto, os próximos passos podem incluir:

Integração com banco de dados real
Implementação de autenticação de usuário
Criação de dashboard financeiro
Expansão das métricas de avaliação
Aprimoramento da rastreabilidade das respostas do agente

## 🎯 Considerações Finais

Este projeto demonstra a aplicação prática de IA generativa na construção de um assistente especializado em finanças, unindo personalização, segurança e utilidade em uma solução voltada à organização financeira do usuário.
