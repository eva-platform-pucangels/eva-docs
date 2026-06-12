---
title: Documento Base
nav_order: 3
---

# Projeto EVA — Documento Base

**IA Local, Privada e Open Source**
Comitê de IA · PUC Angels
Versão 1.0 · Junho de 2026

> Este documento descreve o Projeto EVA em nível conceitual e funcional, servindo como insumo para a elaboração posterior de um SDD (Software Design Document), onde serão detalhadas arquitetura, componentes, interfaces e decisões técnicas.

---

## 1. Visão Geral

O Projeto EVA é uma iniciativa do Comitê de IA da PUC Angels para desenvolver um **agente de inteligência artificial que roda diretamente no computador do usuário** (Mac e Windows), com **privacidade por design**, distribuído como **software open source** e construído de forma colaborativa pela comunidade.

A EVA nasce de uma constatação simples: hoje, o acesso a IA de qualidade é quase sempre "alugado". As ferramentas dominantes dependem de infraestrutura em nuvem de grandes provedores, o que implica custos recorrentes, exposição de dados pessoais e de negócio a terceiros, e dependência de decisões comerciais que o usuário não controla. A EVA inverte essa lógica: a inteligência roda na máquina do usuário, os dados permanecem com ele, e a evolução do produto é guiada pela própria comunidade que o utiliza.

## 2. Contexto e Problema

### 2.1 Visão do problema

Acessibilidade limitada a soluções de inteligência artificial privadas, personalizadas e independentes de grandes provedores.

### 2.2 Descrição do problema

Usuários individuais e membros da rede PUC Angels enfrentam barreiras significativas para acessar soluções de IA que sejam verdadeiramente privadas, personalizadas e independentes dos grandes provedores de tecnologia. A maioria das ferramentas atuais depende de infraestrutura em nuvem, o que gera três consequências centrais:

1. **Custos recorrentes** — assinaturas e cobrança por uso criam uma barreira financeira contínua à adoção de IA.
2. **Riscos de privacidade** — dados pessoais e de negócio trafegam por servidores de terceiros, sem controle real do usuário sobre armazenamento, uso e retenção.
3. **Dependência de terceiros** — mudanças de preço, política ou disponibilidade dos provedores afetam diretamente quem constrói rotinas e processos sobre essas ferramentas.

### 2.3 Sintomas observados

Dificuldade de adoção de IA na comunidade devido a custos elevados, preocupações com privacidade e falta de controle sobre os dados pessoais.

## 3. Proposta de Solução

A EVA é um **agente de IA local** com três frentes funcionais integradas em um único produto, mais uma camada de rede comunitária:

### 3.1 Assistente pessoal

Apoio ao dia a dia do usuário: escrita, análise, organização e automação de tarefas. O diferencial é que todo o contexto acumulado (preferências, histórico, documentos de referência) permanece exclusivamente na máquina do usuário.

### 3.2 IDE de código

Ambiente de desenvolvimento com IA integrada para criar, revisar, depurar e refatorar código localmente, sem que o código-fonte do usuário precise sair de sua máquina.

### 3.3 Motor de conhecimento

Capacidade de indexar e consultar documentos, anotações e bases de conhecimento pessoais do usuário, oferecendo busca semântica e respostas contextualizadas de forma privada e personalizada.

### 3.4 Rede peer-to-peer

Camada de rede que conecta membros da comunidade entre si, permitindo o **compartilhamento de capacidade computacional**. Usuários com hardware mais potente podem ceder capacidade ociosa, ampliando o poder de processamento disponível para a comunidade como um todo, sem intermediação de servidores centrais.

### 3.5 Integração com o ecossistema existente

A EVA não exige ruptura com as ferramentas que o usuário já utiliza. Ela se integra a serviços de IA existentes — como ChatGPT, Gemini e DeepSeek — funcionando como camada de orquestração: o usuário decide, caso a caso, o que roda localmente e o que pode ser delegado a serviços externos.

## 4. Princípios de Design

Estes princípios são inegociáveis e devem orientar todas as decisões técnicas no SDD:

1. **Privacidade por design** — nenhum dado do usuário sai da máquina sem decisão explícita dele. Execução local é o padrão; uso de serviços externos é opt-in e transparente.
2. **Execução local em primeiro lugar** — o núcleo da EVA deve funcionar de forma completa sem conexão com a internet, em hardware de consumidor comum (Mac e Windows).
3. **Open source** — código aberto, repositório público, licença permissiva à colaboração. Qualquer membro pode contribuir, revisar e auditar o código.
4. **Construção comunitária** — o roadmap e a evolução do produto são guiados pela comunidade PUC Angels, com desenvolvimento iterativo e validação de valor desde as primeiras versões.
5. **Custo zero de operação para o usuário** — sem assinaturas, sem cobrança por uso, sem dependência obrigatória de serviços pagos.
6. **Interoperabilidade** — integração com ferramentas de IA existentes em vez de competição frontal; o usuário mantém liberdade de escolha.

## 5. Público-Alvo e Mercado

| Segmento | Tamanho estimado | Horizonte |
|---|---|---|
| Membros ativos da rede PUC Angels | ~500 membros | Base atual |
| Adoção estimada no 1º ano | ~350 usuários (70% da rede) | 12 meses |
| Expansão para comunidades acadêmicas e tecnológicas locais | até 2.000 usuários | 24 meses |

