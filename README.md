# Projeto EVA

**IA Local, Privada e Open Source**
Comitê de IA · PUC Angels

> E se você tivesse uma IA que é sua — de verdade? Não uma assinatura, não um acesso ao servidor de outra empresa, mas uma inteligência artificial que pertence ao usuário.

O **Projeto EVA** é uma iniciativa open source do Comitê de IA da PUC Angels para democratizar o acesso à inteligência artificial entre os membros da rede. A EVA é um **agente de IA local**, instalado diretamente no computador do usuário (Mac ou Windows), com **privacidade por design** e construído de forma **colaborativa pela comunidade**.

---

## Por que a EVA

Hoje, o acesso a IA de qualidade é quase sempre "alugado". As ferramentas dominantes dependem de infraestrutura em nuvem de grandes provedores, o que implica:

- **Custos recorrentes** — assinaturas e cobrança por uso criam uma barreira financeira contínua.
- **Riscos de privacidade** — dados pessoais e de negócio trafegam por servidores de terceiros, sem controle real do usuário.
- **Dependência de terceiros** — mudanças de preço, política ou disponibilidade afetam diretamente quem constrói sobre essas ferramentas.

A EVA inverte essa lógica: a inteligência roda na máquina do usuário, os dados permanecem com ele, e a evolução do produto é guiada pela própria comunidade.

## Os cinco pilares

1. **Execução local.** A EVA roda na máquina do próprio usuário, sem depender da infraestrutura de terceiros para funcionar.
2. **Privacidade por design.** Os dados do usuário permanecem no seu computador — nunca são enviados para servidores externos sem decisão explícita.
3. **Rede peer-to-peer.** Quando precisa de mais capacidade computacional, a EVA pode se conectar a outros usuários EVA, formando uma rede distribuída e colaborativa.
4. **Integração com o ecossistema existente.** A EVA não substitui as ferramentas que o usuário já usa — integra-se a ChatGPT, Gemini, DeepSeek e outras IAs do mercado.
5. **Multifuncionalidade.** Funciona como **assistente pessoal**, como **IDE de código** e como **motor de conhecimento**, crescendo e se personalizando junto com o usuário.

## O que a EVA faz

| Frente | Descrição |
|---|---|
| **Assistente pessoal** | Apoio ao dia a dia: escrita, análise, organização e automação de tarefas — com todo o contexto mantido localmente. |
| **IDE de código** | Ambiente de desenvolvimento com IA integrada para criar, revisar, depurar e refatorar código sem que o código-fonte saia da máquina. |
| **Motor de conhecimento** | Indexação e consulta de documentos e bases de conhecimento pessoais, com busca semântica privada e contextualizada. |
| **Rede peer-to-peer** | Compartilhamento de capacidade computacional entre membros, sem servidores centrais. |
| **Integrações externas (opt-in)** | Orquestração de serviços de IA existentes, com o usuário decidindo o que roda local e o que é delegado. |

## Princípios de design (inegociáveis)

1. **Privacidade por design** — nenhum dado sai da máquina sem decisão explícita do usuário.
2. **Execução local em primeiro lugar** — o núcleo funciona completo sem internet, em hardware de consumidor comum.
3. **Open source** — repositório público e licença permissiva à colaboração; qualquer membro pode contribuir e auditar.
4. **Construção comunitária** — roadmap e evolução guiados pela comunidade PUC Angels.
5. **Custo zero de operação para o usuário** — sem assinaturas, sem cobrança por uso.
6. **Interoperabilidade** — integração com ferramentas existentes em vez de competição frontal.

## Estado atual (junho/2026)

O projeto está na fase de **mobilização e formação do time fundador**. O grupo de desenvolvimento no WhatsApp foi criado, mensagens de engajamento foram disparadas ao longo da semana, e a **reunião de kickoff** foi convocada para quinta-feira, 11/6, às 19h — cobrindo visão e objetivos, organização do time e frentes de trabalho, e primeiros passos técnicos.

Uma **versão inicial da documentação técnica (SDD)** já foi elaborada como proposta para discussão no kickoff — ver seção [Especificação técnica (SDD)](#especificação-técnica-sdd).

## Especificação técnica (SDD)

A documentação de design da EVA segue a metodologia **Spec-Driven Development (SDD)** do [GitHub Spec Kit](https://learn.microsoft.com/pt-br/training/modules/spec-driven-development-github-spec-kit-greenfield-intro/): **constituição → especificação → plano → tarefas**. Os artefatos estão em [sdd/](sdd/) e são **documentos vivos**, atualizados conforme o projeto evolui.

| Artefato | Responde | Conteúdo |
|---|---|---|
| [constitution.md](sdd/constitution.md) | Quais regras são inegociáveis? | Os 6 princípios não negociáveis, padrões de tecnologia e o KPI norteador |
| [spec.md](sdd/spec.md) | **O quê** e **por quê**? | Histórias de usuário, critérios de aceitação, requisitos funcionais (RF) e não funcionais (RNF), casos extremos |
| [plan.md](sdd/plan.md) | **Como**? | Arquitetura, pilha de tecnologia proposta, mapeamento M1–M7 e sequência de implementação |
| [tasks.md](sdd/tasks.md) | Em **quais passos**? | Tarefas discretas e rastreáveis, organizadas em 8 fases |

> A versão atual é uma **proposta inicial** para o kickoff. As decisões de tecnologia em `plan.md` são candidatas e devem ser ratificadas pelo time fundador. Comece por [sdd/README.md](sdd/README.md).

## Como contribuir

A EVA está sendo construída de forma colaborativa e comunitária. O recrutamento é **deliberadamente inclusivo** — não exige que o participante seja especialista. Há espaço para quem programa, desenha, escreve ou contribui com visão de negócio. O critério é **querer construir**.

- **Open source**: código aberto, permitindo que qualquer pessoa contribua e audite.
- **Coordenação via WhatsApp**: grupo de desenvolvimento ativo com comunicação semanal.

## Próximos passos

1. **Reunião de kickoff** — definir objetivos, organização do time e primeiros passos técnicos.
2. **Revisar e ratificar o SDD** ([sdd/](sdd/)) — fechar as decisões de tecnologia e as perguntas em aberto do [plano](sdd/plan.md).
3. Definição do MVP e priorização dos módulos (M1–M7).
4. Estruturação do repositório de código e do fluxo de contribuição.
5. Continuidade do engajamento da comunidade.

## Documentação

- [Projeto EVA — Resumo](Projeto%20EVA%20Resumo.md) — resumo detalhado do projeto.
- [Projeto EVA — Documento Base](Projeto%20Eva%20Documento%20Base.md) — documento conceitual e funcional completo, insumo para o SDD.
- [SDD — Documentação orientada a especificações](sdd/README.md) — constituição, especificação, plano e tarefas (metodologia GitHub Spec Kit).
- [Apresentação (PPTX)](Projeto_EVA_PUC_angels.pptx) — slides do projeto.

---

*Documentação mantida pelo Comitê de IA da PUC Angels. Sujeita a revisão colaborativa pela comunidade.*
