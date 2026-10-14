# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-10-14 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- **Tasks concluídas:** 4/8 (50%). F1-T01 a F1-T04 seguem concluídas nos limites registrados. F1-T05 está em correção; não será marcada como concluída enquanto a trilha de leitura não estiver restaurada e validada.
- **F1-T05 — aceite visual de fixtures:** em 2026-10-14, Marcela confirmou colaboradores, setores e `/cadastros` em `0.0.26` (`156263c`). Logs daquela versão registraram HTTP 200 nas APIs de `employees`, `departments`, `tomadores`, `projects` e `contracts`.
- **Auditoria de leitura:** cinco hooks `onRecordEnrich` foram suspensos para corrigir HTTP 500. Em `0.0.27` (`9a086ff`), `employees_read_audit_log.js` foi migrado para `onRecordsListRequest` como experimento; QA passou em setup, estática, build e integrações, mas `test.ran=false`. Não há request autenticado pós-build; logs mais recentes mostram tentativas de login HTTP 400. Hooks de leitura das outras coleções continuam suspensos. **Não inserir dados reais.**
- **Próximo teste:** autenticar em `0.0.27`, abrir `/colaboradores`; depois `/fechamento` → “Controle de acesso e auditoria” → “Atualizar trilha”. Confirmar listagem sem erro e log de leitura `employees` com `identification`. Usar apenas fixtures sintéticas. Só então replicar padrão para as demais coleções e repetir QA/runtime.
- **Produção:** não publicada. `lastPublishedRef=2b24bd5`.
- **F1-T04:** preservada. B-MET-01 e B-STE-01 seguem pendentes até primeiro fechamento real medido.

## Ambiente
- Preview: `https://rh-pucci-3116c--preview.goskip.app` · `0.0.27` (`9a086ff`).
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção: https://rh-pucci-3116c.goskip.app · referência publicada `2b24bd5`.