O perfil do usuário inicial é o membro da rede PUC Angels: investidores-anjo, empreendedores e profissionais tecnicamente engajados, com interesse em IA, sensibilidade a questões de privacidade e disposição para adotar (e ajudar a construir) ferramentas em estágio inicial.

O volume de uso esperado é de **dezenas de interações diárias por usuário**, caracterizando a EVA como ferramenta de uso cotidiano e alta recorrência.

## 6. Objetivos e Métricas

**KPI principal:** quantidade de usuários que adotam a EVA e a utilizam regularmente.

**Meta:** engajar pelo menos **70% da rede PUC Angels** no uso da EVA nos primeiros 12 meses após o lançamento.

Métricas de apoio sugeridas para detalhamento futuro: usuários ativos semanais (WAU), interações por usuário/dia, retenção em 30/60/90 dias, número de contribuidores ativos no repositório open source e nós ativos na rede peer-to-peer.

## 7. Estratégia de Criação de Valor

**Alavancas:**

- Redução de custos operacionais com IA para os membros da rede
- Aumento da adoção tecnológica na comunidade
- Incentivo à inovação colaborativa

**Premissa-chave:** a comunidade PUC Angels está interessada e disposta a colaborar no desenvolvimento e na adoção da EVA.

## 8. Modelo de Desenvolvimento

O projeto será conduzido com **esforço voluntário do Comitê de IA da PUC Angels**, sem necessidade de investimento financeiro (R$ 0 para MVP e escala). Os pilares do modelo são:

1. **Voluntariado** — tempo e talento dos membros do Comitê de IA e da rede ampliada.
2. **Open source** — repositório aberto com contribuição, revisão e evolução colaborativa do código.
3. **Coordenação ativa** — grupo de desenvolvimento no WhatsApp já em operação, com cadência semanal de comunicação para alinhamento, recrutamento de colaboradores e acompanhamento de progresso.

## 9. Riscos e Mitigações

| Risco | Descrição | Mitigação proposta |
|---|---|---|
| Baixa adesão | Membros da comunidade não adotam ou não colaboram com o projeto | Desenvolvimento aberto e iterativo com a própria comunidade, validando valor desde as primeiras versões; comunicação semanal ativa |
| Viabilidade técnica | Dificuldade de garantir execução local eficiente e sustentável em hardware de consumidor | Priorizar modelos otimizados para execução local; arquitetura modular que permita delegar cargas pesadas via rede P2P ou serviços externos (opt-in) |
| Sustentabilidade do voluntariado | Dependência de tempo voluntário pode gerar descontinuidade | Documentação robusta, onboarding facilitado de novos contribuidores e governança comunitária do repositório |

## 10. Escopo Funcional de Alto Nível (insumo para o SDD)

A lista abaixo organiza as capacidades da EVA em módulos candidatos, a serem detalhados no SDD:

### M1 — Núcleo do agente local
- Execução de modelos de IA localmente (inferência on-device)
- Gerenciamento de contexto e memória persistente local
- Suporte a Mac e Windows

### M2 — Assistente pessoal
- Interface conversacional (chat)
- Tarefas de escrita, análise e organização
- Automação de tarefas do usuário

### M3 — IDE de código
- Edição de código com assistência de IA
- Geração, revisão e depuração de código local

### M4 — Motor de conhecimento
- Ingestão e indexação de documentos locais
- Busca semântica e respostas com base na base pessoal do usuário

### M5 — Rede peer-to-peer
- Descoberta e conexão entre nós da comunidade
- Compartilhamento de capacidade computacional
- Mecanismos de segurança e consentimento para uso de recursos

### M6 — Integrações externas (opt-in)
- Conectores para ChatGPT, Gemini e DeepSeek
- Controle transparente do usuário sobre o que é enviado a serviços externos

### M7 — Privacidade e segurança (transversal)
- Dados em repouso e em trânsito sob controle do usuário
- Auditabilidade (código aberto)
- Política de "nada sai da máquina sem opt-in explícito"

## 11. Premissas e Restrições

**Premissas:**
- A comunidade PUC Angels colaborará no desenvolvimento e na adoção
- Hardware de consumidor atual (notebooks Mac/Windows) é suficiente para executar modelos locais úteis
- Há modelos open source disponíveis e adequados para os casos de uso previstos

**Restrições:**
- Orçamento: R$ 0 (esforço exclusivamente voluntário)
- Plataformas iniciais: macOS e Windows
- Licenciamento: compatível com modelo open source do projeto

## 12. Próximos Passos

1. **Reunião de kickoff** — definir objetivos, organização do time e primeiros passos técnicos
2. Elaboração do **SDD (Software Design Document)** a partir deste documento
3. Definição do MVP e priorização dos módulos (M1–M7)
4. Estruturação do repositório open source e do fluxo de contribuição
5. Continuidade do engajamento da comunidade via grupo de desenvolvimento no WhatsApp

---

*Documento elaborado pelo Comitê de IA da PUC Angels como base conceitual do Projeto EVA. Sujeito a revisão colaborativa pela comunidade.*