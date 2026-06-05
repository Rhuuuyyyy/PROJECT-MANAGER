# AGENTS.md

Esta bancada é operada principalmente pelo **Claude Code**, que carrega `CLAUDE.md`
automaticamente. `AGENTS.md` existe para portabilidade entre ferramentas (padrão aberto
mantido pela Agentic AI Foundation / Linux Foundation).

**Qualquer agente** (Claude Code, Codex, Cursor, etc.) deve, antes de agir:

1. Ler **`CLAUDE.md`** (contrato operacional + primeira ação de toda sessão).
2. Ler **`START-HERE.md`** (manual completo da bancada).
3. Ler **`state/STATE.md`** (fase atual e próxima ação) e seguir a partir dali.

Não há instruções específicas de stack aqui: a bancada é stack-agnóstica e descobre o projeto
montado em `workspace/` na fase de Intake.
