# Changelog — Pucci Ambiental · adapta-cliente

## 2026-09-24 · [Marcela] · DEBUG task F1-T04: página em branco → causa raiz ReferenceError por funções ausentes → corrigido
- O card de competência chamava `formatMinutes` e `getElapsedMinutes`, mas as funções não estavam presentes em `src/pages/Index.tsx`; a exceção de runtime deixava a tela em branco quando havia linhas para renderizar.
- Correção mínima aplicada no mesmo escopo da F1-T04; versão Skip `0.0.12` (`d36e32a`).
- QA completo passou: setup, análise estática, build, integrações e testes. Preview abre sem autenticação; logs não registram erros novos de hooks.
- A senha sintética não estava disponível para reproduzir o fluxo autenticado nesta sessão; não foi inventada nem foi usada credencial real. Novo teste humano permanece obrigatório.

## 2026-09-24 — F1-T03 concluída: prova técnica de exportação e retorno contábil
- Marcela confirmou: “Sim, a cadeia registrada representa o processo real. Relatório está sim aprovado.”
- Relatório aprovado em `03_documentos/provas/relatorio-prova-f1-t03.md`, com dados pessoais omitidos.
- CA-1-014 e CA-1-017 comprovados: Stelanto e Flipchart demonstraram retorno estruturado por rotas read-only; a cadeia real da contabilidade foi registrada com o e-mail de resposta e seis PDFs da competência 08/2026.
- Logs do Skip confirmaram Stelanto `POST /backend/v1/stelanto/mirror-view` autenticado HTTP 200 e sem sessão HTTP 401; Flipchart `GET /backend/v1/flipchart/consulta` autenticado HTTP 200 e sem sessão HTTP 401.
- Rastreabilidade entrada→retorno confirmada para os eventos contábeis; recomendação registrada: entrada estruturada na origem e conferência por totais quando o retorno da contabilidade for exclusivamente PDF, com fallback CSV/XLSX ou extração assistida.
- Nenhum token, credencial ou dado pessoal foi publicado no repositório.
- Próximo passo: iniciar a análise da F1-T04 em novo ciclo solicitado pela champion; CA-1-015 e CA-1-016 continuam fora do fechamento da F1-T03.

## 2026-09-23 — F1-T03: prova read-only do Flipchart aprovada parcialmente
- Marcela executou o teste humano no preview da versão `0.0.8` e informou: “funcionou”.
- Logs do Skip confirmaram a chamada autenticada `GET /backend/v1/flipchart/consulta?dataInicio=2026-08-01&dataFim=2026-08-31` com HTTP 200; a tentativa sem sessão respondeu HTTP 401.
- A prova exibiu o retorno estruturado do Flipchart com formato JSON, via, granularidade, campos e fontes.
- Nenhum token foi exposto e nenhuma resposta com registros foi copiada para o repositório.
- Subprovas Stelanto e Flipchart aprovadas; F1-T03 permanece aberta somente pela amostra do retorno da contabilidade.
- Próximo passo: obter a cadeia/amostra real devolvida pela contabilidade por e-mail, com anexos necessários e dados mascarados quando aplicável; depois consolidar o relatório da F1-T03.

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
