# Debug Summary — página em branco no card de competência

- **Data:** 2026-09-24
- **Task:** F1-T04 / `04_fase-atual/specs/spec-1-004.md`
- **Sintoma:** ao clicar no card/fluxo da competência no preview, a página ficou em branco durante o teste humano da versão `0.0.9`.
- **Reprodução:** a entrada pública do preview abriu normalmente. A reprodução autenticada não foi concluída nesta sessão porque a senha da conta sintética não estava disponível; não foi usada credencial real nem inventada. A cadeia foi confirmada por inspeção do arquivo implantado: a tabela de competências renderizava `formatMinutes(...)` e `getElapsedMinutes(...)`, mas as duas funções não existiam no módulo.
- **Causa raiz:** `ReferenceError` em tempo de execução quando o card renderizava uma competência; o QA estrutural/build não capturou porque a exceção ocorre no navegador no caminho com dados de competência.
- **Correção:** adicionadas as funções `formatMinutes` e `getElapsedMinutes` no `src/pages/Index.tsx`; nenhuma mudança fora da F1-T04; `.skip.config.json` preexistente preservado.
- **Verificação automática:** versão `0.0.12` (`d36e32a`) — setup, análise estática, build, integrações e testes passaram; preview abre; não há erros novos de hooks. A tentativa de login desta sessão retornou 400 por senha sintética indisponível e não é falha nova do produto.
- **Gate:** aguardando novo teste humano no preview da versão `0.0.12`.
