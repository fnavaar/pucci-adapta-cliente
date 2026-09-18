# Objetivo e visão do projeto

## Objetivo
Substituir o fechamento mensal da pré-folha (hoje disperso entre Stelanto, Flipchart e `Adapta RH.xlsx`) por um sistema único, com rastreabilidade, sem reentrada manual de dados e com o lead time total medido — do ajuste de ponto ao arquivamento documental.

## Métrica norte
Lead time total do fechamento mensal (t0 = abertura da competência, t1 = encerramento). Baseline a medir na Fase 1; meta de 50% do kickoff como referência até lá.

## Fases
1. **Fase 1 — Núcleo operacional:** competência/checklist, ajustes de ponto com homologação, importação de alocação e rateio validado (30 dias), ficha mensal, NFs/INSS, governança (política/RBAC/trilha) e provas técnicas.
2. **Fase 2 — Ciclo com a contabilidade:** pré-folha, SLA, importação/comparação, divergências, encargos (sem recálculo).
3. **Fase 3 — Complementos:** TAB XV/XIII, rateio gerencial (Yampa), compliance documental (Wehandle/Atlas).
4. **Fase 4 — Loops:** fechamento mensal, SLA contabilidade, justificativas de ponto, compliance documental.
5. **Fase 5 — Validação integral** do conjunto.

## Regras do jogo
- O sistema se adapta ao processo da Pucci (ex.: 30 dias comerciais fixos) — nunca o contrário.
- A contabilidade (Dominium) processa a folha legal; o sistema consolida, valida e compara — nunca recalcula.
- Dado sensível (salários, CPF, PIX, pensão) só entra após a política de dados aprovada pelo champion.