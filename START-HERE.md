# START HERE — Manual da Bancada

> Ponto de entrada autodescritivo. Se você é uma sessão nova (humano ou agente) e só tem este
> diretório, este arquivo basta para entender tudo e retomar o trabalho.

## 1. O que é isto

Uma **bancada reutilizável de engenharia de software aumentada por IA**. O trabalho que ela
governa é sempre o mesmo tipo: **pegar um projeto que já existe e melhorá-lo, reestruturá-lo e
organizá-lo** para as necessidades do usuário, de forma segura e eficiente — usando um agente de
IA (Claude Code) como engenheiro principal.

A bancada **não** contém o projeto. Ela contém a *doutrina*, o *fluxo*, as *skills*, os
*templates* e a *memória de estado* que tornam o trabalho repetível e retomável em qualquer
projeto, em qualquer stack.

## 2. Como o usuário entrega o projeto (a relação bancada ↔ projeto)

O projeto-alvo é **montado em `workspace/`**. Veja `workspace/README.md` para os 3 modos
(symlink — recomendado p/ repo local; clone — p/ repo remoto; cópia — fallback). A justificativa
dessa arquitetura está na seção 6.

Regra de ouro da separação:
- **Dentro de `workspace/` (o repo do usuário):** artefatos duráveis que devem viajar com o
  projeto — `CONTEXT.md` (glossário de domínio), `docs/adr/` (decisões), `SPEC.md`, e um
  `CLAUDE.md`/`AGENTS.md` próprio do projeto. São versionados pelo usuário.
- **Aqui na bancada (`state/`):** memória do engajamento — `STATE.md`, `JOURNAL.md`,
  `PROJECT-PROFILE.md`, `IMPROVEMENT-CHARTER.md`. Não poluem o repo do usuário e tornam a
  bancada reutilizável.

## 3. Como começar (cold start)

1. Leia `state/STATE.md`.
   - **"Nenhum engajamento ativo"** → não há projeto montado ainda. Peça ao usuário para montar
     o projeto em `workspace/` (veja `workspace/README.md`) e então rode a **Fase 0 (Intake)** e
     a **Fase 1 (Charter)** de `doctrine/01-workflow.md`.
   - **Engajamento em andamento** → o STATE diz a fase atual e a **próxima ação única**. Faça-a.
2. Em dúvida sobre *por que* fazemos algo de certo jeito → `doctrine/00-principles.md`.
3. Em dúvida sobre *o que* fazer agora e *qual skill* usar → `doctrine/01-workflow.md`.
4. Em dúvida sobre a *evidência* por trás da doutrina → `doctrine/02-research-basis.md`.

## 4. Estrutura de arquivos

```
.
├── CLAUDE.md                  # contrato operacional, auto-carregado pelo Claude Code
├── AGENTS.md                  # ponteiro p/ portabilidade entre ferramentas
├── START-HERE.md              # este manual
├── doctrine/
│   ├── 00-principles.md       # princípios operantes (o "porquê/o quê")
│   ├── 01-workflow.md         # fluxo por fases + gates + qual skill em cada fase
│   └── 02-research-basis.md   # base de evidências, datada e com fontes
├── templates/
│   ├── PROJECT-PROFILE.md     # molde do retrato do projeto (preenchido na Fase 0)
│   └── IMPROVEMENT-CHARTER.md # molde das metas do usuário (preenchido na Fase 1)
├── state/
│   ├── STATE.md               # status atual + próxima ação (a memória de retomada)
│   └── JOURNAL.md             # log append-only de sessões e decisões
├── workspace/                 # PONTO DE MONTAGEM do projeto do usuário (vazio por padrão)
│   └── README.md              # como montar o projeto
├── .claude/
│   ├── skills/                # as 8 skills instaladas (+ find-skills)
│   ├── settings.json          # (opcional) allowlist de inspeção — habilite via /update-config
│   └── settings.local.json    # permissões pessoais (gitignored)
└── skills-lock.json           # lockfile das skills instaladas
```

## 5. O fluxo em uma olhada (detalhe em `doctrine/01-workflow.md`)

`Intake → Charter → Domínio & Decisões → Revisão de Arquitetura → Rede de Segurança →
Especificar & Planejar → Implementar (incremental) → Verificar & Revisar → Documentar`

Cada fase tem **entradas, saídas, a skill que a conduz e um gate**. Gates marcados com 🚦
exigem aprovação do usuário antes de avançar. Ao fim de cada fase: **atualize `state/`**.

## 6. Por que esta arquitetura (decisão justificada)

Avaliei quatro relações possíveis bancada↔projeto: (a) diretório irmão; (b) projeto **aninhado**
na bancada; (c) bancada copiada para dentro do projeto; (d) etapa de ingestão.

Escolhi **(b) + (d): a bancada é o diretório de trabalho e o projeto é montado em `workspace/`,
com uma etapa de Intake que o ingere.** Razões:
- O Claude Code carrega `CLAUDE.md` e as `.claude/skills/` a partir do diretório de trabalho.
  Aninhar o projeto sob a bancada faz **toda a doutrina e todas as skills valerem para o projeto**
  com um único diretório de trabalho — sem caminhos externos frágeis (problema do irmão).
- **Symlink** como modo recomendado mantém o repositório do usuário **intacto e dono do próprio
  git**; a bancada nunca se mistura ao histórico do projeto (problema da cópia-para-dentro).
- A **separação de artefatos** (seção 2) garante que o que é valioso para o projeto fique no
  projeto, e o que é "andaime" do agente fique na bancada → a bancada permanece **reutilizável**
  e o repo do usuário permanece **limpo**.
- A **etapa de Intake** descobre o stack em tempo de execução → a bancada nunca precisa
  hard-codar tecnologia (**adaptável**).

## 7. O que NÃO fazer
- Não modifique `workspace/` sem `IMPROVEMENT-CHARTER.md` aprovado.
- Não hard-code stack/linguagem/domínio na doutrina ou nos templates da bancada.
- Não deixe o `CLAUDE.md` da bancada crescer: o que é situacional vira skill ou doc referenciado.
- Não confie em "parece pronto" — feche o loop com uma verificação executável.

---
*Os arquivos `prompt-1-*.md` e `prompt-2-*.md` na raiz foram os prompts de bootstrap que
construíram esta bancada; não fazem parte do runtime e podem ser arquivados.*
