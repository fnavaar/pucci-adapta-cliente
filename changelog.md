# Changelog — Pucci Ambiental · adapta-cliente

## 2026-10-11 · [Marcela] · DEBUG F1-T05: listagens recuperadas no preview; cadastros aguardam confirmação visual
- Após a Champion relatar HTTP 500 nas listagens em `0.0.25`, suspendi temporariamente os cinco hooks de auditoria de leitura que escreviam em `audit_logs` durante `onRecordEnrich`; RLS e hooks de escrita foram mantidos.
- QA Skip `0.0.26` (`156263c`) passou em setup, análise estática, build e integrações; `test.ran=false`, então testes automatizados não executaram.
- Marcela confirmou: “Retestei no preview 0.0.26: as listagens de colaboradores e setores abriram.” Logs autenticados entre 17:21 e 17:27 UTC mostram GET HTTP 200 para `employees`, `departments`, `tomadores`, `projects` e `contracts`; a consulta de erros não mostra falhas posteriores a 17:18 UTC.
- Resultado é consistente com a hipótese de side effect em `onRecordEnrich`, mas a causa individual ainda não está isolada porque cinco hooks foram suspensos de uma vez. A auditoria de leitura permanece temporariamente desativada; não inserir dados reais até restaurá-la e validá-la.
- Há um POST de `departments` HTTP 200 às 17:25:55 UTC após tentativas anteriores com 500/400; consultar a listagem antes de criar outra fixture com o mesmo código.
- Produção não publicada: `lastPublishedRef=2b24bd5`. F1-T05 permanece aberta; as APIs responderam 200, mas falta a Champion confirmar visualmente a tela `/cadastros` e os registros sintéticos.
- Debug Summary: `06_notas/debug/debug-2026-10-11-f1-t05-enrichment-500.md`. Aprendizado candidato: `06_notas/aprendizado-contínuo/AP-2026-10-11-1428-isolar-hooks-de-enriquecimento.md`.

## 2026-10-09 · [Marcela] · DEBUG F1-T05: integração do cadastro mestre no preview
- Retomada da task ativa sem abrir outra frente. Diagnóstico da falha de migration: a `0004` mínima falhou enquanto os novos hooks de cadastro mestre estavam no working tree e passou após remover esses hooks; o Skip não expôs stack trace que isolasse um arquivo específico. Regra aplicada: criar schema em migrations ordenadas; instalar hooks que referenciam as coleções depois do schema.
- Migrations `0004` a `0009` aplicadas no Skip Cloud: departamentos, colaboradores, tomadores, projetos e contratos; relações colaborador→departamento, projeto→tomador, contrato→projeto/tomador; fixtures explicitamente sintéticas e índices únicos.
- RLS verificado: departamentos/colaboradores legíveis por Champion, Analista e Financeiro; escrita de RH restrita a Champion/Analista. Projetos graváveis por Champion/Analista; Financeiro mantém somente leitura. Tomadores/contratos seguem escopo fiscal da matriz. Auditoria append-only registra ator, ação, coleção, id e nomes de campos, nunca valores pessoais.
- Novo layout: login somente PocketBase, sem credencial demo nem fallback local; telas de colaboradores e setores consultam backend; nova tela `/cadastros` consulta tomadores, projetos/obras e contratos; `/fechamento` mantém o módulo F1-T04 protegido.
- Hooks de auditoria de leitura foram corrigidos para chamar `e.requestInfo()` como método documentado. QA `0.0.25` passou em setup, análise estática, build e integrações; `test.ran=false`. Depois, a Champion observou HTTP 500; no debug os hooks de leitura foram suspensos e o preview avançou para `0.0.26`.
- Produção permanece em `2b24bd5`; F1-T04 preservada. Nenhum dado real foi inserido.

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
- Marcela confirmou: “Sim, a cadeia registrada representa o processo real. Relatório aprovado em `03_documentos/provas/relatorio-prova-f1-t03.md`, com dados pessoais omitidos.
- CA-1-014/017 comprovados por provas read-only de Stelanto/Flipchart e cadeia real com a contabilidade; nenhum token/dado pessoal foi publicado no repositório.

## 2026-09-23 — F1-T03: provas read-only do Stelanto e Flipchart
- Marcela confirmou testes funcionais e logs autenticados HTTP 200; chamadas sem sessão retornaram HTTP 401. Respostas com registros não foram copiadas para o repositório.

## 2026-09-22 · F1-T03: fluxo da contabilidade por e-mail
- Pucci envia informações por e-mail à contabilidade e recebe retorno por e-mail; evidência não depende de acesso ao sistema contábil.

## 2026-09-22 · F1-T03 selecionada
- SPEC-1-004 · CA-1-014/017 · Leva 2. Próximo gate: autorização da Champion e acessos.
