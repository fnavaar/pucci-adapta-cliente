# Debug Summary — F1-T05 · auditoria de leitura e visibilidade da coleção

- **Task/SPEC:** F1-T05 · `04_fase-atual/specs/spec-1-002.md`; trilha consultável vinculada a SPEC-1-003/CA-1-011.
- **Sintoma inicial:** em `0.0.25`, listagens de employees/departments falharam com HTTP 500 `Failed to enrich records`; hooks `onRecordEnrich` faziam gravações em `audit_logs`.
- **Recuperação:** em `0.0.26`, hooks de leitura suspensos; QA passou e Champion aprovou telas com fixtures. Em `0.0.27`, hook de employees movido a `onRecordsListRequest`; evento validado pela Champion.
- **Observabilidade:** em `0.0.29` (`3545c75`), a tabela exibe `collection_name`. QA passou em setup, análise estática, build e integrações; `test.ran=false`.
- **Teste humano de auditoria:** aprovado em 2026-10-14. A Champion confirmou `read/identification` para `employees`, `departments`, `tomadores`, `projects` e `contracts`; lista de 14:42 inclui departments/projects/contracts, confirmações textuais cobrem tomadores/employees. Backend registra HTTP 200 para as consultas master-data/audit_logs. `sensitive_payroll` é fixture separada, não F1-T05.
- **Segurança/publicação:** produção preservada em `lastPublishedRef=2b24bd5`.
- **Único gate restante da task:** a descrição pede carregar cadastros reais após a política aprovada. Confirmar só se essa carga autorizada foi feita; não solicitar nem copiar dados pessoais pelo chat. Depois revalidar e fechar F1-T05 formalmente. Não iniciar F1-T06 antes do fechamento.
- **Causa dos 500 iniciais:** side effect em `onRecordEnrich` é consistente com a falha, sem isolamento individual; não atribuir causa mais específica sem evidência.
