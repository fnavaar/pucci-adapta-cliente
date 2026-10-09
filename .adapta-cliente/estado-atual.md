# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: aguardando_teste_humano
- autorizacao_implementacao: confirmada — 2026-09-24T10:20:00-03:00 — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: pendente — aguarda homologação de colaboradores, departamentos, tomadores, projetos e contratos sintéticos no preview
- verificacao_automatica: passou com ressalva — Skip `0.0.24` (`e8e9427`): setup, análise estática, build e integrações passaram; o runner reportou `test.ran=false`, então não houve execução de testes automatizados. Migrations `0004` a `0009` estão aplicadas; as cinco coleções, as quatro relações e índices únicos foram conferidos no backend. Logs recentes confirmam leituras HTTP 200 de `departments` e `employees`; consulta de `tomadores/projects/contracts` ainda depende da sessão humana no preview. Nenhum erro de hook apareceu no filtro de logs consultado.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-09-1621-ordenar-schema-e-hooks-skip.md
- ultima_acao: integração segura do novo layout implementada no preview; autenticação local e credenciais demo removidas; cadastro mestre e fixtures sintéticas adicionados; RBAC conforme papéis; trilha append-only de create/read/update/delete configurada sem registrar valores pessoais; migração de escopo F1-T05 aplicada
- proxima_acao: Champion testar o fluxo no preview e informar se funcionou; não publicar produção nem iniciar F1-T06 antes do aceite
- atualizado_em: 2026-10-09T16:21:16-03:00
