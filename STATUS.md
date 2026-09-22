# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-09-22 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado (5 fases); SPECs F1 (4) e tasks F1-T01..T08 publicadas.
- **Champion:** Marcela — definida pela CEO em 18/09/2026, executora e homologadora única das tasks, responsável pelo aceite, pela política de dados e pelas exceções.
- **Execução autorizada:** Marcela conduz priorização, execução, validação e conclusão de todas as tasks; nenhum conflito de responsável deve pausar tasks.
- **Tasks concluídas:** 2/8 (25%). F1-T01 concluída após aprovação escrita da política e matriz versão 0.1; F1-T02 concluída em 22/09/2026 após QA da versão `0.0.6` e homologação humana dos passos 3 a 10 no preview.
- **F1-T02:** concluída no ambiente homologado `RH Pucci`/preview. Critérios CA-1-010 a CA-1-013 comprovados com fixtures sintéticas; nenhum dado real foi usado.
- **F1-T03:** selecionada e analisada; a parte da contabilidade foi esclarecida: não há acesso ao sistema. A evidência será a cadeia real de e-mails enviada pela Pucci e a resposta da contabilidade, com anexos quando existirem. Nenhum produto foi alterado e nenhuma exportação foi executada.
- **Ambiente oficial:** Skip `RH Pucci` (projectId `59746`), na organização `Org de Luisa`; Skip Cloud em execução.
- **B-ENV-01:** ambiente definido e provisionado; QA e validação técnica da F1-T02 passaram.
- **B-GOV-01:** política/matriz aprovadas e controles técnicos homologados no preview. O uso de dados reais permanece condicionado à decisão operacional de publicar/confirmar o ambiente produtivo; nenhum dado real foi inserido.
- **Segurança:** nenhuma credencial de teste foi gravada no repositório; o bundle homologado não contém as senhas fornecidas durante o teste.

## Ambiente oficial do projeto

- **Projeto Skip:** `RH Pucci` · ID `59746`
- **Skip Cloud:** `rh-pucci-3116c` · status `running`
- **Preview:** https://rh-pucci-3116c--preview.goskip.app — versão `0.0.6`, homologada
- **Backend:** https://rh-pucci-3116c.shrd00.internal.goskip.dev
- **Produção:** https://rh-pucci-3116c.goskip.app — a comparação de assets ainda mostra bundle frontend anterior ao `0.0.6`; a publicação da correção visual não foi alegada nem usada como evidência de homologação
- **Versão Skip:** `0.0.6` no preview
- **Política de execução:** tarefas futuras serão implementadas nesse projeto, uma por vez, seguindo a SPEC e os gates; nenhum dado real será usado sem confirmação do ambiente produtivo.

## Próximo passo
Autorizar a implementação da F1-T03, conceder acesso read-only ao Stelanto e ao Campos Solo–Flipchart e disponibilizar a cadeia de e-mails enviada pela Pucci à contabilidade e a resposta recebida, incluindo anexos necessários. Depois disso, executar a prova e produzir o relatório com formato, campos, granularidade, via e recomendação/fallback de importação.

## Bloqueios ativos
B-IMP-01 (formatos), acesso read-only ao Stelanto/Flipchart e cadeia de e-mails da contabilidade para F1-T03, B-MET-01 (baseline), B-FISC-01 (base INSS), B-STE-01 (decisão Stelanto) e a confirmação/publicação do bundle `0.0.6` no ambiente produtivo. Esses itens não reabrem a F1-T02, que foi concluída no preview homologado.
