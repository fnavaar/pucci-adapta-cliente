# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: aguardando_teste_humano
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: auditoria aprovada no preview `0.0.29` em 2026-10-14. Evidências da Champion confirmam `read/identification` para `employees` (mensagem anterior), `departments`, `projects`, `contracts` (lista 14:42:54) e `tomadores` (confirmação explícita na mesma rodada de teste). A tela exibe `collection_name`. `sensitive_payroll` é fixture separada e não conta como cadastro mestre.
- verificacao_automatica: QA `0.0.29` (`3545c75`) passou em setup, análise estática, build e integrações; `test.ran=false`. Logs do backend em 2026-10-14 por volta de 17:42 UTC mostram HTTP 200 para as consultas de `tomadores`, `projects`, `contracts` e `departments`; consultas anteriores mostram `employees`. Produção permanece em `lastPublishedRef=2b24bd5`.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md
- ultima_acao: teste humano de auditoria das cinco coleções aprovado em `0.0.29`; produção não publicada
- proxima_acao: Champion confirmar se os cadastros reais autorizados pela política já foram carregados no ambiente autorizado; não enviar dados pessoais no chat
- atualizado_em: 2026-10-14T14:55:20-03:00
