# STATUS — Pucci Ambiental · adapta-cliente

**Data:** 2026-10-11 · **Fase atual:** 1 (núcleo operacional do fechamento)

## Estado
- Escopo definitivo v1.0 aprovado (5 fases); SPECs F1 e tasks F1-T01..T08 publicadas.
- **Champion:** Marcela — definida em 18/09/2026, executora e homologadora única das tasks, responsável pelo aceite, política de dados e exceções.
- **Tasks concluídas:** 4/8 (50%). F1-T01 a F1-T04 seguem concluídas nos limites já registrados. F1-T05 ainda não conta como concluída; aguarda reteste humano.
- **F1-T05 — status:** implementação está no preview Skip `0.0.26` (`156263c`); produção continua em `lastPublishedRef=2b24bd5`. Migrations `0004`–`0009` permanecem aplicadas; coleções e relações mantidas. O relato humano e logs do `0.0.25` mostram GET de `employees`/`departments` HTTP 500 `Failed to enrich records.`
- **Correção diagnóstica F1-T05:** desativei temporariamente cinco hooks de leitura `onRecordEnrich` que faziam `$app.save` em `audit_logs` durante enriquecimento. RLS e hooks de escrita permanecem. É hipótese ainda sem confirmação live após o novo build: navegador de inspeção redireciona ao login e ainda não houve request autenticado do `0.0.26`.
- **Sinal de escrita separado:** POST de `departments` registrou HTTP 500 `Failed to enrich record.` e tentativas seguintes HTTP 400 `Failed to create record.`. Como o log não contém mensagem detalhada/payload, não se sabe se uma tentativa anterior deixou registro persistido. Conferir listagem/código sintético antes de repetir criação.
- **QA F1-T05:** `0.0.26` (`156263c`) passou setup, análise estática, build e integrações; runner reportou `test.ran=false` (testes automatizados não executados). Não houve verificação autenticada pós-build.
- **Próximo gate:** autenticar no preview e testar primeiro apenas listagens de colaboradores e setores. Se abrir, registrar HTTP 200; depois testar tomadores/projetos/contratos e auditoria com procedimento controlado. Se continuar falhando, guardar tela/ação e horário. Não publicar produção nem iniciar F1-T06.
- **F1-T04:** módulo de fechamento preservado. B-MET-01 e B-STE-01 seguem pendentes até fechamento real medido.
- **Ambiente oficial:** Skip RH Pucci (projectId `59746`), Skip Cloud `rh-pucci-3116c`.

## Ambiente
- Preview: `https://rh-pucci-3116c--preview.goskip.app` · `0.0.26` (`156263c`).
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção: https://rh-pucci-3116c.goskip.app · sem atualização da F1-T05 (`lastPublishedRef=2b24bd5`).
- Nenhum dado real inserido; testes de criação devem continuar usando identificadores sintéticos.
