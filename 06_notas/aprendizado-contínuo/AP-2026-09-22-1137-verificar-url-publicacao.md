# AP-2026-09-22-1137 — Verificar a URL antes da homologação visual

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T02 / `04-fase-atual/specs/spec-1-003.md`
- Sinal: preview e produção do mesmo projeto entregaram bundles diferentes após a criação da versão `0.0.6`.
- Evidência: comparação direta dos assets públicos; preview contém `fixtureMessage`, produção não contém.
- Regra reutilizável: antes de interpretar um teste visual como falha do código, confirmar a URL e o hash/asset da versão efetivamente servida; `isPublished` isolado não comprova que a versão corrente esteja na produção.
- Quando aplicar: homologações com preview e produção simultâneos, especialmente após `apply_changes` sem publicação explícita.
- Quando não aplicar: quando o ambiente único e a versão servida forem comprovados pelo mesmo hash.
- Confiança: alta — diferença observada diretamente nos bundles públicos.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
