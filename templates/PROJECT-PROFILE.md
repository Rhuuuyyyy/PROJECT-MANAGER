<!-- TEMPLATE — copie para state/PROJECT-PROFILE.md e preencha na Fase 0 (Intake). Stack-agnóstico:
     descubra os valores reais explorando o projeto; não presuma. -->

# Project Profile — <nome do projeto>

- **Data do intake:** <AAAA-MM-DD>
- **Como o projeto foi montado:** symlink | clone | cópia (ver workspace/README.md)
- **Caminho em workspace/:** `workspace/<...>`

## Identidade & stack (descoberta, não presumida)
- **Linguagem(ns) principal(is):**
- **Frameworks / runtime / versões:**
- **Gerenciador de pacotes / build system:**
- **Repositório:** mono-repo | multi-repo | pacote único — observações:

## Comandos verificados (rode-os; cole a saída de sucesso)
- **Instalar deps:** `...`
- **Build:** `...`
- **Testes:** `...`  (framework: ...; como rodar um único teste: `...`)
- **Lint / format / typecheck:** `...`
- **Rodar a aplicação localmente:** `...`

## Mapa de módulos (alto nível)
- Pontos de entrada:
- Principais módulos/pacotes e responsabilidade de cada:
- Fronteiras/seams notáveis (onde o comportamento pode ser alterado sem editar no lugar):

## Saúde & riscos
- **Cobertura de testes (estado atual):**
- **Áreas sem teste / frágeis / "aqui mora o medo":**
- **Dívidas/arquitetura rasa observada (candidatos preliminares):**
- **Dependências externas / serviços / segredos / variáveis de ambiente:**
- **Restrições de execução (DB, rede, credenciais, plataformas):**

## Domínio
- **Glossário existe?** (`CONTEXT.md` no repo?) sim/não — onde:
- **ADRs existem?** (`docs/adr/` ou `docs/decisions/`?) sim/não — onde:

## Perguntas em aberto para o usuário
- ...

> Saída desta fase também: um rascunho de `CLAUDE.md` *dentro* do projeto (convenções que o agente
> deve seguir ao trabalhar no repo). Mantenha-o enxuto (ver Princípio 1).
