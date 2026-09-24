# Relatório de baseline e decisão Stelanto — F1-T04

**Task:** Medir o tempo do fechamento atual e registrar a decisão sobre o Stelanto
**SPEC:** SPEC-1-004 · **Data:** 2026-09-24 · **Champion:** Marcela
**Ambiente técnico:** RH Pucci / Skip 59746 · preview `0.0.12` (`d36e32a`)

> Este documento separa o que foi comprovado no ambiente de homologação do que ainda depende de um fechamento real. Nenhum dado pessoal ou credencial é registrado.

## 1. Instrumentação entregue e homologada

- `competencies.t0` é preenchido automaticamente pelo backend ao abrir a competência.
- `competencies.t1` é preenchido automaticamente pelo backend ao encerrar.
- `competencies.touch_time_minutes` foi adicionado por migration `0002_f1_t04_touch_time`, aplicada no Skip Cloud.
- Touch time aceita somente inteiro não negativo no schema e inteiro positivo para encerrar.
- Competência encerrada não pode ser reaberta nem ter t0, t1 ou touch time alterados.
- A interface exibe t0, t1, touch time e o lead time total calculado como `t1 - t0`.
- Marcela testou o fluxo no preview e confirmou que a página em branco foi corrigida e que o fluxo completo funcionou.

## 2. Verificação técnica

| Prova | Resultado |
|---|---|
| QA Skip `0.0.9` após primeira implementação | passou em setup, análise estática, build, integrações e testes |
| Debug da página em branco | causa encontrada: `ReferenceError` por `formatMinutes`/`getElapsedMinutes` ausentes; corrigido |
| QA Skip `0.0.12` após correção | passou em setup, análise estática, build, integrações e testes |
| Migration | `0002_f1_t04_touch_time` aplicada |
| Schema live | `touch_time_minutes`: número inteiro, mínimo 0 |
| Logs do teste humano | criação e consulta de competências com HTTP 200 no preview; consultas read-only do Flipchart com HTTP 200 |
| Segurança | nenhum segredo ou dado pessoal publicado; alteração preexistente em `.skip.config.json` preservada |

## 3. Baseline real — pendência explícita (CA-1-015)

**Status: pendente.**

Ainda não há evidência de um fechamento real da Pucci medido no sistema. Os registros observados nos logs correspondem à homologação com competências sintéticas. Portanto, não é correto publicar um número de lead time como baseline da operação real.

O próximo fechamento real deverá registrar:

- `t0`: abertura da competência;
- `t1`: encerramento da competência;
- touch time: soma dos minutos efetivamente trabalhados nas atividades do fechamento;
- lead time total: `t1 - t0`;
- contexto agregado, sem CPF, salário ou outros dados pessoais.

## 4. Decisão sobre o Stelanto — pendência explícita (CA-1-016)

**Status: aberta.**

O Stelanto permanece como fonte oficial do ponto neste ciclo, conforme decisão estrutural já existente. A decisão de integrar agora ou substituir depois **não foi tomada nesta task**, porque ainda não existe baseline real suficiente para comparar o custo/benefício operacional. Não há base para inferir uma substituição.

A decisão deverá ser registrada após o primeiro fechamento real medido, usando:

- lead time total;
- touch time;
- dependências e retrabalho observados;
- dados já provados na F1-T03 sobre Stelanto, Flipchart e retorno contábil.

## 5. Veredito da task

A F1-T04 fica **concluída quanto à instrumentação e homologação da medição**, com as pendências CA-1-015 e CA-1-016 declaradas explicitamente conforme a regra RN-402/RN-403 da SPEC. O baseline real e a decisão Stelanto permanecem itens operacionais pendentes, não resultados inventados.
