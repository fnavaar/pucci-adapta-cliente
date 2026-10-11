# Changelog — Pucci Ambiental · adapta-cliente

## 2026-10-11 · [Marcela] · DEBUG F1-T05: listagem falha durante enriquecimento
- Após a Champion relatar falha no teste humano, logs do preview `0.0.25` mostram listagens de `employees` e `departments` com HTTP 500 `Failed to enrich records.` depois de login HTTP 200.
- Hipótese: os hooks de leitura gravavam em `audit_logs` de dentro de `onRecordEnrich`. Suspendi temporariamente os cinco hooks de leitura; não alterei RLS nem hooks de escrita.
- QA `0.0.26` (`156263c`) passou em setup, análise estática, build e integrações; `test.ran=false`, sem testes automatizados. Sem sessão Champion não há request pós-build, portanto a correção ainda não foi comprovada no runtime.
- Logs separados mostram POST `departments` HTTP 500 `Failed to enrich record.` e depois HTTP 400 `Failed to create record.`. Sem payload nem erro interno, não afirmar rollback/persistência; confirmar se o código sintético já existe antes de repetir criação.
- Preview `0.0.26`; produção permanece em `2b24bd5`. F1-T05 continua aberta, agora aguardando reteste humano autenticado, primeiro somente leitura de colaboradores e setores.
- Debug Summary: `06_notas/debug/debug-2026-10-11-f1-t05-enrichment-500.md`.

## 2026-10-09 · [Marcela] · DEBUG F1-T05: integração do cadastro mestre no preview
- Retomada da task ativa sem abrir outra frente. Diagnóstico da falha de migration: a `0004` mínima falhou enquanto os novos hooks de cadastro mestre estavam no working tree e passou após remover esses hooks; o Skip não expôs stack trace que isolasse um arquivo específico. Regra aplicada: criar schema em migrations ordenadas; instalar hooks que referenciam as coleções depois do schema.
- Migrations `0004` a `0009` aplicadas no Skip Cloud: departamentos, colaboradores, tomadores, projetos e contratos; relações colaborador→departamento, projeto→tomador, contrato→projeto/tomador; fixtures explicitamente sintéticas e índices únicos.
- RLS verificado: departamentos/colaboradores legíveis por Champion, Analista e Financeiro; escrita de RH restrita a Champion/Analista. Projetos agora são graváveis por Champion/Analista; Financeiro mantém somente leitura. Tomadores/contratos seguem escopo fiscal da matriz. Auditoria append-only registra ator, ação, coleção, id e nomes de campos, nunca valores pessoais.
- Novo layout: login somente PocketBase, sem credencial demo nem fallback local; telas de colaboradores e setores consultam backend; nova tela `/cadastros` consulta tomadores, projetos/obras e contratos; `/fechamento` mantém o módulo F1-T04 protegido.
- Hooks de auditoria de leitura corrigidos para chamar `e.requestInfo()` como método documentado. Logs não registraram erros de hooks no filtro consultado; execução real dos novos hooks ainda requer verificação humana autenticada.
- QA Skip `0.0.25` (`1279dde`): setup, análise estática, build e integrações passaram. O estágio de testes reportou `ran:false`; testes automatizados não foram executados. Logs confirmam leituras autenticadas de `departments` e `employees` HTTP 200; ainda falta a Champion validar as telas de tomadores/projetos/contratos.
- Preview atualizado para `0.0.25`; produção não publicada, `lastPublishedRef=2b24bd5`. F1-T04 preservada. Nenhum dado real foi inserido.
- F1-T05 aguarda teste humano da Champion; progresso da fase permanece 4/8 (50%) até o aceite.
- Debug: `06_notas/debug/debug-2026-10-09-f1-t05-migration-hooks.md`. Aprendizado: `06_notas/aprendizado-contínuo/AP-2026-10-09-1621-ordenar-schema-e-hooks-skip.md`.

## 2026-09-24 · [Marcela] · Task F1-T04 concluída: instrumentação de baseline homologada
- Marcela executou o teste humano da versão `0.0.12` e confirmou: “Fiz o teste de tudo, pode continuar”.
- Instrumentação homologada: t0 automático na abertura, t1 automático no encerramento, touch time obrigatório em minutos, cálculo do lead time total (`t1 - t0`) e bloqueio de reabertura/alteração após fechamento.
- Migration `0002_f1_t04_touch_time` aplicada no Skip Cloud; QA `0.0.12` (`d36e32a`) passou em setup, análise estática, build, integrações e testes.
- Relatório: `03_documentos/provas/relatorio-baseline-f1-t04.md`.
- **CA-1-015:** pendência explícita — ainda não houve fechamento real medido; não foi inventado baseline operacional.
- **CA-1-016:** pendência explícita — Stelanto permanece fonte oficial neste ciclo; decisão integrar/substituir segue aberta até existir baseline real.
- Próximo passo: medir o primeiro fechamento real autorizado e então registrar o baseline e a decisão sobre o Stelanto.

