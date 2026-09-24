# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-09-24 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado (5 fases); SPECs F1 e tasks F1-T01..T08 publicadas.
- **Champion:** Marcela — definida pela CEO em 18/09/2026, executora e homologadora única das tasks, responsável pelo aceite, pela política de dados e pelas exceções.
- **Execução autorizada:** Marcela conduz priorização, execução, validação e conclusão de todas as tasks; nenhum conflito de responsável deve pausar tasks.
- **Tasks concluídas:** 3/8 (37,5%). F1-T01 concluída após aprovação escrita da política e matriz versão 0.1; F1-T02 concluída em 22/09/2026 após QA da versão `0.0.6` e homologação humana dos passos 3 a 10; F1-T03 concluída em 24/09/2026 após relatório aprovado e comprovação dos critérios CA-1-014 e CA-1-017.
- **F1-T02:** concluída no ambiente homologado `RH Pucci`/preview. Critérios CA-1-010 a CA-1-013 comprovados com fixtures sintéticas; nenhum dado real foi usado.
- **F1-T03:** concluída. O relatório em `03_documentos/provas/relatorio-prova-f1-t03.md` registra as provas read-only do Stelanto e do Flipchart, a cadeia real de e-mails com a contabilidade e o retorno com 6 PDFs da competência 08/2026. Marcela confirmou que a cadeia representa o processo real e aprovou o relatório.
- **Evidência técnica da F1-T03:** Stelanto respondeu pela rota `POST /backend/v1/stelanto/mirror-view` com HTTP 200 autenticado e 401 sem sessão; Flipchart respondeu pela rota `GET /backend/v1/flipchart/consulta` com HTTP 200 autenticado e 401 sem sessão. Tokens permaneceram server-side.
- **Recomendação registrada:** como o retorno contábil é exclusivamente PDF, a entrada deve ser estruturada na origem e a conferência deve comparar totais do Resumo Mensal; fallback: solicitar CSV/XLSX ou usar extração assistida do PDF.
- **Ambiente oficial:** Skip `RH Pucci` (projectId `59746`), na organização `Org de Luisa`; Skip Cloud em execução.
- **B-ENV-01:** ambiente definido e provisionado; QA e validações técnicas das provas passaram.
- **B-GOV-01:** política/matriz aprovadas e controles técnicos homologados no preview. Nenhuma credencial ou dado pessoal foi publicado no repositório.

## Ambiente oficial do projeto

- **Projeto Skip:** `RH Pucci` · ID `59746`
- **Skip Cloud:** `rh-pucci-3116c` · status `running`
- **Preview usado na prova read-only:** versão `0.0.8`; rotas Stelanto e Flipchart homologadas por Marcela.
- **Backend:** https://rh-pucci-3116c.shrd00.internal.goskip.dev
- **Produção:** não foi usada como evidência da F1-T03.
- **Política de execução:** tarefas futuras serão implementadas nesse projeto, uma por vez, seguindo a SPEC e os gates; nenhum dado real será usado sem confirmação do ambiente autorizado.

## Próximo passo
Iniciar a análise da F1-T04 — medir o tempo do fechamento atual e registrar a decisão sobre o Stelanto — somente em novo ciclo solicitado pela champion.

## Bloqueios ativos
B-MET-01 e B-STE-01 permanecem para a F1-T04 (baseline de lead time e decisão sobre o Stelanto). B-FISC-01 permanece para a F1-T07 (confirmação formal da base de INSS). A F1-T03 não possui bloqueio ativo; B-IMP-01 foi respondido com evidência e recomendação de formato/fallback.
