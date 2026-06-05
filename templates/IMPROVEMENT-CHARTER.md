<!-- TEMPLATE — copie para state/IMPROVEMENT-CHARTER.md e preencha na Fase 1 (Charter), entrevistando
     o usuário. Este é o ÚNICO insumo reservado para a sessão futura: as metas do usuário. Nada em
     workspace/ é modificado antes deste charter ser APROVADO. -->

# Improvement Charter — <nome do projeto>

- **Data:** <AAAA-MM-DD>   **Status:** rascunho | **APROVADO pelo usuário**

## 1. Objetivo (no idioma do usuário)
O que o usuário quer melhorar/reestruturar/organizar e **por quê**. Problema atual sentido.

## 2. Definition of Done (testável)
Condições concretas e verificáveis que provam que terminamos. Reescreva pedidos vagos como
critérios mensuráveis (ex.: "X passa a ser testável de ponta a ponta"; "tempo de build < N";
"módulo Y deixa de vazar Z").
- [ ] ...
- [ ] ...

## 3. Restrições & non-negotiables
- Não pode quebrar: (APIs públicas, contratos, comportamento observável, ...)
- Tecnologias que **devem** permanecer / **não** podem entrar:
- Limites de tempo/risco/budget:
- Compliance/segurança/licenças:

## 4. Escopo
- **Dentro:**
- **Fora (explicitamente):**

## 5. Como o usuário quer participar (gates)
- Aprovação necessária em: [x] Charter  [ ] escolha do candidato de arquitetura  [ ] spec+plano  [ ] antes de PR/merge
- Forma de revisão preferida (PR, resumo no chat, demo, ...):
- Quão autônomo o agente pode ser entre gates:

## 6. Riscos aceitáveis / apetite
O usuário tolera reescritas maiores ou prefere mudanças mínimas e reversíveis? Strangler Fig ok?

## 7. Notas
Qualquer contexto de negócio, prazos, stakeholders.

---
**Ao aprovar:** marque Status = APROVADO, grave em `state/JOURNAL.md` e avance para a Fase 2.