## 2026-09-24 · [Marcela] · DEBUG task F1-T04: página em branco → causa raiz ReferenceError por funções ausentes → corrigido
- O card de competência chamava `formatMinutes` e `getElapsedMinutes`, mas as funções não estavam presentes em `src/pages/Index.tsx`; a exceção de runtime deixava a tela em branco quando havia linhas para renderizar.
- Correção mínima aplicada no mesmo escopo da F1-T04; versão Skip `0.0.12` (`d36e32a`).
- QA completo passou: setup, análise estática, build, integrações e testes. Preview abre sem autenticação; logs não registram erros novos de hooks.
- A senha sintética não estava disponível para reproduzir o fluxo autenticado nesta sessão; não foi inventada nem foi usada credencial real. Novo teste humano permanece obrigatório.

## 2026-09-24 — F1-T03 concluída: prova técnica de exportação e retorno contábil
- Marcela confirmou: “Sim, a cadeia registrada representa o processo real. Relatório está sim aprovado.”
- Relatório aprovado em `03_documentos/provas/relatorio-prova-f1-t03.md`, com dados pessoais omitidos.
- CA-1-014 e CA-1-017 comprovados: Stelanto e Flipchart demonstraram retorno estruturado por rotas read-only; a cadeia real de e-mails com a contabilidade e o retorno com seis PDFs da competência 08/2026 foram registrados.
- Logs do Skip confirmaram Stelanto `POST /backend/v1/stelanto/mirror-view` autenticado HTTP 200 e sem sessão HTTP 401; Flipchart `GET /backend/v1/flipchart/consulta` autenticado HTTP 200 e sem sessão HTTP 401.
- Rastreabilidade entrada→retorno confirmada; recomendação: entrada estruturada na origem e conferência por totais quando retorno for PDF, com fallback CSV/XLSX ou extração assistida.
- Nenhum token, credencial ou dado pessoal foi publicado no repositório.

## 2026-09-23 — F1-T03: prova read-only do Flipchart aprovada parcialmente
- Marcela executou o teste humano no preview da versão `0.0.8` e informou: “funcionou”.
- Logs do Skip confirmaram a chamada autenticada `GET /backend/v1/flipchart/consulta?dataInicio=2026-08-01&dataFim=2026-08-31` com HTTP 200; a tentativa sem sessão respondeu HTTP 401.
- A prova exibiu o retorno estruturado do Flipchart com formato JSON, via, granularidade, campos e fontes.
- Nenhum token foi exposto e nenhuma resposta com registros foi copiada para o repositório.
- Subprovas Stelanto e Flipchart aprovadas; F1-T03 permaneceu aberta pela amostra do retorno da contabilidade.

## 2026-09-23 — F1-T03: prova read-only do Stelanto aprovada parcialmente
- Marcela executou o teste humano no preview da versão `0.0.7` e informou: “funcionou”.
- Logs do Skip confirmaram duas chamadas autenticadas `POST /backend/v1/stelanto/mirror-view` com HTTP 200; a chamada sem sessão respondeu HTTP 401.
- A prova exibiu retorno estruturado do Stelanto; nenhum token ou dado de colaborador foi copiado para o repositório.

## 2026-09-22 · F1-T03: fluxo da contabilidade por e-mail esclarecido
- Marcela informou que a Pucci não tem acesso ao sistema da contabilidade.
- O fluxo real é: a Pucci envia informações por e-mail para a contabilidade; a contabilidade devolve informações por e-mail para a confecção da folha.
- A evidência da contabilidade na F1-T03 será a cadeia real de e-mails e os anexos necessários, sem exigir acesso ao sistema contábil.

## 2026-09-22 · F1-T03 selecionada; análise concluída, autorização pendente
- Próxima task elegível da Fase 1: **Provar como o Stelanto e o Flipchart exportam seus dados**.
- SPEC-1-004 · critérios CA-1-014 e CA-1-017 · Leva 2.
- Próximo gate: autorização da champion e disponibilização dos acessos.
