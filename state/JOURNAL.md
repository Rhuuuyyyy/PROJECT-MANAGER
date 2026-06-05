# JOURNAL — Log append-only de sessões e decisões

> Acrescente ao final; nunca reescreva o passado. Uma entrada por sessão e por decisão não-óbvia.
> Formato: data, fase, o que aconteceu, decisões + porquê (ADR-worthy vai virar ADR no projeto).

---

## 2026-06-04 — Bootstrap da bancada
- **Fase:** construção do ambiente (pré-Intake).
- **O que aconteceu:** pesquisa atual sobre engenharia de software agêntica e melhoria de codebases
  existentes; destilação da doutrina (`doctrine/`); construção da estrutura da bancada (entry point,
  templates, estado, ponto de montagem, settings).
- **Decisões-chave:**
  - Relação bancada↔projeto: **projeto aninhado em `workspace/` + etapa de Intake**; symlink como
    modo recomendado. Justificativa em `START-HERE.md` §6.
  - Separação de artefatos: duráveis (CONTEXT.md, docs/adr, SPEC.md, CLAUDE.md do projeto) **dentro
    do projeto**; estado/diário **na bancada**.
  - Loadout de 8 skills instaladas (ver `skills-lock.json`) mapeado às fases do fluxo.
- **Próxima ação:** aguardar projeto em `workspace/` → Fase 0 (Intake). Ver `state/STATE.md`.
