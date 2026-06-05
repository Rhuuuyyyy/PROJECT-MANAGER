# Doutrina Operante — Princípios

> Destilação opinativa da pesquisa (fontes datadas em `02-research-basis.md`). Estes princípios
> **governam** o trabalho; não são sugestões. Cada um traz a razão e o que ele te faz fazer.

## Os 10 princípios

### 1. Contexto é o recurso escasso — engenhe-o de propósito
A qualidade do agente despenca conforme o contexto enche ("context rot"; atenção é orçamento
finito). **Faça:** busque o *menor conjunto de tokens de alto sinal*; carregue informação
*just-in-time* (caminhos/queries, não despejos); use **subagentes** para exploração pesada;
`/clear` e compactação entre fases; mantenha o `CLAUDE.md` enxuto. → *Anthropic, "Context
Engineering", 2025-09-29; skill `context-engineering`.*

### 2. Entender antes de mudar — separe exploração/planejamento da execução
Pular direto para o código produz a solução do problema errado. **Faça:** comece em *plan mode*;
mapeie estrutura, domínio e riscos do projeto existente; só então implemente. → *Claude Code best
practices; skill `improve-codebase-architecture`.*

### 3. Comportamento é sagrado — rede de segurança ANTES de refatorar
Sistemas legados codificam anos de correções em casos extremos que somem num restructure cego.
**Faça:** fixe o comportamento atual com **characterization tests** (golden master) — bugs e tudo
— antes de tocar na área. Sem rede → sem refactor. → *prática consolidada de modernização de
legado; skill `test-driven-development`.*

### 4. Mude em passos minúsculos, reversíveis e sempre verdes
"Faça cada passo de refatoração tão pequeno que o programa nunca pare de funcionar" (Fowler).
**Faça:** commits minúsculos, cada um deixando o sistema funcional; **Strangler Fig** para
substituições grandes; nunca uma reescrita monolítica. → *skills `request-refactor-plan`,
`incremental-implementation`.*

### 5. Especifique antes de trabalho significativo — a spec é a fonte da verdade
Para qualquer mudança não-trivial, escreva a spec primeiro: `SPECIFY → PLAN → TASKS → IMPLEMENT`,
com revisão humana entre fases. Traduza pedidos vagos em **critérios de sucesso testáveis**.
**Faça:** entreviste o usuário; surface premissas; só codifique contra uma spec aprovada. →
*GitHub Spec Kit, 2025-09-02; skill `spec-driven-development`.*

### 6. Toda mudança precisa de uma verificação que o próprio agente roda
"Parece pronto" não é pronto. **Faça:** dê ao agente um teste/build/lint/diff/screenshot que
retorne pass/fail e feche o loop sozinho; mostre **evidência**, não afirmação; adicione uma
**revisão adversarial** num subagente de contexto limpo (use `/code-review`). → *Claude Code best
practices; S. Willison, "Designing agentic loops", 2025-09-30.*

### 7. Busque profundidade — aprofunde módulos, não multiplique módulos rasos
Os melhores módulos têm interface pequena escondendo muita implementação (Ousterhout, *deep
modules*). Módulo raso (interface ≈ implementação) não paga seu custo. **Faça:** aplique o **teste
da deleção**; consolide acoplamento que vaza; mire testabilidade e navegabilidade-por-IA. →
*Ousterhout, "A Philosophy of Software Design"; skill `improve-codebase-architecture`.*

### 8. Registre o *porquê* — decisões viram ADRs, domínio vira glossário
Código mostra o *quê*; o valor está no *porquê* e nas alternativas rejeitadas. **Faça:** escreva
**ADRs** para decisões caras de reverter; mantenha um **`CONTEXT.md`** que dá nome ao domínio;
torne o codebase legível para humanos *e* agentes futuros. → *skills `documentation-and-adrs`,
`grill-with-docs`.*

### 9. Persista estado — trate sessões como turnos
Cada sessão nova começa sem memória, "como engenheiros em turnos". **Faça:** use `state/STATE.md`
(fase + próxima ação), `state/JOURNAL.md` (decisões) e o histórico git como memória; atualize-os
ao fim de cada fase; comece toda sessão relendo o estado. → *Anthropic, "Effective harnesses for
long-running agents", 2025-11-26.*

### 10. Orquestre — não superautomatize; humano nos gates
A tendência madura de 2026 é **coerência por orquestração, não autonomia cega**. Ganhos medidos
são reais porém modestos e dependem de prática. **Faça:** o agente faz o trabalho braçal; o humano
aprova nos 🚦 gates (charter, plano, antes de implementar); use multi-agente (orquestrador +
subagentes em contexto próprio) quando ajudar. → *B. Böckeler/Thoughtworks; M. Mason, 2026-01;
Anthropic multi-agent research system.*

## O que NÃO acreditamos (separar prática de hype)
- **"Vibe coding" em escala** não é método — é o que a spec-driven veio corrigir.
- **Agentes não modernizam legado "sozinhos".** Supervisão humana e validação de comportamento
  são obrigatórias.
- **Métricas infladas de produtividade** devem ser tratadas com ceticismo; meça resultados reais.
- **Não confie no output só porque parece plausível** (princípio 6).
- **Não inche contexto/`CLAUDE.md`**: mais instrução ≠ melhor; o excesso faz o agente ignorar o
  que importa (princípio 1).
- **Ferramentas/benchmarks específicos** envelhecem rápido — prenda-se aos princípios, não a um
  produto. Reavalie a base de evidências periodicamente (`02-research-basis.md`).
