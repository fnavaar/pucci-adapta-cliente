# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-10-14 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- **Tasks concluídas:** 4/8 (50%). F1-T01 a F1-T04 concluídas nos limites já registrados. F1-T05 segue ativa e não será marcada como concluída até a auditoria de leitura ser restaurada e verificada.
- **F1-T05 — aceite sintético:** Marcela confirmou em 2026-10-14 que `/colaboradores`, `/setores` e `/cadastros` abriram e mostraram fixtures sintéticas no preview `0.0.26` (`156263c`). Logs daquele reteste mostram HTTP 200 para as APIs `employees`, `departments`, `tomadores`, `projects` e `contracts`.
- **F1-T05 — gate de segurança pendente:** os cinco hooks de auditoria de leitura que escreviam em `audit_logs` dentro de `onRecordEnrich` continuam suspensos, exceto uma tentativa de substituição para `employees` em `0.0.27` (`9a086ff`) usando `onRecordsListRequest`. QA passou em setup, análise estática, build e integrações; `test.ran=false`. Ainda não há chamada autenticada após esse novo build. Logs recentes registram tentativas de login HTTP 400, portanto não há prova de que o hook novo grave auditoria nem que a tela abra nessa versão. A auditoria das outras quatro coleções permanece desligada.
- **Privacidade:** manter somente fixtures sintéticas. Não inserir nomes, e-mails, identificadores ou qualquer dado real enquanto a trilha de leitura estiver incompleta.
- **Produção:** não publicada. `lastPublishedRef=2b24bd5`; o trabalho segue apenas no preview.
- **Próximo passo:** teste autenticado de `/colaboradores` em `0.0.27` e conferência do log sintético de leitura em `/fechamento`; em seguida, restaurar/testar leitura nas demais coleções antes de fechar F1-T05. Não iniciar F1-T06.
- **F1-T04:** módulo preservado. B-MET-01 e B-STE-01 seguem pendentes até o primeiro fechamento real medido.

## Ambiente
- Preview: `https://rh-pucci-3116c--preview.goskip.app` · versão `0.0.27` (`9a086ff`).
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção: https://rh-pucci-3116c.goskip.app · referência publicada `2b24bd5`.
