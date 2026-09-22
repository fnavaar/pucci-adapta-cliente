# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-09-22 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado (5 fases); SPECs F1 (4) e tasks F1-T01..T08 publicadas.
- **Champion:** Marcela — definida pela CEO em 18/09/2026, executora e homologadora única das tasks, responsável pelo aceite, pela política de dados e pelas exceções.
- **Execução autorizada:** Marcela conduz priorização, execução, validação e conclusão de todas as tasks; nenhum conflito de responsável deve pausar o fluxo.
- **Tasks concluídas:** 1/8 (12,5%). F1-T01 concluída após aprovação escrita da política e matriz versão 0.1; CA-1-012 revalidado.
- **F1-T02:** versão `0.0.6` com correção visual no preview; passo 3 confirmado, passo 4 reaberto após nova falha relatada; passos 5 a 10 pendentes; task não concluída.
- **Ambiente oficial:** Skip `RH Pucci` (projectId `59746`), na organização `Org de Luisa`; Skip Cloud em execução.
- **B-ENV-01:** ambiente definido e provisionado; QA e validação técnica da F1-T02 passaram.
- **B-GOV-01:** fechado quanto à aprovação documental da política; controles técnicos da F1-T02 implementados no preview, aguardando homologação humana completa.
- Dados reais continuam bloqueados até a homologação da F1-T02 e confirmação dos controles no uso do processo.

## Ambiente oficial do projeto

- **Projeto Skip:** `RH Pucci` · ID `59746`
- **Skip Cloud:** `rh-pucci-3116c` · status `running`
- **Preview:** https://rh-pucci-3116c--preview.goskip.app — bundle `0.0.6` contém a correção inline
- **Backend:** https://rh-pucci-3116c.shrd00.internal.goskip.dev
- **Produção:** https://rh-pucci-3116c.goskip.app — ainda serve o bundle anterior; publicação de `0.0.6` não autorizada
- **Versão Skip:** `0.0.6` no preview
- **Política de execução:** tarefas futuras serão implementadas nesse projeto, uma por vez, seguindo a SPEC e os gates; nenhum dado real será usado sem os controles comprovados.

## Próximo passo
Usar o preview exato, fazer recarga forçada e repetir somente o passo 4; se o teste precisar ocorrer na URL de produção, autorizar antes a publicação da versão `0.0.6`. Não concluir a task nem iniciar a próxima antes da confirmação.

## Bloqueios ativos
B-IMP-01 (formatos), B-MET-01 (baseline), B-FISC-01 (base INSS), B-STE-01 (Stelanto), divergência de bundle entre preview e produção, novo teste humano do passo 4 e a liberação de dados reais até a homologação — detalhados nas SPECs.
