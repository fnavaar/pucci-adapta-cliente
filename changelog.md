# Changelog — Pucci Ambiental · adapta-cliente

## 2026-09-23 — F1-T03: prova read-only do Stelanto aprovada parcialmente
- Marcela executou o teste humano no preview da versão `0.0.7` e informou: “funcionou”.
- Logs do Skip confirmaram duas chamadas autenticadas `POST /backend/v1/stelanto/mirror-view` com HTTP 200; a chamada sem sessão anterior respondeu HTTP 401.
- A prova exibiu o retorno estruturado do Stelanto para o período testado, com formato JSON, via, granularidade e resumo por colaborador/dias/batidas.
- Nenhum token foi exposto e nenhuma resposta de colaborador foi copiada para o repositório.
- Subprova Stelanto aprovada; F1-T03 permanece aberta porque ainda faltam a prova do Flipchart e a amostra do retorno da contabilidade.
- Próximo passo: obter contrato técnico do Flipchart e implementar a prova read-only correspondente; coletar a amostra real devolvida pela contabilidade.

## 2026-09-22 — F1-T03: fluxo da contabilidade por e-mail esclarecido
- Marcela informou que a Pucci não tem acesso ao sistema da contabilidade.
- O fluxo real é: a Pucci envia informações por e-mail para a contabilidade; a contabilidade devolve informações por e-mail para a confecção da folha.
- A evidência da contabilidade na F1-T03 será a cadeia real de e-mails e os anexos necessários, sem exigir acesso ao sistema contábil.
- Acesso read-only ao Stelanto e ao Campos Solo–Flipchart continua pendente.
- F1-T03 permanece em `aguardando_autorizacao`; nenhum produto foi alterado e nenhuma prova foi executada.

## 2026-09-22 — F1-T03 selecionada; análise concluída, autorização pendente
- Próxima task elegível da Fase 1: **Provar como o Stelanto e o Flipchart exportam seus dados**.
- SPEC-1-004 · critérios CA-1-014 e CA-1-017 · Leva 2.
- Nenhum arquivo de produto foi alterado; nenhuma exportação foi executada.
- Pré-condições ainda pendentes: acesso read-only ao Stelanto e ao Campos Solo–Flipchart; cadeia real de e-mails enviada pela Pucci à contabilidade e resposta recebida, com anexos quando existirem.
- Próximo gate: autorização da champion para implementar a prova técnica e disponibilização dos acessos.
