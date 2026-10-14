# Estado atual — Adapta Cliente

- task_id: F1-T05
- champion: Marcela
- spec: 04_fase-atual/specs/spec-1-002.md
- etapa: em_correcao
- autorizacao_implementacao: confirmada — 2026-10-09 (horário original não registrado) — “Crie tudo necessário”, após o relatório de análise da F1-T05
- teste_humano: aprovado para fluxo sintético no preview `0.0.26` — 2026-10-14; Marcela confirmou que colaboradores, setores e Cadastros mestres abriram e mostraram os registros sintéticos. A versão atual `0.0.27` ainda precisa de teste autenticado porque o hook de auditoria de leitura de employees foi alterado depois do aceite visual.
- verificacao_automatica: `0.0.27` (`9a086ff`) passou setup, análise estática, build e integrações; `test.ran=false`, sem testes automatizados. Em `0.0.26`, logs autenticados registraram HTTP 200 nas cinco APIs master-data. Em `0.0.27`, hook `onRecordsListRequest` grava auditoria apenas em `employees`, mas não há request autenticado pós-build; logs mostram tentativas de login HTTP 400 às 16:36–16:40 UTC, então auditoria ainda não validada. Hooks de leitura de departments, tomadores, projects e contracts seguem desativados. Não liberar dados reais.
- aprendizado: capturado:06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md
- ultima_acao: reteste visual sintético aprovado em `0.0.26`; hook de auditoria de employees migrado para `onRecordsListRequest` em `0.0.27`, aguardando prova autenticada da listagem e do log
- proxima_acao: Champion testar login e listagem `/colaboradores` em `0.0.27` e conferir a entrada read-only de `employees` em `/fechamento`; depois restaurar auditoria equivalente às demais coleções e revalidar
- atualizado_em: 2026-10-14T13:42:12-03:00
