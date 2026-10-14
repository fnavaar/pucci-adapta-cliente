# Debug Summary — F1-T05 · auditoria de leitura e visibilidade da coleção

- **Task/SPEC:** F1-T05 · `04_fase-atual/specs/spec-1-002.md`; trilha consultável vinculada a SPEC-1-003/CA-1-011.
- **Sintoma inicial:** em `0.0.25`, listagens de employees/departments falharam com HTTP 500 `Failed to enrich records`; hooks `onRecordEnrich` faziam gravações em `audit_logs`.
- **Recuperação:** em `0.0.26`, cinco hooks de leitura foram suspensos; QA passou e a Champion aprovou as telas com fixtures. Em `0.0.27`, o hook de employees passou para `onRecordsListRequest`; evento `read/identification` validado pela Champion.
- **Observabilidade:** em `0.0.29` (`3545c75`), a trilha passou a exibir `collection_name`. QA passou em setup, análise estática, build e integrações; `test.ran=false`.
- **Teste humano da auditoria:** em 2026-10-14, a Champion confirmou `read/identification` para `employees`, `departments`, `tomadores`, `projects` e `contracts`; log list enviado às 14:42 inclui departments/projects/contracts; a confirmação em texto cobre tomadores e employees. Logs do backend mostram HTTP 200 para listagens master-data e audit_logs. Teste de auditoria das cinco coleções aprovado em preview `0.0.29`.
- **Segurança/publicação:** `sensitive_payroll` é uma fixture separada e não entra na cobertura cadastral F1-T05. Produção segue em `lastPublishedRef=2b24bd5`.
- **Gate restante da task:** confirmar se os cadastros reais autorizados foram carregados conforme a descrição da F1-T05. Pedir apenas confirmação, sem solicitar ou copiar dados pessoais no chat. Não iniciar F1-T06 antes de fechar formalmente F1-T05.
- **Causa dos 500 iniciais:** gravação em `onRecordEnrich` é compatível com a falha, mas não foi isolada por hook; não atribuir causa individual sem evidência.
