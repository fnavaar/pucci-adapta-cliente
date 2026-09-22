# Evidência — F1-T02: controle de acesso, auditoria e t0/t1

**Data da implementação:** 2026-09-18  
**Data dos debugs visuais:** 2026-09-22  
**Ambiente:** Skip `RH Pucci` · projectId `59746` · versão implementada `0.0.5`; correção visual na versão `0.0.6` no preview  
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
- Feedback de criação da fixture renderizado dentro do card da ação na versão `0.0.6` do preview.

## Provas automatizadas executadas

| Prova | Resultado |
|---|---|
| QA Skip v0.0.5: setup | PASSOU |
| QA Skip v0.0.5: análise estática | PASSOU |
| QA Skip v0.0.5: build | PASSOU |
| QA Skip v0.0.5: integrações | PASSOU |
| QA Skip v0.0.5: testes | PASSOU; o template não possui suíte de testes própria |
| QA Skip v0.0.6 após correção visual: setup | PASSOU |
| QA Skip v0.0.6 após correção visual: análise estática | PASSOU |
| QA Skip v0.0.6 após correção visual: build | PASSOU |
| QA Skip v0.0.6 após correção visual: integrações | PASSOU |
| QA Skip v0.0.6 após correção visual: testes | PASSOU |
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
| Primeiro teste humano do passo 3 | OK — papel Champion / Gestora confirmado |
| Primeiro teste humano do passo 4 | parcial — fixture criada, ID e valores sintéticos exibidos; confirmação visual não percebida |
| Repetição do passo 4 após a versão 0.0.6 | não confirmada — Marcela informou novamente que a mensagem não apareceu; auditoria de bundles encontrou produção desatualizada |

## Debug Summary — confirmação visual

**Task e problema:** F1-T02; confirmação visual ausente após criação da fixture sintética.  
**Reprodução:** `POST /api/collections/sensitive_payroll/records` retornou HTTP 200; o ID e o registro apareceram; não houve erro de hook.  
**Causa raiz:** o feedback de sucesso era renderizado apenas no topo da página, fora do card da ação.  
**Correção:** adicionar confirmação `Operação concluída` dentro do card da fixture, junto do resultado criado; versão `0.0.6` no preview.  
**Verificação automática:** QA completo da versão `0.0.6` passou.  

## Debug Summary — divergência de ambiente

**Task e problema:** F1-T02; a versão testada pela champion não exibiu a correção esperada.  
**Reprodução:** o preview serve bundle contendo `fixtureMessage` e a mensagem inline; a produção serve bundle sem `fixtureMessage`, portanto mantém somente a mensagem global.  
**Causa raiz confirmada da divergência:** a versão `0.0.6` foi aplicada ao preview, mas não foi publicada na URL de produção.  
**Correção neste ciclo:** nenhuma nova alteração de produto; publicação em produção não executada sem autorização explícita.  
**Gate atual:** em correção; confirmar URL do teste ou autorizar publicação da versão `0.0.6`.

## Limitações conhecidas

- A interface do template não possui suíte E2E; a prova de segurança foi executada diretamente contra o backend com contas e registros sintéticos.
- A produção está servindo versão anterior ao `0.0.6`; o teste humano deve usar o preview até a publicação autorizada.
- A task ainda não está concluída: falta confirmar o passo 4 no ambiente correto e executar os passos 5 a 10.
