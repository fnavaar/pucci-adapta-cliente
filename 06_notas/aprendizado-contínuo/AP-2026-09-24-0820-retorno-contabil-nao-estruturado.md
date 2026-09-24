# AP-2026-09-24-0820 — Retorno contábil não estruturado exige conferência por totais

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T03 / `04_fase-atual/specs/spec-1-004.md`
- Sinal: Stelanto e Flipchart demonstraram retorno estruturado por rotas read-only; a contabilidade devolveu a folha exclusivamente em seis PDFs anexados a e-mail. Os códigos de eventos enviados pela Pucci puderam ser rastreados nos PDFs, mas o retorno não é um formato confiável para importação direta.
- Evidência: `03_documentos/provas/relatorio-prova-f1-t03.md`; logs do Skip com HTTP 200 nas rotas autenticadas e HTTP 401 sem sessão; seis PDFs da competência 08/2026 analisados no ciclo.
- Regra reutilizável: antes de implementar uma importação, classificar cada fonte pelo formato, granularidade, via e capacidade de retorno. Quando o contador devolver apenas PDF, gerar a entrada estruturada na origem e comparar os totais consolidados do retorno; não tratar o PDF bruto como contrato de importação.
- Quando aplicar: em integrações com contabilidade ou fornecedores que respondem por e-mail com documentos renderizados, especialmente quando a entrada já contém eventos codificados e a saída precisa ser conferida.
- Quando não aplicar: se o fornecedor oferecer CSV/XLSX/API com esquema estável, identificadores e totais conciliáveis; nesse caso, validar o contrato estruturado antes de escolher a conferência por PDF.
- Confiança: alta — padrão observado na cadeia real de e-mails e nos seis PDFs, com rastreabilidade dos eventos registrada no relatório aprovado pela champion.
- Privacidade: sem segredo, credencial, dado pessoal ou conteúdo bruto.
