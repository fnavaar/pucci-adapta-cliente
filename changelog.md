# Changelog — Pucci Ambiental · adapta-cliente

## 2026-09-22 — F1-T02: passos 3 a 6 aprovados; passo 7 pendente
- Marcela confirmou o passo 6 como OK no preview.
- Resultado: a trilha de auditoria apareceu com ator, ação, registro e campos.
- Estado de homologação consolidado: passos 3, 4, 5 e 6 aprovados; passos 7 a 10 permanecem pendentes.
- F1-T02 não concluída.

## 2026-09-22 — DEBUG F1-T02: divergência entre preview e produção; registro intermediário supersedido
- **Sintoma:** após a correção visual da versão `0.0.6`, houve divergência sobre a URL usada no teste.
- **Reprodução:** o preview serve bundle contendo `fixtureMessage` e a produção serve bundle sem `fixtureMessage`.
- **Causa:** a versão `0.0.6` está no preview; a produção ainda entrega bundle anterior.
- **Decisão:** a homologação humana continua no preview exato. Publicação em produção não foi executada sem autorização explícita.
- **Estado atual:** as confirmações humanas mais recentes aprovaram os passos 3, 4, 5 e 6; passos 7 a 10 continuam pendentes.

## 2026-09-22 — DEBUG F1-T02: confirmação visual da fixture corrigida
- **Sintoma:** no passo 4, a fixture sintética foi criada; o ID e os valores apareceram, mas a mensagem visual não foi percebida.
- **Reprodução/evidência:** backend registrou `POST /api/collections/sensitive_payroll/records` com HTTP 200; não houve erro de hook.
- **Causa raiz:** o feedback de sucesso estava no topo da página, fora do card da ação.
- **Correção:** feedback de criação da fixture passou a ser renderizado dentro do card, junto do botão, ID e registro. Skip RH Pucci versão `0.0.6`.
- **QA:** setup, análise estática, build, integrações e testes passaram.
- **Dados:** somente fixtures sintéticas; nenhum dado real usado.

## 2026-09-18 — F1-T02 implementada, teste humano pendente
- Núcleo de segurança publicado no Skip `RH Pucci`, versão `0.0.5`.
- Migração `0001_f1_t02_security_core` aplicada: roles, `sensitive_payroll`, `competencies` e `audit_logs`.
- Hooks server-side aplicam deny by default, impedem autoelevação, ocultam campos, registram leitura/escrita/exclusão e protegem t0/t1.
- Laboratório visual adicionado ao preview para login, fixtures sintéticas, competência e auditoria.
- QA do Skip passou em setup, análise estática, build, integrações e testes.
- Provas backend passaram para negação, leitura por papel, escrita por papel, auditoria append-only e t0/t1; nenhum dado real foi usado.
- F1-T02 permanece aberta aguardando teste humano da champion Marcela.
- Evidência detalhada: `03_documentos/setup-ethos/evidencia-f1-t02.md`.
