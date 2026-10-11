# AP-2026-10-11-1428 — Isolar hooks de enriquecimento antes de auditar leitura

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T05 · `04_fase-atual/specs/spec-1-002.md`
- Sinal: na versão `0.0.25`, listagens de `employees` e `departments` falharam com HTTP 500 `Failed to enrich records.`; ambos tinham hooks `onRecordEnrich` que gravavam em `audit_logs`. Após suspender os cinco hooks de leitura e aplicar `0.0.26`, a Champion confirmou que colaboradores e setores abriram; logs autenticados mostram GET HTTP 200 para as cinco coleções master data e nenhuma falha de request posterior a 17:18 UTC.
- Evidência: `06_notas/debug/debug-2026-10-11-f1-t05-enrichment-500.md`; logs Skip do projeto `59746` em 2026-10-11; preview `0.0.26` (`156263c`).
- Regra reutilizável: diante de `Failed to enrich records`, inspecionar `onRecordEnrich` que executa escrita; em preview, isolar a hipótese suspendendo somente esses hooks, repetir a mesma leitura autenticada e comparar logs. Quando vários hooks forem retirados em conjunto, registrar correlação sem atribuir causa a um arquivo/linha específico. Não considerar o fluxo pronto para dados reais enquanto a auditoria de leitura estiver suspensa.
- Quando aplicar: falha de listagem PocketBase em enriquecimento de resposta e hooks de leitura com side effect de escrita.
- Quando não aplicar: erros de listagem sem hooks `onRecordEnrich` ou erros de criação/atualização, que exigem diagnóstico separado.
- Confiança: média — 500 antes, 200 após retirar cinco hooks e confirmação humana de duas telas; não houve bisect individual e a trilha de leitura continua desativada.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
