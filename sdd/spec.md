---
title: Especificação (spec)
parent: SDD
nav_order: 2
---

# Especificação Funcional — Projeto EVA

> **Artefato SDD — `spec.md`**
> Define **o que** a EVA deve fazer (e por quê), na perspectiva do usuário. Não define tecnologia nem arquitetura — isso é responsabilidade de [`plan.md`](plan.md).
> Toda funcionalidade implementada deve rastrear até um requisito desta especificação.
>
> Versão 1.0 · Comitê de IA · PUC Angels · Junho de 2026

---

## Resumo

A EVA é um **agente de inteligência artificial local** para macOS e Windows que permite ao usuário ter sua própria IA — privada, personalizada e de custo zero. Em um único produto, a EVA funciona como **assistente pessoal**, **IDE de código** e **motor de conhecimento**, com todo o contexto e os dados do usuário persistidos exclusivamente em sua máquina. Quando autorizado pelo usuário, a EVA pode ampliar sua capacidade conectando-se a uma **rede peer-to-peer** da comunidade ou delegando tarefas a **serviços de IA externos** (ChatGPT, Gemini, DeepSeek).

## Escopo

### Dentro do escopo (visão de produto)
Assistente pessoal, IDE de código, motor de conhecimento, rede P2P de compartilhamento de capacidade, integrações externas opt-in e a camada transversal de privacidade/segurança.

### Fora do escopo (no MVP)
Versão mobile, versão web hospedada, modelo de monetização, suporte oficial a Linux. Estes podem ser reavaliados em versões futuras.

---

## Histórias de usuário

O usuário-alvo é o membro da rede PUC Angels: investidor-anjo, empreendedor ou profissional tecnicamente engajado, sensível a privacidade e disposto a adotar e coconstruir ferramentas em estágio inicial.

### Épico A — Núcleo e privacidade
- **A1.** Como usuário, quero instalar a EVA no meu computador (Mac ou Windows) e usá-la **sem conexão à internet**, para que eu não dependa de servidores de terceiros.
- **A2.** Como usuário, quero ter certeza de que meus dados **não saem da minha máquina** sem que eu autorize explicitamente, para que minha privacidade seja preservada.
- **A3.** Como usuário, quero ver e controlar quando a EVA usa um serviço externo, para que eu decida o que é local e o que é delegado.

### Épico B — Assistente pessoal
- **B1.** Como usuário, quero conversar com a EVA por uma interface de chat para escrever, analisar e organizar conteúdo.
- **B2.** Como usuário, quero que a EVA lembre das minhas preferências e do histórico relevante, para que as respostas fiquem mais personalizadas ao longo do tempo.
- **B3.** Como usuário, quero automatizar tarefas repetitivas do meu dia a dia.

### Épico C — IDE de código
- **C1.** Como desenvolvedor, quero criar, revisar, depurar e refatorar código com assistência de IA **localmente**, para que meu código-fonte não saia da minha máquina.

### Épico D — Motor de conhecimento
- **D1.** Como usuário, quero indexar meus documentos e anotações locais para consultá-los depois.
- **D2.** Como usuário, quero fazer perguntas em linguagem natural e receber respostas contextualizadas na minha base pessoal (busca semântica), de forma privada.

### Épico E — Rede peer-to-peer
- **E1.** Como usuário com hardware potente, quero ceder capacidade ociosa para a comunidade, mediante meu consentimento.
- **E2.** Como usuário com hardware limitado, quero usar capacidade compartilhada por outros nós para executar tarefas mais pesadas.

### Épico F — Integrações externas (opt-in)
- **F1.** Como usuário, quero conectar a EVA a ChatGPT, Gemini ou DeepSeek e escolher, caso a caso, o que delegar a esses serviços.

---

## Critérios de aceitação

Condições observáveis e testáveis para considerar cada capacidade concluída.

### Núcleo e privacidade
- A EVA instala e executa funções essenciais (chat com modelo local) **sem qualquer conexão de rede**.
- Por padrão, nenhuma requisição de saída é feita; qualquer chamada externa é precedida de autorização do usuário e fica registrada/auditável.
- O usuário consegue listar e revogar integrações externas a qualquer momento.

### Assistente pessoal
- O usuário envia uma mensagem e recebe resposta gerada por modelo local.
- O contexto do usuário (preferências, histórico) persiste entre sessões e é armazenado apenas localmente.

### Motor de conhecimento
- O usuário adiciona um documento local e ele passa a ser pesquisável.
- Uma pergunta em linguagem natural retorna resposta com referência aos trechos da base pessoal utilizados.
- Documentos com formato não suportado exibem mensagem de erro clara.

