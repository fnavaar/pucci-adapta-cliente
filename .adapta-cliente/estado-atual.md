# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: em_correcao
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: fluxo visual de fixtures aprovado em `0.0.26` (2026-10-14). Em `0.0.27`, Marcela confirmou por log quatro leituras sintéticas de `employees` com `action=read`, `fields=identification`; logs do Skip corroboram GET employees e GET audit_logs HTTP 200 em 13:49:40–13:49:50 local.
- verificacao_automatica: `0.0.27` (`9a086ff`) QA passou em setup, análise estática, build e integrações, `test.ran=false`. Hook `onRecordsListRequest` de employees validado em runtime por evidência Champion + HTTP 200. Hooks equivalentes para departments, tomadores, projects e contracts foram adicionados ao working tree e aguardam QA/build `0.0.28` e reteste autenticado. Não usar dados reais até prova das cinco coleções.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md
- ultima_acao: validação humana do hook employees aprovada; iniciada a restauração dos quatro hooks restantes via list request, sem publicar produção
- proxima_acao: rodar QA `0.0.28`; se passar, Champion retestar as cinco listas com fixtures e consultar a trilha para conferir eventos `read` de todas as coleções
- atualizado_em: 2026-10-14T13:51:19-03:00
