# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-09-22 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado (5 fases); SPECs F1 (4) e tasks F1-T01..T08 publicadas.
- **Champion:** Marcela — definida pela CEO em 18/09/2026, executora e homologadora única das tasks, responsável pelo aceite, pela política de dados e pelas exceções.
- **Execução autorizada:** Marcela conduz priorização, execução, validação e conclusão de todas as tasks; nenhum conflito de responsável deve pausar o fluxo.
- **Tasks concluídas:** 1/8 (12,5%). F1-T01 concluída após aprovação escrita da política e matriz versão 0.1; CA-1-012 revalidado.
- **F1-T02:** versão `0.0.6` publicada no Skip `RH Pucci`; passos 3 e 4 do teste humano aprovados, passos 5 a 10 ainda pendentes; task não concluída.
- **Ambiente oficial:** Skip `RH Pucci` (projectId `59746`), na organização `Org de Luisa`; Skip Cloud em execução.
- **B-ENV-01:** ambiente definido e provisionado; QA e validação técnica da F1-T02 passaram.
- **B-GOV-01:** fechado quanto à aprovação documental da política; controles técnicos da F1-T02 implementados no preview, aguardando homologação humana completa.
- Dados reais continuam bloqueados até a homologação da F1-T02 e confirmação dos controles no uso do processo.

## Ambiente oficial do projeto

- **Projeto Skip:** `RH Pucci` · ID `59746`
- **Skip Cloud:** `rh-pucci-3116c` · status `running`
- **Preview:** https://rh-pucci-3116c--preview.goskip.app
- **Backend:** https://rh-pucci-3116c.shrd00.internal.goskip.dev
- **Produção:** https://rh-pucci-3116c.goskip.app — publicada conforme status verificado em 22/09/2026; a homologação desta task continua no preview.
- **Versão Skip:** `0.0.6`
- **Política de execução:** tarefas futuras serão implementadas nesse projeto, uma por vez, seguindo a SPEC e os gates; nenhum dado real será usado sem os controles comprovados.

## Próximo passo
Executar o passo 5 do teste humano da F1-T02 no preview: clicar em `Consultar registro` e confirmar que o registro recém-criado aparece com os valores sintéticos esperados. Não concluir a task nem iniciar a próxima antes da homologação completa.

## Bloqueios ativos
B-IMP-01 (formatos), B-MET-01 (baseline), B-FISC-01 (base INSS), B-STE-01 (Stelanto), passos 5 a 10 do teste humano da F1-T02 e a liberação de dados reais até a homologação — detalhados nas SPECs.
