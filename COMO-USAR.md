# Como usar esta bancada

Esta pasta é uma **oficina** que melhora, reorganiza e reestrutura um projeto que **já existe**.
Você encaixa seu projeto, dá o objetivo, e o agente faz o trabalho em etapas — pedindo sua
aprovação nos momentos importantes.

## Passo 1 — Coloque seu projeto em `workspace/`
Use **uma** destas opções (symlink é o recomendado, mantém seu repositório intacto):

```bash
# repositório local (recomendado)
ln -s /caminho/do/seu-projeto "workspace/seu-projeto"

# OU repositório remoto
git clone <url> "workspace/seu-projeto"

# OU cópia simples
cp -R /caminho/do/seu-projeto "workspace/seu-projeto"
```

## Passo 2 — Abra o Claude Code **nesta pasta** (a raiz da bancada)
Não abra dentro de `workspace/`. Abra aqui na raiz.

## Passo 3 — Diga para começar
Escreva algo como:

> **Montei meu projeto em `workspace/`. Comece o Intake (Fase 0).**

## O que vai acontecer
1. Ele **analisa** seu projeto (sem mudar nada).
2. Ele **te entrevista** sobre o que você quer melhorar e o que é "pronto".
   👉 **Nada no seu código é alterado antes de você aprovar** esse objetivo.
3. Depois ele trabalha em etapas (arquitetura → testes de segurança → plano → implementar →
   verificar → documentar) e **pede sua aprovação** nos pontos-chave.

## Como retomar mais tarde
Abra o Claude Code aqui de novo e diga: **continue**.
Ele lembra exatamente onde parou (está em `state/STATE.md`).

## Como trocar de projeto
Tire o projeto de `workspace/`, coloque outro, e comece de novo pelo Passo 3.

---
**Quer entender mais a fundo?** Leia `START-HERE.md`.
**Dica:** se aparecerem pausas pedindo "continue" a cada arquivo, é um hook de validação de
`.canvas` no seu `~/.claude/`; peça ao agente para te mostrar como desativá-lo.
