# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-09-18 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado (5 fases); SPECs F1 (4) e tasks F1-T01..T08 publicadas.
- **Champion:** Marcela — definida pela CEO em 18/09/2026, executora e homologadora única das tasks, responsável pelo aceite, pela política de dados e pelas exceções.
- **Execução autorizada:** Marcela conduz priorização, execução, validação e conclusão de todas as tasks; nenhum conflito de responsável deve pausar o fluxo.
- **Tasks concluídas:** 1/8 (12,5%). F1-T01 concluída após aprovação escrita da política e matriz versão 0.1; CA-1-012 revalidado.
- **Próxima task:** F1-T02 — ativar controle de acesso e trilha de auditoria no sistema.
- **Ambiente oficial:** Skip `RH Pucci` (projectId `59746`), na organização `Org de Luisa`; Skip Cloud em execução.
- **B-ENV-01:** ambiente definido e provisionado; validação técnica e configuração de segurança continuam na F1-T02.
- **B-GOV-01:** fechado quanto à aprovação documental da política; liberação técnica de dados continua condicionada à F1-T02.
- Dados reais continuam bloqueados até ambiente autorizado, RBAC/RLS, trilha de auditoria e t0/t1 serem comprovados.
- RBAC, trilha de auditoria e t0/t1 ainda não foram ativados; pertencem à F1-T02.

## Ambiente oficial do projeto

- **Projeto Skip:** `RH Pucci` · ID `59746`
- **Skip Cloud:** `rh-pucci-3116c` · status `running`
- **Preview:** https://rh-pucci-3116c--preview.goskip.app
- **Backend:** https://rh-pucci-3116c.shrd00.internal.goskip.dev
- **Produção:** https://rh-pucci-3116c.goskip.app — ainda não publicada
- **Política de execução:** tarefas futuras serão implementadas neste projeto, uma por vez, seguindo a SPEC e os gates; nenhum dado real será usado sem os controles comprovados.

## Próximo passo
Autorizar a implementação da F1-T02 no projeto Skip `RH Pucci` e confirmar a árvore canônica do repositório antes da primeira alteração técnica.

## Bloqueios ativos
B-IMP-01 (formatos), B-MET-01 (baseline), B-FISC-01 (base INSS), B-STE-01 (Stelanto), confirmação da árvore canônica do handoff e a liberação técnica de dados até F1-T02 — detalhados nas SPECs.
