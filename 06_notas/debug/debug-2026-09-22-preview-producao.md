# Debug Summary — F1-T02 — divergência preview/produção

- **Data:** 2026-09-22
- **Task/SPEC:** F1-T02 / `04-fase-atual/specs/spec-1-003.md`
- **Ambiente:** Skip `RH Pucci` · projectId `59746`
- **Sintoma:** após a versão `0.0.6`, a champion ainda não visualizou a mensagem `Operação concluída` junto do ID.
- **Reprodução:** comparação dos bundles públicos: preview `/assets/index-BCjpus0O.js` contém `fixtureMessage` e a mensagem inline; produção `/assets/index-9op2ZCVL.js` não contém `fixtureMessage`.
- **Causa raiz:** `0.0.6` está no preview, mas a produção pública continua servindo o bundle anterior; `isPublished` não prova publicação da versão corrente.
- **Correção:** nenhuma nova alteração de código neste ciclo. O teste deve usar o preview exato; publicar produção requer autorização explícita.
- **Verificação:** comparação via `curl`; logs do backend mostram criação da fixture com HTTP 200; sem erro de hook.
- **Gate:** em correção até confirmar a URL ou publicar `0.0.6`.
- **Privacidade:** sem credenciais, segredo ou dado real.
