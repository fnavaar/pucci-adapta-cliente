# Debug Summary — F1-T05 · auditoria de leitura e visibilidade da coleção

- **Task/SPEC:** F1-T05 · `04_fase-atual/specs/spec-1-002.md`; trilha consultável vinculada a SPEC-1-003/CA-1-011.
- **Sintoma inicial:** em `0.0.25`, listagens de employees/departments falharam com HTTP 500 `Failed to enrich records`; hooks `onRecordEnrich` faziam gravações em `audit_logs`.
- **Recuperação:** cinco hooks de leitura foram suspensos em `0.0.26`; QA passou e Champion aprovou visualmente as telas com fixtures. Logs mostram HTTP 200 nas cinco APIs. Em `0.0.27`, o hook de employees foi movido a `onRecordsListRequest`; Champion comprovou eventos `read/identification` de employees.
- **Observabilidade:** em `0.0.29` (`3545c75`), a tabela de auditoria passou a renderizar `collection_name`. QA passou em setup, análise estática, build e integrações; `test.ran=false`. Produção permanece em `2b24bd5`.
- **Reteste humano parcial:** em 2026-10-14, Marcela enviou eventos `read/identification` para `employees` e `departments`, além de uma leitura separada de `sensitive_payroll`. Esta última não prova F1-T05. O material ainda não demonstra `tomadores`, `projects` e `contracts`; não concluir falha dos respectivos hooks porque as coleções podem não ter sido consultadas.
- **Próximo passo:** abrir `/cadastros` em `0.0.29` para disparar consultas a tomadores/projects/contracts, depois abrir a trilha e confirmar eventos para essas três coleções. Usar somente fixtures. Não inserir dados reais nem fechar F1-T05 até a cobertura inteira ser comprovada.
- **Causa dos 500 iniciais:** gravação em `onRecordEnrich` é consistente com a falha, mas não foi isolada individualmente; não atribuir causalidade mais específica sem evidência.
