# Debug Summary — F1-T05 · cadastro de contrato sem número

- **Task/SPEC:** F1-T05 · `04_fase-atual/specs/spec-1-002.md`.
- **Sintoma:** Marcela informou que o cadastro de um contrato real não foi salvo porque o formulário exige número, embora o contrato não tenha número oficial.
- **Evidência:** `src/pages/MasterData.tsx` marca o campo `contractNumber` como obrigatório, o submit recusa valor vazio e envia `contract_number`; a coleção `contracts` declara o campo como obrigatório e tem índice único `idx_contracts_number`.
- **Causa do bloqueio observável:** obrigatoriedade implementada tanto na tela quanto no schema.
- **Decisão ainda necessária:** a SPEC não define como identificar contratos que não têm número. Não inventar número oficial, placeholder nem identificador automático. Nenhum contrato real foi consultado ou alterado.
- **Gate:** aguardando decisão da Champion sobre identificador para contratos sem número; não alterar a regra nem iniciar F1-T06 antes dessa decisão.
