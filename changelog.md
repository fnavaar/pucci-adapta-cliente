# Changelog — Pucci Ambiental · adapta-cliente

## 2026-10-14 · [Marcela] · DEBUG F1-T05: teste parcial de auditoria em 0.0.29
- Após adicionar `collection_name` à tabela da trilha e passar QA em `0.0.29` (`3545c75`), Marcela enviou a leitura autenticada: `employees` e `departments` têm eventos `read/identification`. Há também uma leitura separada da fixture `sensitive_payroll`; ela não conta para a cobertura cadastral da F1-T05.
- A evidência enviada não mostra `tomadores`, `projects` ou `contracts`; portanto a trilha permanece parcialmente validada e a task aberta. Não inferir que os hooks falharam: as três coleções podem não ter sido consultadas nesta sessão.
- Próximo passo: abrir `/cadastros` no preview `0.0.29` para consultar as três coleções, depois atualizar a trilha em `/fechamento` e confirmar `read/identification` para cada uma. Usar somente fixtures; não inserir dados reais.
- Produção continua em `lastPublishedRef=2b24bd5`.

## 2026-10-14 · [Marcela] · DEBUG F1-T05: coluna de coleção na trilha; reteste 0.0.29 pendente
- A tabela da trilha foi atualizada para mostrar `collection_name`; QA de setup, análise estática, build e integrações passou, mas `test.ran=false`. Reteste humano por coleção ficou pendente.

## 2026-10-11 · [Marcela] · DEBUG F1-T05: listagens recuperadas após suspensão de hooks de enriquecimento
- Logs de `0.0.25` mostraram HTTP 500 `Failed to enrich records`; hooks tentavam gravar auditoria em `onRecordEnrich`. Suspensos hooks de leitura em `0.0.26`; QA passou e listagens autenticadas responderam HTTP 200. Causa individual não foi isolada. Dados reais permaneceram bloqueados.
- Debug Summary: `06_notas/debug/debug-2026-10-11-f1-t05-enrichment-500.md`.

## 2026-10-09 · [Marcela] · DEBUG F1-T05: integração do cadastro mestre no preview
- Migrations `0004`–`0009` aplicadas em etapas para cadastro mestre, relações, fixtures sintéticas, índices e RBAC. Login PocketBase; produção preservada em `2b24bd5`.

## 2026-09-24 · F1-T04: instrumentação de baseline homologada
- T0, T1, touch time e lead time implementados/homologados em `0.0.12`; baseline real e decisão Stelanto seguem pendentes até primeiro fechamento real medido.

## 2026-09-24 · F1-T03: prova de exportação e retorno contábil aprovada
- Relatório aprovado pela Champion; provas read-only de Stelanto/Flipchart e cadeia contábil sem publicação de credenciais ou dados pessoais.
