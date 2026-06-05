# workspace/ — Ponto de Montagem do Projeto

Coloque **aqui** o projeto que você quer melhorar. Esta pasta fica vazia até você montar algo.
A bancada (a doutrina, as skills e o `CLAUDE.md` da raiz) passa a valer automaticamente para o
que estiver aqui, porque o Claude Code é iniciado a partir da raiz da bancada.

## Três modos de montar (escolha um)

### 1. Symlink — recomendado para um repositório **local** existente
Mantém o repositório no lugar original e **dono do próprio git**; a bancada nunca se mistura ao
histórico do projeto.
```bash
ln -s /caminho/para/seu-projeto "workspace/seu-projeto"
```

### 2. Clone — para um repositório **remoto**
```bash
git clone <url-do-repo> "workspace/seu-projeto"
```

### 3. Cópia — fallback (sem git, ou querendo isolar de verdade)
```bash
cp -R /caminho/para/seu-projeto "workspace/seu-projeto"
```

## Depois de montar
Inicie o Claude Code **na raiz da bancada** (não dentro de `workspace/`) e diga algo como:
> "Montei meu projeto em `workspace/`. Comece o Intake (Fase 0)."

O agente lerá `state/STATE.md`, fará a Fase 0 (Intake) e a Fase 1 (Charter, onde ele entrevista
você sobre suas metas) antes de qualquer modificação.

## Regras
- **Artefatos duráveis** gerados durante o trabalho (`CONTEXT.md`, `docs/adr/`, `SPEC.md`, um
  `CLAUDE.md` próprio do projeto) são gravados **dentro** do seu projeto, para viajarem com o repo
  e serem versionados por você.
- A **memória do engajamento** (estado, diário, profile, charter) fica na bancada, em `state/` —
  não polui o seu repositório.
- Um projeto ativo por vez. Para trocar de projeto, arquive `state/` (ex.: `state.<projeto>/`) e
  comece um novo Intake.

> `.gitkeep` mantém esta pasta versionável vazia. O conteúdo real do projeto montado **não** deve
> ser commitado na bancada (veja `.gitignore`).
