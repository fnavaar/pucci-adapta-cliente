# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: aguardando_teste_humano
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: parcial em `0.0.29` — em 2026-10-14 às 14:34, Marcela enviou eventos `read/identification` para `employees` e `departments` (um registro employees e três departments). A tabela também mostra uma leitura separada da fixture sintética `sensitive_payroll`; isso não comprova as três coleções restantes da F1-T05. Eventos de `tomadores`, `projects` e `contracts` ainda não foram apresentados.
- verificacao_automatica: Skip `0.0.29` (`3545c75`) passou em setup, análise estática, build e integrações; `test.ran=false`. A UI mostra `collection_name` na trilha. Produção permanece em `lastPublishedRef=2b24bd5`.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md
- ultima_acao: reteste parcial da Champion em `0.0.29`: auditoria visível para employees/departments; não há evidência no envio atual para tomadores/projects/contracts
- proxima_acao: abrir `/cadastros` no preview `0.0.29` para consultar tomadores, projetos e contratos; depois abrir `/fechamento` → “Controle de acesso e auditoria” → “Atualizar trilha” e confirmar eventos `read/identification` dessas três coleções
- atualizado_em: 2026-10-14T14:37:42-03:00
