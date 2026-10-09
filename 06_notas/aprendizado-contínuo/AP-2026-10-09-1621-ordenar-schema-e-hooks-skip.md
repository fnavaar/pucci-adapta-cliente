# AP-2026-10-09-1621 — Separar migrations de schema dos hooks que usam coleções novas

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T05 · `04_fase-atual/specs/spec-1-002.md`
- Sinal: no Skip Cloud, a migration mínima de `departments` falhou enquanto os novos hooks do cadastro mestre estavam presentes no build; o mesmo schema mínimo aplicou depois que esses hooks foram removidos. A plataforma não expôs stack trace que isolasse qual arquivo individual causou o conflito.
- Evidência: comparação das execuções de QA, versão `0.0.17` (`8fc68cb`) passou no estágio de integrações depois da retirada temporária dos hooks; migrations `0004`–`0009` aplicadas no live em etapas; detalhe oficial de migrations Skip recomenda criar coleções antes de migrations/dados que dependem delas. Resumo técnico em `06_notas/debug/debug-2026-10-09-f1-t05-migration-hooks.md`.
- Regra reutilizável: ao criar coleções novas no Skip, primeiro aplicar e validar schema-base; depois relações/fixtures; instalar hooks filtrados por essas coleções só quando o schema já existir. Não tratar build/QA verde como prova de que o hook executou; verificar runtime/logs e um caminho real.
- Quando aplicar: task que acrescenta coleção PocketBase e hooks `onRecord*` para essa coleção no mesmo projeto.
- Quando não aplicar: coleções já existentes e hooks independentes delas; não presume que todo erro de migration seja hook sem A/B semelhante.
- Confiança: média — a remoção conjunta dos hooks acompanhou a mudança de migration falha para aplicada; não houve bisect individual nem stack trace do Skip.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
