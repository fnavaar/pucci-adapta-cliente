# Debug Summary — F1-T05 · enriquecimento e auditoria de leitura

- **Task/SPEC:** F1-T05 · `04_fase-atual/specs/spec-1-002.md`; requisito de trilha alinhado à SPEC-1-003, CA-1-011.
- **Sintoma:** em `0.0.25`, GET de employees/departments falhou com HTTP 500 `Failed to enrich records.`; hooks de leitura gravavam em `audit_logs` dentro de `onRecordEnrich`.
- **Ação e evidência:** cinco hooks de leitura foram suspensos em `0.0.26`; QA passou e Marcela confirmou visualmente colaboradores, setores e `/cadastros` com fixtures. Logs autenticados de `0.0.26` mostram HTTP 200 para as cinco APIs master-data.
- **Causa:** side effect em `onRecordEnrich` é compatível com a falha, mas não foi isolado hook por hook. Não atribuir causa individual sem teste controlado.
- **Tentativa de restaurar trilha:** em `0.0.27` (`9a086ff`), somente `employees_read_audit_log.js` mudou para `onRecordsListRequest`; o hook cria um log `read` por employee retornado, com ator, id e `identification`, sem copiar valores pessoais. QA passou em setup, estática, build e integrações; `test.ran=false`. Sem chamada autenticada após o build — logs mais recentes mostram tentativas de login HTTP 400. Resultado do hook permanece desconhecido; quatro hooks de leitura continuam suspensos.
- **Privacidade/publicação:** todos os testes aprovados usaram fixtures sintéticas; não inserir dados reais até auditoria de leitura estar ativa e verificada. Produção permanece em `lastPublishedRef=2b24bd5`.
- **Gate:** F1-T05 em correção. Testar `/colaboradores` em `0.0.27` e conferir no módulo `/fechamento` → “Controle de acesso e auditoria” → “Atualizar trilha” um log `read` de `employees` com campo `identification`. Depois reativar/testar uma coleção por vez. Não fechar a task antes de cumprir esse gate de segurança.
