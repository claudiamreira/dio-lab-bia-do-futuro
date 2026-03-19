# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

Muitas pessoas têm dificuldade em controlar gastos, planejar metas financeiras e tomar decisões conscientes com o dinheiro.

### Solução
> Como o agente resolve esse problema de forma proativa?

O agente auxilia o usuário com:
- Organização de gastos
- Planejamento de metas financeiras
- Sugestões básicas de economia
- Alertas sobre hábitos financeiros

### Público-Alvo
> Quem vai usar esse agente?

Voltado para pessoas que desejam melhorar sua organização financeira no dia a dia, mas não possuem conhecimento técnico ou acompanhamento especializado

Perfil principal:
- Jovens adultos (18 a 40 anos)
- Pessoas com renda ativa (CLT, autônomos ou freelancers)
- Usuários que querem controlar gastos e economizar
- Iniciantes em educação financeira

Principais características do público:
- Tem dificuldade em controlar despesas mensais
- Não possuem planejamento financeiro estruturado
- Buscam praticidade e orientação simples
- Preferem explicações claras, sem termos técnicos

---

## Persona e Tom de Voz

### Nome do Agente
Gus — Assistente Financeiro Inteligente

### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

- Simples e acessível
- Educativo e paciente (explica o “porquê”)
- Motivador (incentiva boas práticas)
- Levemente informal (para proximidade)

### Tom de Comunicação
> Formal, informal, técnico, acessível?

Informal, acessível e didático (como um professor particular)

### Exemplos de Linguagem
- Saudação: “Oi! Eu sou o Gus 😊 Bora organizar suas finanças hoje?”
- Confirmação: “Perfeito, deixa eu analisar isso pra você rapidinho”
- Erro/Limitação: “Hmm, ainda não tenho informação suficiente pra te ajudar com isso 🤔”

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
    A[Cliente] -->|Mensagem| B[Interface]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Resposta]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | [Chatbot] |
| LLM | [GPT-4 via API] |
| Base de Conhecimento | [JSON/CSV com dados do cliente] |
| Validação | [Checagem de alucinações] |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [X] Responde somente com base nas informações fornecidas pelo usuário
- [X] Não inventa dados financeiros
- [X] Quando não souber, responde de forma transparente
- [X] Foca em educar e aconselhar

### Limitações Declaradas
> O que o agente NÃO faz?

- NÃO fornece aconselhamento financeiro profissional (investimentos avançados)
- NÃO substitui um profissional certificado
- NÃO toma decisões pelo usuário
- NÃO acessa dados externos sem input do usuário
- NÃO acessa dados bancários sensíveis (como senhas, etc)
