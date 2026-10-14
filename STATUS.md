# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-10-14 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- **Tasks concluídas:** 4/8 (50%). F1-T01 a F1-T04 concluídas nos limites registrados. F1-T05 segue ativa; não iniciar F1-T06 ainda.
- **F1-T05 — cadastro visual:** Champion aprovou `/colaboradores`, `/setores` e `/cadastros` com fixtures em `0.0.26`; as cinco APIs master-data retornaram HTTP 200.
- **F1-T05 — auditoria de leitura:** aprovada por teste humano em `0.0.29` (`3545c75`). Marcela confirmou `read/identification` para `employees`, `departments`, `tomadores`, `projects` e `contracts`; a UI mostra `collection_name`. QA passou em setup, estática, build e integrações; `test.ran=false` (sem testes automatizados).
- **Única confirmação pendente:** a descrição da F1-T05 pede carregar os cadastros reais após a política aprovada. Perguntar somente se essa carga autorizada ocorreu; não copiar/solicitar nomes, CNPJs ou identificadores pelo chat. Fechar F1-T05 após essa confirmação e revalidar o registro da execução.
- **Produção:** preservada em `lastPublishedRef=2b24bd5`; nenhuma publicação desta correção.
- **F1-T04:** preservada; B-MET-01/B-STE-01 aguardam o primeiro fechamento real medido.

## Ambiente
- Preview: `https://rh-pucci-3116c--preview.goskip.app` · `0.0.29` (`3545c75`).
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção: https://rh-pucci-3116c.goskip.app · referência publicada `2b24bd5`.
