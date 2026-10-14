# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-10-14 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- **Tasks concluídas:** 4/8 (50%). F1-T01 a F1-T04 seguem concluídas nos limites registrados. F1-T05 continua ativa; ainda não fechar nem iniciar F1-T06.
- **F1-T05 — telas cadastrais:** Marcela aprovou `/colaboradores`, `/setores` e `/cadastros` com fixtures sintéticas em `0.0.26`. Logs daquela versão mostram HTTP 200 nas cinco APIs master-data.
- **F1-T05 — auditoria de leitura:** hook `onRecordsListRequest` de employees validado em `0.0.27`; Marcela apresentou eventos `read/identification` em `0.0.28`, mas a tela não exibia a coleção, impossibilitando comprovar cobertura de cada tabela. Corrigida a UI em `0.0.29` (`3545c75`) para exibir `collection_name` na trilha; QA passou em setup, estática, build e integrações. `test.ran=false`, então testes automatizados não rodaram.
- **Próximo passo:** reteste autenticado em `0.0.29`: `/fechamento` → “Controle de acesso e auditoria” → “Atualizar trilha”; confirmar evento `read` de employees, departments, tomadores, projects e contracts, todos com `identification`, usando fixtures apenas. Se algum estiver ausente, manter F1-T05 aberta e depurar. Não inserir dados reais.
- **Produção:** preservada em `lastPublishedRef=2b24bd5`; nenhuma publicação desta correção.
- **F1-T04:** preservada; B-MET-01/B-STE-01 aguardam o primeiro fechamento real medido.

## Ambiente
- Preview: `https://rh-pucci-3116c--preview.goskip.app` · `0.0.29` (`3545c75`).
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção: https://rh-pucci-3116c.goskip.app · referência publicada `2b24bd5`.
