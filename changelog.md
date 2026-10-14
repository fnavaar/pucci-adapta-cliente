# Changelog — Pucci Ambiental · adapta-cliente

## 2026-10-14 · [Marcela] · DEBUG F1-T05: coluna de coleção na trilha; reteste 0.0.29 pendente
- Marcela confirmou visualmente `/colaboradores`, `/setores` e `/cadastros` com fixtures sintéticas em `0.0.26` e validou o hook de leitura de employees com eventos `read/identification` em `0.0.27`.
- Em `0.0.28`, Champion forneceu 20 eventos de auditoria `read/identification`. A visualização não exibia `collection_name`, então esses eventos não podiam ser atribuídos com segurança às cinco coleções.
- Correção pontual em `src/pages/Index.tsx`: adicionar coluna “Coleção” e mostrar `log.collection_name` na tabela da trilha.
- QA Skip `0.0.29` (`3545c75`): setup, análise estática, build e integrações passaram; `test.ran=false`, sem testes automatizados. Diff confirmado. Produção preservada em `2b24bd5`.
- Próximo passo: Champion retestar no preview `0.0.29`, atualizar a trilha e verificar `read` para `employees`, `departments`, `tomadores`, `projects`, `contracts`, com campo `identification`. Usar apenas fixtures sintéticas; não inserir dados reais. Se algum hook falhar, depurar antes de fechar F1-T05.

## 2026-10-11 · [Marcela] · DEBUG F1-T05: listagens recuperadas após suspensão de hooks de enriquecimento
- Logs de `0.0.25` mostraram HTTP 500 `Failed to enrich records`; hooks tentavam gravar auditoria em `onRecordEnrich`. Suspensos hooks de leitura em `0.0.26`; QA passou e listagens autenticadas responderam HTTP 200. Causa individual não foi isolada. Dados reais permaneceram bloqueados.
- Debug Summary: `06_notas/debug/debug-2026-10-11-f1-t05-enrichment-500.md`.

## 2026-10-09 · [Marcela] · DEBUG F1-T05: integração do cadastro mestre no preview
- Migrations `0004`–`0009` aplicadas em etapas para cadastro mestre, relações, fixtures sintéticas, índices e RBAC. Login PocketBase; produção preservada em `2b24bd5`.

## 2026-09-24 · F1-T04: instrumentação de baseline homologada
- T0, T1, touch time e lead time implementados/homologados em `0.0.12`; baseline real e decisão Stelanto seguem pendentes até primeiro fechamento real medido.

## 2026-09-24 · F1-T03: prova de exportação e retorno contábil aprovada
- Relatório aprovado pela Champion; provas read-only de Stelanto/Flipchart e cadeia contábil sem publicação de credenciais ou dados pessoais.
