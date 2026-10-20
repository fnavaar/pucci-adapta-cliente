# Debug Summary — F1-T05 · edição de tomadores

- **Task/SPEC:** F1-T05 · `04_fase-atual/specs/spec-1-002.md`.
- **Sintoma:** Champion precisava corrigir um tomador real, mas a tela só permitia cadastrar/listar.
- **Causa raiz:** `tomadorService.update`, regra de atualização e trilha já existiam; `src/pages/MasterData.tsx` não tinha ação nem fluxo de edição.
- **Correção:** botão Editar e diálogo pré-preenchido para razão social, nome fantasia e CNPJ; status preservado; mensagem clara para CNPJ duplicado; campos e ações com alvos de toque adequados; confirmação antes de descartar alterações; atualização local da lista sem uma nova consulta aos tomadores; fixture `CNPJ-SINTETICO-01` sem ação de edição.
- **Dados:** nenhuma leitura ou alteração de tomadores reais pelo agente. Nenhuma mudança no banco.
- **QA:** Skip `0.0.31` (`5191b26`); setup, análise estática, build e integrações passaram. `test.ran=false` — a plataforma não executou testes automatizados.
- **Publicação:** produção `https://rh-pucci-3116c.goskip.app`; Skip confirmou `lastPublishedRef=5191b26` em 2026-10-20.
- **Gate atual:** aguardando teste humano da Champion em produção. F1-T05 segue aberta; não iniciar F1-T06 antes do fechamento.
