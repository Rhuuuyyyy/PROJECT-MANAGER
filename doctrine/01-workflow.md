# Doutrina Operante — Fluxo por Fases

> O caminho de ponta a ponta para melhorar um projeto existente. Cada fase: **objetivo →
> skill(s) que conduzem → entradas → saídas → gate → estado a gravar**. 🚦 = exige aprovação do
> usuário antes de avançar. Comece sempre lendo `state/STATE.md` para saber em que fase você está.

> **Ajuste de escopo:** este fluxo é o caminho completo para uma mudança significativa. Para um
> ajuste pequeno e óbvio (typo, rename trivial), o Princípio 5 permite encurtar — vá direto à
> Fase 6→7 com um mini-charter de uma linha. Não burocratize o trivial.

---

## Fase 0 — Intake (ingestão do projeto)
- **Objetivo:** descobrir o projeto montado em `workspace/` sem mudá-lo. Stack-agnóstico.
- **Conduz:** exploração nativa (subagente `Explore`) + `init` (gera `CLAUDE.md` do projeto) + `context-engineering`.
- **Entradas:** projeto montado em `workspace/` (ver `workspace/README.md`).
- **Faça:** detecte linguagem/stack, comandos de build/test/lint, pontos de entrada, mapa de
  módulos, estado de cobertura de testes, áreas de risco, dependências externas. Preencha uma
  cópia de `templates/PROJECT-PROFILE.md` em `state/PROJECT-PROFILE.md`. Gere/auxilie um
  `CLAUDE.md` *do projeto* dentro de `workspace/` (convenções que o agente deve seguir lá).
- **Saídas:** `state/PROJECT-PROFILE.md`; `workspace/<projeto>/CLAUDE.md` (rascunho).
- **Gate:** — (só leitura; sem risco)
- **Grave:** STATE = "Fase 0 concluída; aguardando Charter".

## Fase 1 — Charter (metas do usuário) 🚦
- **Objetivo:** capturar *o que o usuário quer* e *como saberemos que terminou*. É o único insumo
  reservado para esta etapa humana.
- **Conduz:** entrevista (estilo "deixe o agente te entrevistar") + `spec-driven-development` (reframe em critérios de sucesso).
- **Faça:** entreviste o usuário; surface premissas; preencha `state/IMPROVEMENT-CHARTER.md`
  (objetivo, motivação, definition of done testável, restrições/non-negotiables, escopo e
  fora-de-escopo, como o usuário quer revisar).
- **Saídas:** `state/IMPROVEMENT-CHARTER.md` aprovado.
- **Gate:** 🚦 **O usuário aprova o charter.** Sem isso, nada em `workspace/` é modificado.
- **Grave:** STATE = "Charter aprovado; próxima: Domínio & Decisões".

## Fase 2 — Domínio & Decisões
- **Objetivo:** dar linguagem ao domínio e expor decisões implícitas — base para uma boa arquitetura.
- **Conduz:** `grill-with-docs`.
- **Faça:** construa/afie `CONTEXT.md` (glossário de domínio) **dentro de `workspace/`**; registre
  decisões já existentes como ADRs em `workspace/.../docs/adr/`. Entreviste para resolver termos fuzzy.
- **Saídas:** `workspace/.../CONTEXT.md`; ADRs iniciais.
- **Gate:** — (revisão leve com o usuário se houver termos contestados)
- **Grave:** STATE + nota no JOURNAL das decisões capturadas.

## Fase 3 — Revisão de Arquitetura
- **Objetivo:** achar oportunidades de *aprofundamento* (deepening) alinhadas ao charter.
- **Conduz:** `improve-codebase-architecture` (usa `CONTEXT.md` e os ADRs; gera relatório HTML; aplica o teste da deleção).
- **Faça:** explore com subagentes; produza o relatório de candidatos (problema/solução/benefício/
  antes-depois/força da recomendação); **o usuário escolhe** o que atacar.
- **Saídas:** relatório de arquitetura (HTML em tmp) + candidato(s) escolhido(s).
- **Gate:** 🚦 **O usuário escolhe o candidato.**
- **Grave:** STATE = "Candidato X escolhido; próxima: Rede de Segurança".

