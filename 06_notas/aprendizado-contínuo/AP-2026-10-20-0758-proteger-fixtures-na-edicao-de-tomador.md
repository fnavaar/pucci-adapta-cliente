# AP-2026-10-20-0758 — Proteger fixtures sintéticas nos fluxos de edição

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T05 / `04_fase-atual/specs/spec-1-002.md`
- Sinal: o fluxo de edição de tomadores foi criado enquanto fixtures sintéticas já coexistiam com o cadastro real; uma ação genérica de editar exporia também a fixture `CNPJ-SINTETICO-01` a mudanças acidentais.
- Evidência: migration `pocketbase/migrations/0008_f1_t05_synthetic_fixtures.js` cria o tomador sintético; em produção, `src/pages/MasterData.tsx` distingue essa fixture e não oferece a ação Editar para ela. QA de Skip `0.0.31` passou em setup, análise estática, build e integrações.
- Regra reutilizável: quando adicionar edição a uma lista que contém fixtures sintéticas, identificar o marcador da fixture e bloquear edição na interface sem ler/alterar registros reais; preservar também validação server-side e trilha já existentes.
- Quando aplicar: CRUD em áreas em que dados sintéticos e reais coexistem.
- Quando não aplicar: ambientes ou coleções sem fixtures; a UI não substitui a autorização/RLS do servidor.
- Confiança: alta — marcador da fixture confirmado na migration e salvaguarda presente no código publicado.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
