---
title: SDD
nav_order: 4
has_children: true
has_toc: false
---

# SDD — Documentação Orientada a Especificações do Projeto EVA

Esta pasta contém a documentação de design do Projeto EVA estruturada segundo a metodologia **Spec-Driven Development (SDD)** do **GitHub Spec Kit**, conforme a [base do Microsoft Learn](https://learn.microsoft.com/pt-br/training/modules/spec-driven-development-github-spec-kit-greenfield-intro/).

Os artefatos foram derivados dos documentos de projeto:
- [Projeto EVA — Resumo](../Projeto%20EVA%20Resumo.md)
- [Projeto EVA — Documento Base](../Projeto%20Eva%20Documento%20Base.md)

## A metodologia em uma linha

> **Constituição → Especificação → Plano → Tarefas → Implementação.** Cada fase produz um artefato que alimenta a próxima; todos são **documentos vivos**, mantidos em sincronia com a realidade.

## Artefatos

| Ordem | Artefato | Comando Spec Kit | Responde | Conteúdo |
|-------|----------|------------------|----------|----------|
| 1 | [constitution.md](constitution.md) | `/speckit.constitution` | Quais regras são inegociáveis? | Princípios, restrições e padrões que toda decisão deve respeitar |
| 2 | [spec.md](spec.md) | `/speckit.specify` | **O quê** e **por quê**? | Resumo, histórias de usuário, critérios de aceitação, requisitos funcionais e não funcionais, casos extremos |
| 3 | [plan.md](plan.md) | `/speckit.plan` | **Como**? | Arquitetura, pilha de tecnologia, sequência de implementação, verificação da constituição, premissas |
| 4 | [tasks.md](tasks.md) | `/speckit.tasks` | Em **quais passos**? | Itens de trabalho discretos e testáveis, organizados em fases |

A fase de **implementação** (`/speckit.implement`) ocorre no repositório de código da EVA, executando as tarefas de `tasks.md`.

## Principais pontos identificados nos documentos base

Estes pontos foram extraídos dos documentos de projeto e ancoram toda a SDD:

- **Agente de IA local** para macOS e Windows — o núcleo funciona offline.
- **Privacidade por design** — nada sai da máquina sem opt-in explícito.
- **Open source** e construção comunitária (PUC Angels), orçamento R$ 0.
- **Três frentes** em um produto: assistente pessoal, IDE de código, motor de conhecimento.
- **Rede peer-to-peer** para compartilhar capacidade computacional.
- **Integração opt-in** com ChatGPT, Gemini e DeepSeek.
- **Módulos M1–M7** e **KPI** de 70% de adoção da rede em 12 meses.

## Fluxo de trabalho e pontos de verificação

```
constitution.md ──> spec.md ──> plan.md ──> tasks.md ──> implementação
       (regras)      (o quê)      (como)      (passos)      (código)
        ▲                                                      │
        └──────────── documentos vivos: descobertas voltam ───┘
```

Comandos opcionais de qualidade do Spec Kit aplicáveis aqui:
- **`/speckit.clarify`** — resolver as *perguntas em aberto* listadas em `spec.md` e `plan.md`.
- **`/speckit.analyze`** — checar consistência entre spec ↔ plan ↔ tasks antes de implementar.
- **`/speckit.checklist`** — gerar checklist de qualidade da especificação.

## Status

Versão 1.0 — **proposta inicial** para discussão na reunião de kickoff. As decisões de tecnologia em `plan.md` são candidatas e devem ser ratificadas pelo time fundador (ver tarefa **T1.1** e as perguntas em aberto).

---

*Documentação mantida pelo Comitê de IA da PUC Angels. Sujeita a revisão colaborativa.*
