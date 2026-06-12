---
title: Tarefas (tasks)
parent: SDD
nav_order: 4
---

# Lista de Tarefas — Projeto EVA

> **Artefato SDD — `tasks.md`**
> Converte [`plan.md`](plan.md) em itens de trabalho discretos, acionáveis e testáveis, organizados por fases.
> Cada tarefa rastreia até um requisito de [`spec.md`](spec.md). Casos de uso não cobertos por nenhuma tarefa indicam lacuna a corrigir.
>
> Versão 1.0 (proposta) · Comitê de IA · PUC Angels · Junho de 2026

---

## Como usar

- `[ ]` pendente · `[~]` em andamento · `[x]` concluída.
- A coluna **Requisito** liga cada tarefa à especificação (RF/RNF) para rastreabilidade.
- A ordem das fases respeita as dependências do plano: fundação → núcleo local → conhecimento → privacidade → integrações → IDE → P2P → testes.

---

## Fase 1 — Fundação

Pré-requisito de tudo: estrutura, shell desktop e dados locais.

- [ ] **T1.1** Definir e ratificar a pilha de tecnologia (shell desktop, runtime, modelo) — fecha as perguntas em aberto do plano. — *Plano*
- [ ] **T1.2** Inicializar o repositório open source com licença permissiva, README e guia de contribuição. — *P3, RNF-08*
- [ ] **T1.3** Criar o esqueleto do aplicativo desktop multiplataforma (Mac/Windows) que abre uma janela vazia. — *RNF-04*
- [ ] **T1.4** Definir o esquema de dados local (SQLite): usuário/preferências, sessões, documentos, índice. — *RF-02*
- [ ] **T1.5** Configurar pipeline de build/empacotamento para Mac e Windows. — *RNF-04*

## Fase 2 — Núcleo local + Assistente pessoal (MVP demonstrável)

- [ ] **T2.1** Integrar o runtime de inferência local e carregar um modelo open source on-device. — *RF-01, P2*
- [ ] **T2.2** Implementar `enviarMensagem(prompt)` que gera resposta com o modelo local, **100% offline**. — *RF-01, RF-03, RNF-02*
- [ ] **T2.3** Construir a UI de chat (envio, streaming de resposta, histórico). — *RF-03, B1*
- [ ] **T2.4** Implementar memória/contexto persistente local entre sessões. — *RF-02, B2*
- [ ] **T2.5** Implementar primitivas de automação de tarefas do usuário. — *RF-04, B3*
- [ ] **T2.6** Validar funcionamento sem rede e com hardware limitado (fallback para modelo menor). — *RNF-02, RNF-03, caso extremo*

## Fase 3 — Motor de conhecimento

- [ ] **T3.1** Implementar ingestão de documentos locais (formatos a definir no `/clarify`). — *RF-06, D1*
- [ ] **T3.2** Gerar embeddings localmente e gravar no índice vetorial. — *RF-06, P1*
- [ ] **T3.3** Implementar busca semântica e resposta contextualizada com citação dos trechos usados. — *RF-07, D2*
- [ ] **T3.4** Tratar formato não suportado/arquivo corrompido com mensagem de erro clara. — *Caso extremo*

## Fase 4 — Privacidade e segurança (transversal, pré-requisito de saída de dados)

- [ ] **T4.1** Implementar o **guardião de privacidade**: nenhuma saída de rede sem autorização explícita. — *P1, RF-12, A2*
- [ ] **T4.2** Implementar registro/auditoria de toda saída de dados para fora da máquina. — *RF-12, RNF-07*
- [ ] **T4.3** Implementar sanitização de todo conteúdo externo antes de uso/render. — *RNF-05, caso extremo*
- [ ] **T4.4** UI de controle: ver, autorizar e revogar integrações e saídas. — *RF-11, A3*

## Fase 5 — Integrações externas (opt-in)

- [ ] **T5.1** Definir interface de conector externo plugável atrás do guardião. — *RF-10, P6*
- [ ] **T5.2** Implementar conectores para ChatGPT, Gemini e DeepSeek. — *RF-10, F1*
- [ ] **T5.3** Garantir pré-visualização/permissão do conteúdo antes do envio externo. — *RF-11, A3*
- [ ] **T5.4** Garantir que revogar um conector interrompe chamadas subsequentes. — *Caso extremo*

## Fase 6 — IDE de código

- [ ] **T6.1** Integrar editor de código na UI. — *RF-05, C1*
- [ ] **T6.2** Implementar geração, revisão, depuração e refatoração com IA **local**. — *RF-05, C1, P2*

## Fase 7 — Rede peer-to-peer

- [ ] **T7.1** Implementar descoberta e conexão entre nós (libp2p), com transporte cifrado. — *RF-08, RNF-05*
- [ ] **T7.2** Implementar compartilhamento de capacidade com **consentimento explícito** do nó que cede. — *RF-09, E1*
- [ ] **T7.3** Implementar consumo de capacidade remota com degradação graciosa se a rede cair. — *E2, caso extremo*
- [ ] **T7.4** Implementar mecanismos de segurança/limites para uso de recursos por nós remotos. — *RNF-05, E1*

## Fase 8 — Testes, hardening e documentação

- [ ] **T8.1** Testes unitários e de integração das funções de núcleo, conhecimento e privacidade. — *RNF-08*
- [ ] **T8.2** Teste de aceitação contra os critérios de `spec.md`. — *Spec*
- [ ] **T8.3** Documentação de usuário e guia de onboarding de contribuidores. — *P5, RNF-08*
- [ ] **T8.4** Revisão de segurança/privacidade (verificação final contra a constituição). — *P1, RNF-05*

---

## Ponto de verificação (antes de implementar)

- [ ] Toda história de usuário de `spec.md` está coberta por ao menos uma tarefa?
- [ ] Todo requisito funcional (RF-01…RF-12) aparece na coluna *Requisito* de alguma tarefa?
- [ ] Nenhuma tarefa habilita saída de dados antes da Fase 4 (guardião de privacidade)?
- [ ] As perguntas em aberto do plano foram resolvidas (T1.1)?

> Sugestão: rodar `/speckit.analyze` para verificar consistência entre spec ↔ plan ↔ tasks antes de `/speckit.implement`.

---

*Lista viva. Descobertas durante a implementação retornam a `spec.md`/`plan.md` antes de virar código.*
