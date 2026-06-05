# Doutrina Operante — Base de Evidências (datada)

> Receitas da pesquisa que sustenta a doutrina. Campo move rápido: **reavalie a cada ~trimestre**
> e atualize datas. Última revisão: **2026-06-04**. Preferimos fontes primárias e recentes;
> sinalizamos o que é consolidado vs. contestado.

## Fontes primárias (alta confiança)
- **Anthropic — "Effective context engineering for AI agents"** (2025-09-29). Define context
  engineering; "context rot"; orçamento de atenção finito; menor conjunto de tokens de alto sinal;
  just-in-time retrieval; compaction; structured note-taking; subagentes. → Princípios 1, 9.
- **Anthropic — "Effective harnesses for long-running agents"** (2025-11-26). Sessões como turnos;
  agente inicializador vs. agente de execução; arquivos de progresso + git como memória; protocolo
  de re-entrada; verificação ponta-a-ponta. → Princípios 9, 6; design de `state/`.
- **Anthropic — Claude Code best practices** (docs, code.claude.com). Explore→plan→code→commit;
  "dê ao Claude uma verificação que ele roda"; `CLAUDE.md` enxuto e podado; skills sob demanda;
  hooks determinísticos; subagentes p/ investigação e revisão adversarial; `/clear`. → Princípios 2, 6, 1.
- **Anthropic — "How we built our multi-agent research system"**. Orquestrador + subagentes em
  paralelo, cada um com contexto próprio e tarefa autocontida; síntese + passe de citação. → Princípio 10.
- **GitHub — Spec Kit** (anúncio 2025-09-02) e **github/spec-kit** (repo). Spec-Driven Development:
  `Spec → Plan → Tasks → Implement`; a spec como artefato primário. → Princípio 5.
- **agents.md / AGENTS.md** — padrão aberto formalizado em 2025-08 (OpenAI, Google, Cursor,
  Factory, Sourcegraph); adotado por 60k+ repos; sob a Agentic AI Foundation / Linux Foundation.
  "README para máquinas". → design de `AGENTS.md`.
- **John Ousterhout — "A Philosophy of Software Design"**. Deep vs. shallow modules; complexidade;
  encapsular complexidade atrás de interfaces pequenas. → Princípio 7 (e a skill `improve-codebase-architecture`).

## Vozes independentes (corroboração / ceticismo saudável)
- **Simon Willison — "Designing agentic loops"** (2025-09-30) e "An LLM agent runs tools in a loop
  to achieve a goal". Desenhar o loop e as ferramentas é a nova habilidade; o agente exercita o
  próprio código. → Princípio 6.
- **Birgitta Böckeler / Thoughtworks** (QCon London 2025; podcasts "AI-assisted coding" e "Context
  engineering: tackling legacy systems"). Ganhos medidos **modestos** (~8% relatado) e dependentes
  de prática; "curb the enthusiasts, encourage the skeptics"; contexto é crucial. → Princípio 10 e a seção anti-hype.
- **Mike Mason — "AI Coding Agents in 2026: Coherence Through Orchestration, Not Autonomy"**
  (2026-01). → Princípio 10.
- **Modernização de legado com IA** (Augment Code; isaqb.org "AI Agents Don't Modernize Legacy Code
  on Their Own"; CodeScene; createq). Characterization tests como rede de segurança; mapeamento de
  dependências; passos reversíveis; Strangler Fig; **supervisão humana obrigatória**. → Princípios 3, 4, 10.

## Pesquisa acadêmica / panorama (contexto, menor peso)
- arXiv **2510.21413** — "Context Engineering for AI Agents in Open-Source Software" (2025-10).
- arXiv **2602.14690** — "Configuring Agentic AI Coding Tools: An Exploratory Study" (2026-02):
  arquivos de contexto dominam a configuração; AGENTS.md como padrão interoperável; ainda **sem
  estrutura de conteúdo consolidada** (variação descritiva/prescritiva/proibitiva).
- Visual Studio Magazine (2026-05-12): Spec Kit em ascensão como "antídoto ao vibe coding".

## Consolidado vs. contestado
- **Consolidado (battle-tested):** context engineering como disciplina; arquivos de contexto
  (CLAUDE.md/AGENTS.md); explore→plan→code→commit; loop de verificação com testes; characterization
  tests antes de refatorar legado; commits minúsculos; subagentes p/ isolar contexto e revisão;
  spec-driven para trabalho não-trivial; deep modules.
- **Contestado / a tratar com cautela:** "times autônomos de IA" substituindo engenheiros;
  números de produtividade inflados; ideia de que agentes modernizam legado sozinhos; padrão de
  *conteúdo* ideal para arquivos de contexto (ainda em aberto). Trate como hipótese, não fato.

## Como atualizar esta base
1. Refaça as buscas-chave (context engineering, agentic coding, spec-driven, AI refactoring legado,
   harnesses long-running) filtrando por data recente.
2. Prefira fontes primárias (engenharia da Anthropic/OpenAI/Google, repos oficiais, autores
   reconhecidos). Registre **data** de cada afirmação corrente.
3. Se um princípio em `00-principles.md` perder sustentação, abra um ADR na própria bancada
   explicando a mudança antes de reescrever a doutrina.
