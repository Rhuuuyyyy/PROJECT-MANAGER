# Workbench — Engenharia de Software Aumentada por IA

Você (Claude Code) está operando uma **bancada (workbench) reutilizável** cujo único propósito é
**melhorar, reestruturar e organizar um projeto de software já existente**, com qualidade de
engenheiro principal. Este diretório é a bancada. O projeto-alvo é montado em `workspace/`.
A bancada é **stack-agnóstica**: nada aqui presume linguagem, framework ou domínio.

## ⛳ Primeira ação em TODA sessão (re-entrância — não pule)
1. Leia `state/STATE.md`. Ele declara a **fase atual** e a **próxima ação única**.
2. Se o STATE disser *"nenhum engajamento ativo"*, leia `START-HERE.md` por completo e conduza o
   onboarding (Fase 0 → 1) com o usuário.
3. Só depois disso comece a executar. Não improvise fora do que o STATE indica.

## Como trabalhamos (resumo — doutrina completa em `doctrine/`)
- **Contexto é o recurso escasso.** Mantenha o contexto enxuto; use subagentes p/ exploração; `/clear` entre fases. → `doctrine/00-principles.md`
- **Entender antes de mudar.** Explore → planeje → implemente → verifique. Use plan mode.
- **Nunca refatore sem rede de segurança.** Characterization tests fixam o comportamento atual *antes* de qualquer mudança. Passos minúsculos, reversíveis, sempre verdes.
- **Toda mudança precisa de uma verificação que VOCÊ mesmo roda** (teste/build/lint/diff). "Parece pronto" não é pronto.
- **Especifique antes de trabalho significativo** e **registre o porquê** (ADRs) e o domínio (`CONTEXT.md`).
- O fluxo completo por fases, com os gates humanos, está em `doctrine/01-workflow.md`.

## Skills desta bancada (use-as; carregam sob demanda via `/<nome>` ou automaticamente)
`context-engineering` · `grill-with-docs` · `improve-codebase-architecture` ·
`spec-driven-development` · `request-refactor-plan` · `incremental-implementation` ·
`test-driven-development` · `documentation-and-adrs`
Nativas úteis: `init`, `update-config`, `code-review`, `simplify`, `verify`, `run`, `find-skills`.
O mapeamento "qual skill em qual fase" está em `doctrine/01-workflow.md`.

## Limites (guardrails)
- **NÃO** modifique nada dentro de `workspace/` sem um `state/IMPROVEMENT-CHARTER.md` aprovado pelo usuário (Fase 1). Antes disso, só leitura/análise.
- **Artefatos duráveis do projeto** (`CONTEXT.md`, `docs/adr/`, `SPEC.md`, `CLAUDE.md` do projeto) são escritos **DENTRO de `workspace/`** para viajarem com o repositório. **Estado e diário da bancada** ficam em `state/` (fora do repo do usuário).
- **Atualize `state/STATE.md` e `state/JOURNAL.md` ao fim de cada fase** — é isso que torna a próxima sessão fria capaz de continuar.
