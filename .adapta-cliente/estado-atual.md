# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: aguardando_teste_humano
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: fluxo visual das telas com fixtures aprovado em `0.0.26` (2026-10-14); auditoria de employees aprovada em `0.0.27` por eventos `read/identification` enviados pela Champion. Em `0.0.28`, a Champion apresentou 20 eventos `read/identification`, mas a UI não mostrava collection_name, então não foi possível comprovar cobertura das cinco coleções. A UI agora exibe a coleção em `0.0.29`; reteste humano por coleção pendente.
- verificacao_automatica: `0.0.29` (`3545c75`) passou em setup, análise estática, build e integrações; `test.ran=false`. O diff de `src/pages/Index.tsx` foi verificado: a tabela de auditoria renderiza `log.collection_name` ao lado de ação/registro. Produção não alterada (`lastPublishedRef=2b24bd5`).
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md
- ultima_acao: coluna “Coleção” adicionada à trilha para tornar verificável a cobertura por entidade; QA `0.0.29` aprovado, sem testes automatizados
- proxima_acao: Champion autenticar no preview `0.0.29`, abrir `/fechamento` → “Controle de acesso e auditoria” → “Atualizar trilha” e confirmar eventos `read` para `employees`, `departments`, `tomadores`, `projects` e `contracts`; usar somente fixtures sintéticas
- atualizado_em: 2026-10-14T14:31:19-03:00
