# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: em_correcao
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: aprovado para fluxo sintético no preview `0.0.26` — 2026-10-14; Marcela confirmou colaboradores, setores e `/cadastros` com fixtures. A alteração posterior de auditoria em `0.0.27` aguarda reteste autenticado.
- verificacao_automatica: `0.0.27` (`9a086ff`) passou em setup, análise estática, build e integrações; `test.ran=false`. Logs de `0.0.26` comprovam HTTP 200 nas cinco APIs master-data. Em `0.0.27`, `employees_read_audit_log.js` usa `onRecordsListRequest` para gravar metadados de leitura em `audit_logs`; ainda sem leitura autenticada pós-build. Logs recentes incluem tentativas de autenticação HTTP 400. Auditoria de leitura das outras quatro coleções permanece suspensa. Não usar dados reais.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md
- ultima_acao: aprovação visual das telas e fixtures em `0.0.26`; hook experimental de auditoria de employees alterado em `0.0.27`; produção não atualizada (`2b24bd5`)
- proxima_acao: Champion autenticar no preview `0.0.27`, testar `/colaboradores`, abrir `/fechamento` → “Controle de acesso e auditoria” → “Atualizar trilha” e confirmar listagem e log `read` de `employees` com campo `identification`; usar somente fixtures sintéticas
- atualizado_em: 2026-10-14T13:45:35-03:00
