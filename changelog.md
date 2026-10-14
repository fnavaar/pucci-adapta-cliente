# Changelog — Pucci Ambiental · adapta-cliente

## 2026-10-14 · [Marcela] · F1-T05: aceite visual do cadastro sintético; auditoria ainda em validação
- Marcela confirmou que `/cadastros` abriu e exibiu os registros sintéticos no preview `0.0.26`. Somado às confirmações anteriores de colaboradores/setores, fecha o teste visual das telas cadastradas com fixtures.
- Logs autenticados de `0.0.26` registraram GET HTTP 200 para `employees`, `departments`, `tomadores`, `projects` e `contracts`.
- A task permanece em correção por segurança: cinco hooks de auditoria de leitura foram suspensos após erros de enriquecimento. Em `0.0.27` (`9a086ff`), somente o hook de leitura `employees` foi alterado para `onRecordsListRequest`, fora de `onRecordEnrich`; QA em setup, estática, build e integrações passou, mas `test.ran=false` e ainda não há reteste autenticado pós-build. Os outros quatro hooks seguem suspensos. Não usar dados reais.
- Próximo passo: Champion testar employees + “Atualizar trilha” em `/fechamento` na `0.0.27` e confirmar um log `read / employees / identification`; depois reintroduzir auditoria nas outras coleções uma a uma e testar runtime.
- Produção preservada em `lastPublishedRef=2b24bd5`; não concluir F1-T05 nem iniciar F1-T06 neste gate.

## 2026-10-11 · [Marcela] · DEBUG F1-T05: listagens recuperadas após suspensão temporária da auditoria de leitura
- Logs de `0.0.25` mostraram HTTP 500 `Failed to enrich records` nas listagens; hooks gravavam em `audit_logs` dentro de `onRecordEnrich`.
- Suspensos os hooks de leitura em `0.0.26`; QA passou, mas testes automatizados não rodaram. Reteste autenticado de colaboradores/setores e APIs master-data respondeu 200. Trilha de leitura ficou temporariamente suspensa, sem uso de dados reais.
- Há POST de departments em tentativas 500/400 e posterior 200; conferir registro antes de repetir inserção.
- Debug Summary: `06_notas/debug/debug-2026-10-11-f1-t05-enrichment-500.md`.

## 2026-10-09 · [Marcela] · DEBUG F1-T05: integração do cadastro mestre no preview
- Migrations `0004`–`0009` aplicadas em etapas para departamentos, colaboradores, tomadores, projetos, contratos, relações, fixtures sintéticas, índices e RBAC. Login PocketBase; removidos fallback local e credenciais demo; produção preservada em `2b24bd5`.

## 2026-09-24 · F1-T04: instrumentação de baseline homologada
- T0, T1, touch time e lead time implementados e homologados na versão `0.0.12`; baseline real e decisão Stelanto permanecem explicitamente pendentes até fechamento real medido.

## 2026-09-24 · F1-T03: prova de exportação e retorno contábil aprovada
- Relatório aprovado pela Champion; provas read-only de Stelanto/Flipchart e cadeia de e-mails da contabilidade registradas sem publicar credenciais ou dados pessoais.