### Rede peer-to-peer
- O compartilhamento de capacidade só ocorre após consentimento explícito do nó que cede recursos.
- A comunicação entre nós é cifrada; nenhum dado de tarefa trafega em claro.
- Se a rede estiver indisponível, a EVA continua operando localmente sem falhar.

### Integrações externas
- Conectar um serviço externo exige uma ação explícita de configuração (credencial/opt-in).
- Antes de enviar qualquer conteúdo a um serviço externo, o usuário vê o que será enviado (ou configurou previamente essa permissão).

---

## Requisitos funcionais

| ID | Módulo | Requisito |
|----|--------|-----------|
| RF-01 | Núcleo (M1) | Executar inferência de modelos de IA localmente (on-device) em macOS e Windows. |
| RF-02 | Núcleo (M1) | Gerenciar contexto e memória persistente local do usuário. |
| RF-03 | Assistente (M2) | Prover interface conversacional (chat) para escrita, análise e organização. |
| RF-04 | Assistente (M2) | Permitir automação de tarefas definidas pelo usuário. |
| RF-05 | IDE (M3) | Editar, gerar, revisar e depurar código com assistência de IA local. |
| RF-06 | Conhecimento (M4) | Ingerir e indexar documentos locais. |
| RF-07 | Conhecimento (M4) | Realizar busca semântica e responder com base na base pessoal do usuário. |
| RF-08 | Rede P2P (M5) | Descobrir e conectar nós da comunidade. |
| RF-09 | Rede P2P (M5) | Compartilhar capacidade computacional entre nós, com consentimento. |
| RF-10 | Integrações (M6) | Conectar a ChatGPT, Gemini e DeepSeek como camada de orquestração opt-in. |
| RF-11 | Integrações (M6) | Dar ao usuário controle transparente sobre o que é enviado a serviços externos. |
| RF-12 | Privacidade (M7) | Registrar e tornar auditável toda saída de dados para fora da máquina. |

## Requisitos não funcionais

| ID | Atributo | Requisito |
|----|----------|-----------|
| RNF-01 | Privacidade | Execução local é padrão; saída de dados apenas via opt-in explícito (ver constituição P1). |
| RNF-02 | Disponibilidade offline | Núcleo funcional 100% offline em hardware de consumidor comum. |
| RNF-03 | Desempenho | Suportar dezenas de interações diárias por usuário com latência aceitável para uso cotidiano. |
| RNF-04 | Portabilidade | Suporte a macOS e Windows desde o MVP. |
| RNF-05 | Segurança | Conteúdo externo sanitizado; comunicação P2P cifrada em trânsito. |
| RNF-06 | Custo | Caminho padrão de uso gratuito de ponta a ponta (constituição P4). |
| RNF-07 | Auditabilidade | Código aberto e revisável pela comunidade (constituição P3). |
| RNF-08 | Manutenibilidade | Arquitetura modular (M1–M7) com onboarding documentado para contribuidores. |

## Casos extremos

- **Sem internet:** todas as funções de núcleo (chat, conhecimento local) continuam disponíveis; funções que dependem de rede/externo degradam graciosamente com aviso claro.
- **Hardware insuficiente:** se o dispositivo não comporta o modelo local escolhido, a EVA sugere um modelo menor ou delegação P2P/externa (opt-in), sem travar.
- **URL/feed/documento inválido ou corrompido:** exibir mensagem de erro clara, sem quebrar a sessão.
- **Conteúdo externo malicioso:** entradas vindas de IAs de terceiros ou documentos são tratadas como não confiáveis e sanitizadas antes de uso/renderização.
- **Nó P2P indisponível ou desonesto:** falha de um nó não compromete a tarefa local; mecanismos de consentimento e segurança limitam o que um nó remoto pode fazer.
- **Revogação de integração externa:** ao revogar, nenhuma chamada subsequente é feita ao serviço removido.

---

## Perguntas em aberto (para `/clarify`)

1. Qual o **intervalo de retenção/limpeza** da memória de contexto local e o usuário pode configurá-lo?
2. Quais **formatos de documento** o motor de conhecimento deve suportar no MVP?
3. Há **limite de tamanho** de base de conhecimento para o MVP?
4. O compartilhamento P2P terá algum modelo de **reputação/crédito** entre nós?
5. Quais **modelos open source** específicos serão homologados para o MVP (depende do plano)?

---

*Especificação viva. Mudanças de requisito devem ser refletidas aqui antes de propagarem para o plano e as tarefas.*
