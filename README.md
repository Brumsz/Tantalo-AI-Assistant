# 🤖 Lua — Assistente de Chat e Qualificação com IA para a Tântalo

> Assistente conversacional inteligente com memória de longo prazo, desenvolvido para substituir formulários estáticos por uma experiência dinâmica de qualificação de leads e consultoria de alto valor.

---

## 📌 Sobre o Projeto

A **Tântalo** é uma empresa de consultoria especializada na metodologia **Zettelkasten**. O desafio era claro: o processo de qualificação de leads era feito por formulários estáticos, frios e com alta taxa de abandono.

A solução foi criar a **Lua** — uma assistente de IA com persona empática, capaz de conduzir conversas naturais, entender a intenção do usuário em tempo real e realizar diagnósticos precisos para serviços de consultoria de alto valor.

---

## 🎯 Objetivos

- Substituir formulários estáticos por uma experiência conversacional dinâmica
- Realizar o diagnóstico de leads de forma autônoma e assertiva
- Gerenciar agendamentos e remarcações integradas à agenda da empresa
- Educar o lead com base em uma base de conhecimento própria (RAG)

---

## 🏗️ Arquitetura do Sistema

```
Usuário (WhatsApp)
        │
        ▼
   Typebot (Interface conversacional)
        │
        ▼
      n8n (Orquestrador de fluxos)
        │
   ┌────┴────────────────────┐
   │                         │
   ▼                         ▼
PostgreSQL               pgvector (RAG)
(Memória contínua        (Vector Store —
 da conversa)             base de conhecimento)
   │                         │
   └────────┬────────────────┘
            │
            ▼
     LLM (Modelo de Linguagem)
            │
            ▼
   APIs externas: Google Calendar · Gmail · WhatsApp
```

---

## 🛠️ Tech Stack

| Categoria | Tecnologias |
|---|---|
| **Orquestração** | n8n |
| **Banco de Dados** | PostgreSQL com pgvector |
| **IA / LLM** | Modelos de Linguagem (LLMs) |
| **Busca Semântica** | RAG (Retrieval-Augmented Generation) |
| **NLP** | Processamento de Linguagem Natural |
| **Integrações via API** | Google Calendar, Gmail, WhatsApp |
| **Interface** | Typebot |

---

## ⚙️ Decisões Técnicas

### Banco de Dados Híbrido (PostgreSQL + pgvector)
A principal decisão arquitetural foi usar o **PostgreSQL como banco duplo**:
- **Memória contínua:** armazena o histórico completo de cada conversa, permitindo que a Lua lembre de interações anteriores com o mesmo lead (memória de longo prazo)
- **Vector Store:** usando a extensão **pgvector**, o banco funciona também como repositório vetorial para busca semântica na base de conhecimento da Tântalo

### Extração de Intenção em Tempo Real
O fluxo de n8n orquestra a extração de intenções do usuário durante a conversa, roteando automaticamente entre diferentes ações: responder dúvidas, agendar, reagendar ou encaminhar para um consultor humano.

### Persona Empática + Lógica de Back-office
O maior desafio foi equilibrar uma persona com comunicação empática e acolhedora com operações complexas de back-office (gerenciamento de agenda, envio de e-mails, atualização de registros). Isso foi resolvido separando as camadas de persona e de lógica no fluxo do n8n.

---

## ✅ Resultados

- Substituição completa dos formulários estáticos por fluxo conversacional
- Assistente capaz de qualificar leads, agendar e reagendar consultorias de forma autônoma
- Base de conhecimento vetorial permitindo respostas precisas sobre a metodologia Zettelkasten
- Memória de longo prazo ativa — a assistente reconhece e contextualiza leads recorrentes

---

## 🔒 Nota sobre o Código

Este repositório contém apenas a documentação técnica do projeto. O código-fonte e os fluxos de automação não estão disponíveis publicamente por questões de confidencialidade com o cliente.

---

## 👤 Autor

**João Victor Brum**
- [LinkedIn](https://www.linkedin.com/in/joãobrumcosta)
- [GitHub](https://github.com/Brumsz)
- joaovictorbrumcosta@gmail.com
