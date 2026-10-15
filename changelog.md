# Changelog — Pucci Ambiental · adapta-cliente

## 2026-10-15 · [Marcela] · F1-T05 trilha de cinco coleções confirmada em produção; aguarda cadastros mestres reais
- Marcela confirmou que, em produção `0.0.29` (`3545c75`), após clicar “Atualizar trilha”, aparecem as cinco coleções; logs do backend mostram GET HTTP 200 de `audit_logs` às 10:31 UTC. O conteúdo é aceite humano da Champion; o HTTP 200 sozinho não foi tratado como prova de conteúdo.
- O aceite de produção cobre telas (Colaboradores, Setores/Departamentos, Fechamento Operacional) e visibilidade da tabela da trilha. Em 2026-10-14, Marcela informou que nenhum cadastro real havia sido lançado nos formulários. A descrição da F1-T05 exige cadastro mestre real depois da liberação da política.
- Próxima ação: Marcela cadastrar em produção apenas os registros mestres necessários (colaboradores, setores, tomadores, projetos/obras e contratos), conforme política/matriz aprovada. Não enviar dados pessoais pelo chat. Após confirmação sem detalhes, verificar listas/trilha e só então fechar F1-T05.
- F1-T05 permanece ativa; não iniciar F1-T06 até o fechamento formal.
- QA da `0.0.29`: setup, análise estática, build e integrações passaram; `test.ran=false`.

## 2026-10-15 · [Marcela] · F1-T05 produção publicada e telas confirmadas; trilha aguarda reteste
- Marcela confirmou visualmente as telas de Colaboradores, Setores/Departamentos e Fechamento Operacional em produção. O Skip confirma `lastPublishedRef=3545c75` (`0.0.29`); não foi feita publicação pelo agente nesta rodada.
- Logs em 2026-10-15 10:18–10:19 UTC mostram HTTP 200 nas listagens de `employees`, `departments`, `tomadores`, `projects` e `contracts`. Esses status não demonstram os eventos gravados em `audit_logs`.
- A auditoria das cinco coleções foi aceita em preview em 2026-10-14, mas falta comprovar a trilha na produção: após clicar “Atualizar trilha”, conferir `read/identification` em `employees`, `departments`, `tomadores`, `projects` e `contracts`. Usar somente fixtures sintéticas; não inserir cadastros reais nem enviar dados pessoais no chat durante este gate.
- F1-T05 permanece ativa; não iniciar F1-T06 até aprovação humana deste teste em produção.
- QA da `0.0.29`: setup, análise estática, build e integrações passaram; `test.ran=false`.

## 2026-10-14 · [Marcela] · F1-T05 auditoria de leitura aprovada em 0.0.29 (preview)
- A Champion confirmou a trilha com coluna `collection_name`: eventos `read/identification` para `employees`, `departments`, `tomadores`, `projects` e `contracts` em preview `0.0.29` (`3545c75`). A lista de 14:42 inclui departments/projects/contracts; a Champion também confirmou tomadores e employees. Logs do backend mostram HTTP 200 nas listagens master-data e nas consultas da trilha.
- QA de `0.0.29` passou em setup, análise estática, build e integrações; `test.ran=false`. Nenhum teste automatizado foi executado. Produção preservada em `lastPublishedRef=2b24bd5` naquele momento.
- **F1-T05 permanece ativa somente para confirmar o item textual da descrição:** carregar os cadastros reais depois da política aprovada. Pedir apenas confirmação de execução, sem solicitar dados pessoais pelo chat. Não iniciar F1-T06 antes do fechamento formal.
- Leitura de fixture `sensitive_payroll` é prova separada de F1-T02, não se confunde com o cadastro mestre F1-T05.

## 2026-10-14 · [Marcela] · DEBUG F1-T05: tabela da trilha passa a exibir coleção
- Adicionada a coluna `collection_name` na UI de auditoria em `src/pages/Index.tsx`; QA de `0.0.29` (`3545c75`) passou em setup, estática, build e integrações. Teste humano por coleção aprovado na rodada seguinte.

## 2026-10-11 · [Marcela] · DEBUG F1-T05: listagens recuperadas após suspensão de hooks de enriquecimento
- Logs de `0.0.25` mostraram HTTP 500 `Failed to enrich records`; hooks tentavam gravar auditoria em `onRecordEnrich`. Suspensos hooks de leitura em `0.0.26`; QA passou e listagens autenticadas responderam HTTP 200. Causa individual não foi isolada. Dados reais permaneceram bloqueados.
- Debug Summary: `06_notas/debug/debug-2026-10-11-f1-t05-enrichment-500.md`.

## 2026-10-09 · [Marcela] · DEBUG F1-T05: integração do cadastro mestre no preview
- Migrations `0004`–`0009` aplicadas em etapas para cadastro mestre, relações, fixtures sintéticas, índices e RBAC. Login PocketBase; produção preservada em `2b24bd5`.

## 2026-09-24 · F1-T04: instrumentação de baseline homologada
- T0, T1, touch time e lead time implementados/homologados em `0.0.12`; baseline real e decisão Stelanto seguem pendentes até primeiro fechamento real medido.

## 2026-09-24 · F1-T03: prova de exportação e retorno contábil aprovada
- Relatório aprovado pela Champion; provas read-only de Stelanto/Flipchart e cadeia contábil sem publicação de credenciais ou dados pessoais.
