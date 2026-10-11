# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-10-11 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado; SPECs da Fase 1 publicadas.
- **Champion:** Marcela, executora e homologadora das tasks.
- **Tasks concluídas:** 4/8 (50%). F1-T01 a F1-T04 permanecem concluídas nos limites registrados. F1-T05 ainda não foi encerrada; teste humano parcial.
- **F1-T05 — reteste no preview:** versão `0.0.26` (`156263c`). Marcela confirmou que as listagens de colaboradores e setores abriram. Logs autenticados em 2026-10-11 entre 17:21 e 17:27 UTC mostram GET HTTP 200 para `employees`, `departments`, `tomadores`, `projects` e `contracts`. Isso comprova chamadas da API, mas a Champion ainda precisa confirmar visualmente a tela `/cadastros`.
- **Correção diagnóstica:** cinco hooks de leitura `onRecordEnrich` foram temporariamente suspensos após HTTP 500 em `0.0.25`. As leituras 200 surgiram após a alteração; a causa individual não foi isolada por hook. Auditoria de leitura permanece desativada. Não inserir dados pessoais reais até essa auditoria ser restaurada e validada.
- **Criação de department:** logs registram POST HTTP 200 às 17:25:55 UTC após tentativas anteriores com 500/400. Conferir se o registro sintético existe antes de criar outro.
- **QA:** setup, análise estática, build e integrações passaram em `0.0.26`; runner `test.ran=false`, sem testes automatizados. Consulta de erros não mostra falha após 17:18 UTC.
- **Produção:** não publicada; `lastPublishedRef=2b24bd5`. F1-T04 preservada.
- **Próximo passo:** Champion confirmar visualmente `/cadastros` e seus registros sintéticos. Não concluir F1-T05 nem iniciar F1-T06 antes do aceite.

## Ambiente
- Preview: `https://rh-pucci-3116c--preview.goskip.app` · versão `0.0.26` (`156263c`).
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção: https://rh-pucci-3116c.goskip.app · referência publicada `2b24bd5`.
- B-MET-01 e B-STE-01 permanecem pendentes até primeiro fechamento real medido.
