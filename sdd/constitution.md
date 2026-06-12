---
title: Constituição
parent: SDD
nav_order: 1
---

# Constituição do Projeto EVA

> **Artefato SDD — `constitution.md`**
> Princípios orientadores, restrições e requisitos não negociáveis do projeto.
> Este documento tem precedência sobre `spec.md`, `plan.md` e `tasks.md`: toda decisão de especificação, design ou implementação deve ser verificada contra a constituição.
>
> Versão 1.0 · Comitê de IA · PUC Angels · Junho de 2026

---

## Propósito

A EVA existe para **democratizar o acesso à inteligência artificial** entre os membros da rede PUC Angels, entregando uma IA que **pertence ao usuário** — local, privada e de custo zero. Toda decisão técnica deve servir a esse propósito.

## Princípios não negociáveis

Estes princípios são herdados diretamente do documento base e **não podem ser violados** por nenhum plano ou implementação. Quando houver conflito entre um princípio e uma conveniência técnica, o princípio vence.

### P1 — Privacidade por design
Nenhum dado do usuário sai da máquina sem decisão explícita dele. A execução local é o padrão; qualquer uso de serviço externo é **opt-in, transparente e auditável**. Dados em repouso e em trânsito permanecem sob controle do usuário.

### P2 — Execução local em primeiro lugar
O núcleo da EVA deve funcionar de forma **completa e offline**, em hardware de consumidor comum (macOS e Windows). Conectividade com a internet ou com a rede P2P é um aprimoramento, nunca um requisito para o funcionamento básico.

### P3 — Open source e auditável
Código aberto, repositório público e licença permissiva à colaboração. Qualquer membro pode contribuir, revisar e auditar. Não são admitidos componentes proprietários de núcleo que impeçam a auditoria pela comunidade.

### P4 — Custo zero de operação para o usuário
Sem assinaturas, sem cobrança por uso e sem dependência **obrigatória** de serviços pagos. O caminho padrão de uso da EVA deve ser gratuito de ponta a ponta.

### P5 — Construção comunitária
O roadmap e a evolução são guiados pela comunidade PUC Angels, com desenvolvimento iterativo e validação de valor desde as primeiras versões. Decisões de design priorizam a facilidade de contribuição e o onboarding de novos colaboradores.

### P6 — Interoperabilidade, não competição
A EVA integra-se às ferramentas que o usuário já utiliza (ChatGPT, Gemini, DeepSeek e outras) em vez de competir frontalmente. O usuário mantém liberdade de escolha sobre o que roda localmente e o que é delegado.

## Padrões de tecnologia

- **Plataformas-alvo iniciais:** macOS e Windows (desktop). Suporte a Linux é desejável, mas não obrigatório no MVP.
- **Modelos de IA:** priorizar modelos **open source** e otimizados para inferência on-device. Licenciamento dos modelos deve ser compatível com o modelo open source do projeto.
- **Orçamento de operação:** R$ 0. Nenhuma decisão pode introduzir custo recorrente obrigatório para o projeto ou para o usuário.
- **Arquitetura modular:** o sistema deve permitir delegar cargas pesadas via rede P2P ou serviços externos (opt-in) sem comprometer o funcionamento local.

## Requisitos de segurança e privacidade (transversais)

- "Nada sai da máquina sem opt-in explícito" é regra de produto, não apenas técnica.
- Todo conteúdo externo (ex.: respostas de feeds, páginas, saídas de IAs de terceiros) deve ser tratado como **não confiável** e sanitizado antes de renderização ou execução.
- Compartilhamento de capacidade na rede P2P exige **consentimento explícito** e mecanismos de segurança para uso de recursos.
- Comunicação de rede deve ser cifrada em trânsito.

## Convenções de projeto

- **Documentação viva:** `spec.md`, `plan.md` e `tasks.md` são mantidos sincronizados com a realidade. Descobertas durante a implementação retornam aos artefatos antes de virar código ad hoc.
- **Testabilidade:** requisitos são escritos como critérios observáveis e verificáveis.
- **Onboarding facilitado:** documentação robusta e fluxo de contribuição claro são parte do escopo, não um extra (mitigação de risco do voluntariado).

## Métrica norteadora

**KPI principal:** número de membros da rede que adotam e usam a EVA regularmente.
**Meta de referência:** engajar pelo menos **70% da rede PUC Angels** nos primeiros 12 meses após o lançamento. Decisões de produto que claramente prejudiquem essa meta devem ser reavaliadas.

---

*Constituição sujeita a revisão colaborativa pela comunidade. Alterações exigem registro de versão e comunicação ao grupo de desenvolvimento.*
