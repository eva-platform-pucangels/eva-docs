# Plano Técnico — Projeto EVA

> **Artefato SDD — `plan.md`**
> Define **como** a EVA será construída: arquitetura, pilha de tecnologia, sequência de implementação e verificação contra a constituição.
> Decisões aqui derivam de [`spec.md`](spec.md) e devem respeitar [`constitution.md`](constitution.md). Mudança de tecnologia altera este plano, **não** a especificação.
>
> Versão 1.0 (proposta para validação na reunião de kickoff) · Comitê de IA · PUC Angels · Junho de 2026

---

> ⚠️ **Status:** este plano é uma **proposta inicial**. As escolhas de tecnologia abaixo são candidatas, fundamentadas nos princípios do projeto, e devem ser ratificadas ou ajustadas pelo time fundador. Itens em aberto estão na seção [Premissas e perguntas em aberto](#premissas-e-perguntas-em-aberto).

## Visão geral da arquitetura

A EVA é um **aplicativo desktop modular** que orquestra um runtime de IA local. A arquitetura separa quatro camadas:

1. **Camada de apresentação (UI):** interface desktop unificada que expõe as três frentes (assistente, IDE, conhecimento).
2. **Camada de orquestração (núcleo EVA):** roteia cada requisição entre execução local, rede P2P ou serviço externo, aplicando a política de privacidade (opt-in) como guardião central. É aqui que vive a regra "nada sai sem autorização".
3. **Camada de capacidades:**
   - **Runtime de inferência local** (modelos open source on-device).
   - **Armazenamento local** (contexto, memória, base de conhecimento, índice vetorial).
   - **Cliente P2P** (descoberta, conexão e compartilhamento de capacidade).
   - **Conectores externos** (ChatGPT/Gemini/DeepSeek), atrás do guardião de privacidade.
4. **Camada de dados (local):** banco local + índice de embeddings, sempre na máquina do usuário.

```
┌──────────────────────────────────────────────┐
│            UI Desktop (Mac / Windows)          │
│     Assistente  ·  IDE de código  ·  Conhec.   │
├──────────────────────────────────────────────┤
│        Núcleo de Orquestração da EVA           │
│   (roteamento + GUARDIÃO DE PRIVACIDADE opt-in)│
├───────────┬───────────┬───────────┬───────────┤
│ Inferência│ Armazenam.│ Cliente   │ Conectores│
│  local    │  local +  │  P2P      │ externos  │
│ (LLM)     │  vetorial │ (cifrado) │ (opt-in)  │
├───────────┴───────────┴───────────┴───────────┤
│       Dados locais (DB + índice vetorial)      │
└──────────────────────────────────────────────┘
```

Princípio arquitetural central: **local-first**. A rede P2P e os conectores externos são *plugins* opcionais por trás do núcleo; sua ausência nunca quebra o funcionamento local (constituição P2).

## Pilha de tecnologia e principais decisões (propostas)

| Área | Decisão proposta | Justificativa | Alinhamento |
|------|------------------|---------------|-------------|
| Shell desktop | **Tauri** (ou Electron como alternativa) | Multiplataforma Mac/Windows, leve, e Tauri tem footprint menor; ambos open source | RNF-04, P3, P4 |
| Runtime de inferência local | **llama.cpp / Ollama** com modelos GGUF open source | Inferência on-device eficiente em hardware de consumidor; ecossistema open source maduro | RF-01, P2, P3 |
| Modelos | Modelos open source quantizados (ex.: famílias Llama/Mistral/Qwen) com licença compatível | Custo zero, execução local, auditável; modelo concreto a homologar | P3, P4 |
| Armazenamento local | **SQLite** para dados estruturados | Embarcado, sem servidor, zero custo, multiplataforma | RF-02, P2, P4 |
| Índice vetorial | **sqlite-vec / LanceDB** (embeddings locais) | Busca semântica local sem serviço externo | RF-06, RF-07, P1 |
| Rede P2P | **libp2p** com transporte cifrado | Descoberta/conexão descentralizada, sem servidor central, comunicação cifrada | RF-08, RF-09, RNF-05 |
| Conectores externos | Adaptadores plugáveis atrás do guardião de privacidade | Interoperabilidade opt-in mantendo controle do usuário | RF-10, RF-11, P6 |
| Sanitização | Sanitização de todo conteúdo externo antes de uso/render | Trata entradas de terceiros como não confiáveis | RNF-05 |
| Licença | Licença open source permissiva (ex.: MIT/Apache-2.0) | Colaboração e auditoria pela comunidade | P3 |

> A escolha **Tauri vs Electron** e a **família de modelos** são as duas decisões mais relevantes a fechar no kickoff, pois afetam linguagem do núcleo e requisitos de hardware.

## Mapeamento módulos → arquitetura

| Módulo (spec) | Componente arquitetural |
|---------------|--------------------------|
| M1 — Núcleo do agente local | Runtime de inferência + Armazenamento local + Orquestração |
| M2 — Assistente pessoal | UI (chat) + Orquestração + Memória local |
| M3 — IDE de código | UI (editor) + Orquestração + Runtime local |
| M4 — Motor de conhecimento | Ingestão/indexação + Índice vetorial + Busca semântica |
| M5 — Rede peer-to-peer | Cliente P2P (libp2p) + camada de consentimento |
| M6 — Integrações externas | Conectores externos atrás do guardião |
| M7 — Privacidade e segurança | Guardião de privacidade (transversal) + sanitização + auditoria |

## Sequência de implementação

A ordem respeita as dependências (fundação antes do que depende dela) e a priorização local-first:

1. **Fundação** — estrutura do projeto, shell desktop, esquema de dados local (M1 parcial).
2. **Núcleo local + Assistente** — runtime de inferência local e chat funcional offline (M1, M2). *Entrega o valor mínimo demonstrável.*
3. **Motor de conhecimento** — ingestão, indexação e busca semântica local (M4).
4. **Privacidade/segurança transversal** — guardião opt-in e auditoria de saída, sanitização (M7). *Pré-requisito antes de qualquer saída de dados.*
5. **Integrações externas (opt-in)** — conectores ChatGPT/Gemini/DeepSeek atrás do guardião (M6).
6. **IDE de código** — assistência de código local (M3).
7. **Rede peer-to-peer** — descoberta, conexão, compartilhamento com consentimento (M5).
8. **Testes e documentação** — testes, hardening e onboarding de contribuidores (transversal).

> Nota: M7 (guardião de privacidade) precede M6/M5 deliberadamente — nenhum caminho de saída de dados é habilitado antes da camada que o controla existir (constituição P1).

## Verificação da constituição

| Princípio | Como o plano atende |
|-----------|---------------------|
| P1 — Privacidade por design | Guardião de privacidade central; saída só via opt-in; auditoria de saída (M7) implementada antes das integrações |
| P2 — Local-first | Núcleo offline (inferência + dados locais); P2P e externos são plugins opcionais |
| P3 — Open source | Stack 100% open source; licença permissiva; sem componentes proprietários de núcleo |
| P4 — Custo zero | Tauri/Electron, llama.cpp/Ollama, SQLite, libp2p — todos sem custo de operação |
| P5 — Construção comunitária | Arquitetura modular (M1–M7) e onboarding documentado facilitam contribuição |
| P6 — Interoperabilidade | Conectores externos plugáveis; usuário escolhe o que delegar |

✅ Nenhuma decisão proposta viola a constituição. Riscos de viabilidade técnica são tratados via arquitetura modular (delegação P2P/externa opt-in para cargas pesadas).

## Premissas e perguntas em aberto

**Premissas (do documento base):**
- A comunidade colaborará no desenvolvimento e na adoção.
- Hardware de consumidor atual (notebooks Mac/Windows) é suficiente para modelos locais úteis.
- Há modelos open source adequados aos casos de uso previstos.

**Perguntas em aberto (decidir no kickoff / `/clarify`):**
1. **Shell desktop:** Tauri (Rust no núcleo) ou Electron (Node)? Impacta linguagem e contribuição.
2. **Família de modelos homologada** para o MVP e requisitos mínimos de hardware.
3. **Runtime:** Ollama (mais simples de embarcar) vs llama.cpp direto (mais controle)?
4. **Índice vetorial:** sqlite-vec (unifica com o SQLite) vs LanceDB?
5. **Modelo de consentimento/segurança da rede P2P** — escopo do MVP de E1/E2.
6. **Estratégia de embeddings locais** (qual modelo de embedding e custo de indexação).

---

*Plano vivo. Trocas de tecnologia atualizam este documento; requisitos de produto permanecem em `spec.md`.*
