# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: aguardando_teste_humano
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: pendente — aguarda homologação de colaboradores, departamentos, tomadores, projetos e contratos sintéticos no preview
- verificacao_automatica: passou com ressalva — Skip `0.0.25` (`1279dde`): setup, análise estática, build e integrações passaram; o runner reportou `test.ran=false`, portanto nenhum teste automatizado foi executado. Migrations `0004` a `0009` estão aplicadas; backend confirma as cinco coleções, relações, índices únicos e RLS. Logs recentes confirmam leituras HTTP 200 de `departments` e `employees`; leitura autenticada de `tomadores`, `projects` e `contracts` ainda depende do teste humano. Filtro de erros de hooks retornou 0 entradas.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-09-1621-ordenar-schema-e-hooks-skip.md
- ultima_acao: integração segura do novo layout implementada no preview; autenticação local e credenciais demo removidas; cadastro mestre e fixtures sintéticas adicionados; trilha append-only de create/read/update/delete configurada sem registrar valores pessoais; RBAC de projetos corrigido para Financeiro somente leitura. Produção não foi publicada.
- proxima_acao: Champion testar o fluxo no preview e informar se funcionou; não publicar produção nem iniciar F1-T06 antes do aceite
- atualizado_em: 2026-10-09T16:32:05-03:00