## Fase 4 — Rede de Segurança
- **Objetivo:** garantir que o comportamento atual da área-alvo está fixado por testes ANTES de mudar.
- **Conduz:** `test-driven-development` (+ characterization tests onde não há cobertura).
- **Faça:** avalie a cobertura na área; escreva characterization/golden-master tests p/ o
  comportamento atual (bugs inclusos); confirme que rodam verdes.
- **Saídas:** testes de baseline verdes no projeto.
- **Gate:** — (a rede precisa estar verde para prosseguir; isto é um gate técnico, não humano)
- **Grave:** STATE + comando de teste registrado no PROJECT-PROFILE.

## Fase 5 — Especificar & Planejar 🚦
- **Objetivo:** transformar o candidato em uma spec e um plano de commits minúsculos.
- **Conduz:** `spec-driven-development` (SPEC) + `request-refactor-plan` (plano em commits mínimos / RFC).
- **Faça:** escreva `SPEC.md` (objetivo, escopo, fora-de-escopo, critérios de sucesso, verificação
  ponta-a-ponta) **dentro de `workspace/`**; quebre em commits minúsculos, cada um verde.
- **Saídas:** `workspace/.../SPEC.md` + plano de refactor (issue/`PLAN.md`).
- **Gate:** 🚦 **O usuário aprova spec + plano.**
- **Grave:** STATE = "Plano aprovado; implementando commit 1/N".

## Fase 6 — Implementar (incremental)
- **Objetivo:** executar o plano em fatias finas, sempre verdes.
- **Conduz:** `incremental-implementation` + `test-driven-development`.
- **Faça:** uma fatia/commit por vez (red → green → refactor); rode a rede de segurança a cada
  passo; pare e reavalie se algo ficar vermelho. Use `/clear` entre fatias não relacionadas.
- **Saídas:** commits incrementais no projeto.
- **Gate:** — (gate técnico: testes verdes a cada commit)
- **Grave:** STATE atualizado a cada commit ("commit k/N feito"); JOURNAL p/ decisões não-óbvias.

## Fase 7 — Verificar & Revisar
- **Objetivo:** provar que a mudança faz o que devia e não quebrou nada.
- **Conduz:** `verify` / `run` + `code-review` (revisão adversarial em subagente de contexto limpo) + `simplify`.
- **Faça:** rode a suíte completa + build; verifique o critério de sucesso da spec; rode
  `/code-review` contra o diff/plano; aplique limpezas de `simplify`; **mostre evidência**.
- **Saídas:** evidência de verde + diff revisado.
- **Gate:** 🚦 (opcional, conforme o charter) **usuário revisa antes de PR/merge.**
- **Grave:** STATE = "Mudança verificada; próxima: Documentar".

## Fase 8 — Documentar & Registrar
- **Objetivo:** deixar o projeto mais legível do que estava.
- **Conduz:** `documentation-and-adrs`.
- **Faça:** escreva ADR(s) das decisões tomadas; atualize `CONTEXT.md`, README, changelog e o
  `CLAUDE.md` do projeto; remova código morto/comentado.
- **Saídas:** ADRs + docs atualizados no projeto.
- **Gate:** — 
- **Grave:** STATE = "Iteração concluída; pronto para o próximo candidato (volta à Fase 3)".

---

## Cross-cutting (em todas as fases)
- **Higiene de contexto (`context-engineering`):** subagentes p/ exploração; `/clear`/compactação
  entre fases; carregue só as seções de doutrina/spec relevantes ao passo atual.
- **Re-entrância (`state/`):** STATE = fonte única da "próxima ação"; JOURNAL = append-only.
  Atualize **em todo limite de fase** — assuma que a sessão pode morrer logo depois.
- **Gates humanos (🚦):** Charter, escolha do candidato, aprovação de spec+plano e (opcional)
  revisão pré-merge. O agente nunca cruza um 🚦 sozinho.

## Mapa rápido fase → skill
| Fase | Skill primária |
|------|----------------|
| 0 Intake | `Explore` + `init` + `context-engineering` |
| 1 Charter | entrevista + `spec-driven-development` |
| 2 Domínio | `grill-with-docs` |
| 3 Arquitetura | `improve-codebase-architecture` |
| 4 Rede | `test-driven-development` |
| 5 Spec/Plano | `spec-driven-development` + `request-refactor-plan` |
| 6 Implementar | `incremental-implementation` + `test-driven-development` |
| 7 Verificar | `verify`/`run` + `code-review` + `simplify` |
| 8 Documentar | `documentation-and-adrs` |
