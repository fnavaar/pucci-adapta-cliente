# AP-2026-09-24-1002 — Instrumentação homologada não é baseline operacional

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T04 / `04_fase-atual/specs/spec-1-004.md`
- Sinal: t0, t1 e touch time foram implementados no sistema e homologados com competências sintéticas; isso não produz baseline do fechamento real nem autoriza decidir sobre substituir o Stelanto.
- Evidência: `03_documentos/provas/relatorio-baseline-f1-t04.md`; migration `0002_f1_t04_touch_time` aplicada; QA `0.0.12` passou; aceite humano da champion; logs de homologação com competências sintéticas.
- Regra reutilizável: separar três estados na medição: instrumentação disponível, homologação técnica e baseline operacional real. Só fechar baseline/decisão quando existir pelo menos um fechamento real com t0, t1 e touch time observáveis.
- Quando aplicar: em métricas de lead time, comparações de fornecedores e decisões de integração/substituição baseadas em uma primeira medição.
- Quando não aplicar: não usar dados sintéticos ou testes de UI como substituto quando a SPEC exigir comportamento operacional real.
- Confiança: alta — a distinção está prevista na SPEC e foi necessária para evitar publicar um número ou decisão sem fechamento real.
- Privacidade: sem segredo, credencial, dado pessoal ou conteúdo bruto.
