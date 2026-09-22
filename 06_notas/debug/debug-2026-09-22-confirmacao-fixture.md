# Debug Summary — F1-T02 — confirmação inline da fixture

- **Data:** 2026-09-22
- **Task/SPEC:** F1-T02 / `04-fase-atual/specs/spec-1-003.md`
- **Ambiente:** Skip `RH Pucci` · projectId `59746`
- **Sintoma:** no teste humano, a fixture foi criada com sucesso, mas a mensagem visual de operação concluída não apareceu para a champion.
- **Reprodução:** logs do backend registraram `POST /api/collections/sensitive_payroll/records` com HTTP 200; o preview mostrou novo ID e valores sintéticos; não houve erro de hook.
- **Causa raiz:** o componente global de feedback ficava no topo da página, distante do card da ação; a confirmação podia estar fora da área visível.
- **Correção:** renderizar o feedback de criação também dentro do card da fixture, junto do botão, ID e registro.
- **Verificação:** Skip QA da versão `0.0.6` passou em setup, análise estática, build, integrações e testes.
- **Gate:** aguardando repetição humana do passo 4; task não concluída.
- **Privacidade:** sem credenciais, segredo ou dado real.
