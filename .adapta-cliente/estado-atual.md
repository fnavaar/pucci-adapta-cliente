# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: em_correcao
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: aprovado para o fluxo sintético em `0.0.26` — 2026-10-14; Marcela confirmou que colaboradores, setores e `/cadastros` abriram e mostraram os registros sintéticos. Reteste da mudança de auditoria `0.0.27` ainda pendente.
- verificacao_automatica: Skip `0.0.27` (`9a086ff`) passou em setup, análise estática, build e integrações; `test.ran=false`. Logs de `0.0.26` confirmam HTTP 200 nas cinco APIs master-data. Em `0.0.27`, `employees_read_audit_log.js` foi mudado para `onRecordsListRequest` e grava metadados de leitura em `audit_logs`; ainda sem request autenticado posterior ao build. Logs mais recentes contêm tentativas de autenticação HTTP 400. Os hooks de leitura para departments, tomadores, projects e contracts seguem suspensos. Não liberar dados reais até a auditoria de leitura estar ativa e validada em todas as coleções.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md
- ultima_acao: aceite visual do fluxo sintético confirmado; hook experimental de leitura employees em `0.0.27`, pendente reteste; produção permanece em `2b24bd5`
- proxima_acao: Champion autenticar no preview `0.0.27`, abrir `/colaboradores` e depois `/fechamento` → “Controle de acesso e auditoria” → “Carregar trilha”; verificar listagem sem erro e um log `read / employees / identification`. Usar somente dados sintéticos.
- atualizado_em: 2026-10-14T13:42:54-03:00
