# Evidência — F1-T02: controle de acesso, auditoria e t0/t1

**Data:** 2026-09-18
**Ambiente:** Skip `RH Pucci` · projectId `59746` · versão `0.0.5`
**SPEC:** `04-fase-atual/specs/spec-1-003.md`
**Dados:** somente fixtures sintéticas; nenhum dado real usado.

## Implementado

- Campo `role` no usuário com `champion`, `analyst`, `finance`, `homologator` e `none`.
- Coleção `sensitive_payroll` com campos sintéticos para CPF, remuneração, pensão, conta e PIX.
- Coleção `competencies` com `status`, `t0` e `t1`.
- Coleção `audit_logs` com regras append-only: usuários da aplicação não podem criar, editar ou excluir logs.
- Hooks server-side para impedir autoelevação, aplicar limites de escrita, ocultar campos e registrar leitura/escrita/exclusão.
- Bootstrap protegido para criar a primeira champion apenas quando não existe usuário.
- Laboratório visual no preview para login, fixture sintética, consulta de campos, competência e trilha.

## Provas automatizadas executadas

| Prova | Resultado |
|---|---|
| QA Skip: setup | PASSOU |
| QA Skip: análise estática | PASSOU |
| QA Skip: build | PASSOU |
| QA Skip: integrações | PASSOU |
| QA Skip: testes | PASSOU; o template não possui suíte de testes própria |
| Migração `0001_f1_t02_security_core` | aplicada |
| Papel `none` visualizando registro sensível | NEGADO — HTTP 404 |
| Papel `homologator` visualizando registro sensível | NEGADO — HTTP 404 |
| `analyst` lendo CPF/salário/pensão | permitido; conta/PIX ocultos |
| `finance` lendo conta/PIX | permitido |
| `analyst` tentando alterar PIX | NEGADO — HTTP 403 |
| `finance` alterando PIX | permitido e auditado |
| `analyst` tentando se promover a champion | papel permaneceu `analyst` |
| Usuário editando/excluindo `audit_logs` | NEGADO — HTTP 403 |
| Competência abrindo | `t0` definido pelo backend |
| Competência encerrando | `t1` definido pelo backend |
| Cliente tentando reabrir competência encerrada/alterar t0/t1 | NEGADO — HTTP 400 |
| Auditoria de leitura/escrita | ator, ação, registro e campos registrados |
| Logs de hook após as provas | nenhum erro de hook registrado |

## Limitações conhecidas

- A interface do template não possui suíte E2E; a prova de segurança foi executada diretamente
  contra o backend com contas e registros sintéticos.
- A produção não foi publicada. O teste humano deve usar o preview.
- A task ainda não está concluída: falta a homologação humana da champion.
