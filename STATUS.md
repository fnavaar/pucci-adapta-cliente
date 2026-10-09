# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-10-09 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado (5 fases); SPECs F1 e tasks F1-T01..T08 publicadas.
- **Champion:** Marcela — definida pela CEO em 18/09/2026, executora e homologadora única das tasks, responsável pelo aceite, pela política de dados e pelas exceções.
- **Execução autorizada:** Marcela conduz priorização, execução, validação e conclusão de todas as tasks; nenhum conflito de responsável deve pausar tasks.
- **Tasks concluídas:** 4/8 (50%). F1-T01 concluída após aprovação escrita da política e matriz versão 0.1; F1-T02 concluída em 22/09/2026 após QA da versão `0.0.6` e homologação humana dos passos 3 a 10; F1-T03 concluída em 24/09/2026 após relatório aprovado; F1-T04 concluída em 24/09/2026 quanto à instrumentação e homologação da medição. F1-T05 ainda não conta como concluída: aguarda teste humano.
- **F1-T02:** concluída no ambiente homologado `RH Pucci`/preview. Critérios CA-1-010 a CA-1-013 comprovados com fixtures sintéticas; nenhum dado real foi usado.
- **F1-T03:** concluída. O relatório em `03_documentos/provas/relatorio-prova-f1-t03.md` registra as provas read-only do Stelanto e do Flipchart, a cadeia real de e-mails com a contabilidade e o retorno com 6 PDFs da competência 08/2026. Marcela confirmou que a cadeia representa o processo real e aprovou o relatório.
- **F1-T04:** concluída quanto à instrumentação e homologação. O relatório em `03_documentos/provas/relatorio-baseline-f1-t04.md` registra t0, t1, touch time, cálculo de lead time, validação server-side, proteção após fechamento e o aceite humano. Ainda não existe fechamento real medido; por isso o baseline operacional e a decisão de integrar/substituir o Stelanto permanecem pendentes explicitamente.
- **Evidência técnica da F1-T04:** migration `0002_f1_t04_touch_time` aplicada; coleção `competencies` contém `touch_time_minutes` inteiro não negativo; versão Skip `0.0.12` (`d36e32a`) passou no QA completo; logs do teste no preview registraram criação/consulta de competências com HTTP 200.
- **F1-T05 — status:** implementada no preview `0.0.25` (`1279dde`), aguardando homologação humana. O novo layout usa PocketBase, sem fallback `localStorage` e sem credenciais de demonstração. Backend live tem departamentos, colaboradores, tomadores, projetos e contratos; relações e índices únicos aplicados; fixtures marcadas como sintéticas (`SYN-*`, `example.test`, `CNPJ-SINTETICO-*`), sem dados pessoais reais.
- **Segurança F1-T05:** departamentos/colaboradores permitem leitura a Champion, Analista e Financeiro; escrita de RH restrita a Champion/Analista. Projetos são graváveis por Champion/Analista; Financeiro mantém leitura sem escrita. Tomadores/contratos seguem escopo fiscal da matriz. Hooks de auditoria do cadastro mestre registram ator, ação, coleção, ID e nomes de campos, sem valores pessoais. A chamada a `e.requestInfo()` nos hooks de leitura foi corrigida para a assinatura documentada; filtro de erros de hooks retornou 0 entradas.
- **QA F1-T05:** versão `0.0.25` (`1279dde`) passou em setup, análise estática, build e integrações; o runner reportou `test.ran=false`, então não houve execução de testes automatizados. Logs recentes confirmam leituras autenticadas de `departments` e `employees` com HTTP 200. A leitura autenticada de tomadores/projetos/contratos e a auditoria em runtime ainda precisam do teste humano no preview.
- **Produção:** F1-T05 não foi publicada. `lastPublishedRef` permanece `2b24bd5`; o preview, não a produção, contém o trabalho desta task.
- **Recomendação vigente:** Stelanto permanece como fonte oficial do ponto neste ciclo. A decisão de substituir ou integrar será tomada somente após o primeiro fechamento real medido.
- **Ambiente oficial:** Skip `RH Pucci` (projectId `59746`), na organização `Org de Luisa`; Skip Cloud em execução.
- **B-ENV-01:** ambiente definido e provisionado; QA e validações técnicas passaram.
- **B-GOV-01:** política/matriz aprovadas e controles técnicos homologados no preview. Nenhuma credencial ou dado pessoal foi publicado no repositório.

## Ambiente oficial do projeto

- **Projeto Skip:** `RH Pucci` · ID `59746`
- **Skip Cloud:** `rh-pucci-3116c` · status `running`
- **Preview atual:** `https://rh-pucci-3116c--preview.goskip.app` · versão `0.0.25` (`1279dde`), aguardando homologação da F1-T05.
- **Backend:** https://rh-pucci-3116c.shrd00.internal.goskip.dev
- **Produção:** não atualizada para esta task; `lastPublishedRef=2b24bd5`.
- **Política de execução:** tarefas futuras serão implementadas nesse projeto, uma por vez, seguindo a SPEC e os gates; nenhum dado real será usado sem confirmação do ambiente autorizado.

## Próximo passo
Testar a F1-T05 no preview com os cadastros sintéticos. Depois do aceite, fechar a task; não iniciar F1-T06 automaticamente. B-MET-01 e B-STE-01 permanecem pendentes até o primeiro fechamento real medido.

## Bloqueios ativos
B-MET-01 permanece: ainda falta um fechamento real medido, sem dados pessoais, para produzir o baseline. B-STE-01 permanece: decisão integrar/substituir Stelanto ainda aberta até existir o baseline. B-FISC-01 permanece para a F1-T07. B-IMP-01 foi respondido com evidência e recomendação de formato/fallback.
