# Relatório de prova técnica — F1-T03

**Task:** Provar como o Stelanto e o Flipchart exportam seus dados (+ retorno da contabilidade)
**SPEC:** SPEC-1-004 · **Critérios:** CA-1-014, CA-1-017 · **Champion:** Marcela
**Data:** 2026-09-24 · **Executor:** agente (Astro) · **Ambiente:** RH Pucci (Skip 59746)

> Dados pessoais (CPF, salários, PIS, nomes de colaboradores) foram deliberadamente omitidos deste relatório. As evidências originais estão na posse da champion.

---

## 1. Stelanto — prova técnica read-only ✅

| Aspecto | Resultado |
|---|---|
| **Via** | `POST https://api.pipemais.com.br/api/reports/generate/mirror/view` (Bearer via Keycloak `auth.pipemais.com.br`, realm `PipeMais`) |
| **Formato** | JSON estruturado (array por colaborador) |
| **Granularidade** | colaborador → resumo do período → dia → batidas |
| **Campos** | `user` (identificação, equipe, jornada), `summary` (totais em **segundos**: totalWorked, extraTime por faixa, banco de horas, missingTime, lunchBreak), `workDays` (date, status, processStatus, timeEntries), `timeEntries` (time `HH:mm`, type CHECK_IN/CHECK_OUT/FREE_HOURS, device) |
| **Implementação** | Hook `/backend/v1/stelanto/mirror-view` (champion-only, token server-side, limite 31 dias, sem persistência) — v0.0.7 |
| **Evidência** | Card no preview; logs com 2 chamadas autenticadas HTTP 200; tentativa sem sessão bloqueada (401); aprovação humana da champion em 23/09 |

## 2. Campos Solo–Flipchart — prova técnica read-only ✅

| Aspecto | Resultado |
|---|---|
| **Via** | `GET https://dashluisa.netlify.app/.netlify/functions/flipchart-consulta-externa` (Bearer `FLIPCHART_PARCEIRO_API_KEY`) |
| **Formato** | JSON (`{ data: [...] }`) |
| **Granularidade** | registro por viagem/uso de veículo por colaborador |
| **Campos** | `id`, `pessoa`, `data`, `veiculo`, `projeto`, `observacoes`, `status` (original/manual/editado), `source` (flipchart \| movimento) |
| **Implementação** | Hook `/backend/v1/flipchart/consulta` (champion-only, chave server-side, limite 31 dias, sem persistência) — v0.0.8 |
| **Evidência** | Card no preview; log com chamada autenticada HTTP 200 (01/08–31/08); tentativa sem sessão bloqueada (401); aprovação humana da champion em 23/09 |

## 3. Contabilidade — cadeia real de e-mails ✅

### Entrada (enviado pela Pucci)
1. **1º e-mail** — "Solicitação de escrituração no e-Social - Emp. consignado do Trabalhador": Excel com 27 colunas (concedente, contrato, CPF, matrícula, datas de contrato/desconto, parcelas, valores, categoria, competência, estabelecimento, admissão), 4 registros de empréstimos.
2. **2º e-mail** — "PLANILHA RH 08.2026": Excel com 3 abas — **Alocação de Serviços** (TAB III: rateio colaborador×obra em dias, com casos em horas), **Importação** (eventos codificados: VT 270, Prêmio 278, Vale 251, Pensão 258; empresa 13; competência 08/2026), **Projetos** (mapa projeto→obra). NFs com retenção de 11% informadas como **imagem no corpo do e-mail** (não estruturado).

### Retorno (devolvido pela contabilidade)
E-mail com resposta "Segue em anexo a folha para conferência" + ZIP com **6 PDFs**:

| Arquivo | Conteúdo | Granularidade |
|---|---|---|
| Extrato Mensal (6 p.) | eventos por colaborador com códigos, quantidades, valores, bases INSS/FGTS/IRRF, líquido | colaborador |
| Extrato Mensal por Serviços (17 p.) | mesmo extrato, rateado por serviço/centro de custo | colaborador × obra |
| Folha de Ponto 08/2026 | espelho para assinatura (grade de dias em branco) | colaborador |
| Recibo de Pagamento | contracheque (via empregador/empregado) | colaborador |
| Relatório de Líquidos | lista de líquidos + totais | empresa |
| Resumo Mensal | resumo por rubrica (proventos/descontos/informativas), bases e totais gerais, headcount | empresa |

- **Formato do retorno:** exclusivamente PDF (não estruturado), gerado pelo sistema da contabilidade.
- **Rastreabilidade entrada→retorno confirmada:** os códigos de evento da planilha de importação (270, 278, 251, 258) reaparecem nos PDFs; os 4 contratos de empréstimo do 1º e-mail aparecem como eventos de desconto (282/284/286/9750) nos extratos.
- **Conferência atual:** manual, PDF a PDF; divergências → e-mail solicitando ajuste (processo relatado pela champion).

### Achados estruturais do processo atual
1. **NF chega como imagem no corpo do e-mail** — dado não estruturado, inviável importar sem extração manual (impacta F1-T07).
2. **Rótulos de departamento inconsistentes** na TAB III (mesmo código grafado de formas diferentes, inclusive com erro de grafia) e **unidades mistas** (dias × "7h"/"28h") na mesma coluna — força conferência manual e impede importação direta sem normalização.
3. **Retorno 100% em PDF** — a contabilidade não devolve dado estruturado; toda conferência detalhada é manual.

## 4. Recomendação de formato para a importação (CA-1-017)

Para a **F1-T06** (importar alocação e validar rateio), recomendado:

1. **Alocação/rateio:** o RH Pucci deve **gerar nativamente** a TAB III (colaborador × obra × dias), eliminando a planilha digitada. A aba "Importação" da planilha atual (eventos 270/278/251/258) já demonstra o dicionário de eventos que o sistema da contabilidade aceita — adotá-lo como dicionário oficial no RH Pucci.
2. **Normalização obrigatória:** padronizar rótulos de departamento (por código, não por texto) e exigir unidade única (dias) por linha de alocação; horas devem ser convertidas na origem.
3. **Retorno da contabilidade:** PDF não é importável de forma confiável. Recomendação principal: **conferência por totais** — o RH Pucci calcula a pré-folha e compara apenas os totais por rubrica do Resumo Mensal (conferência leve, automática). Fallback declarado: solicitar à contabilidade o Resumo Mensal em CSV/XLSX; se indisponível, conferência assistida por extração do PDF.
4. **NFs:** exigir da equipe interna arquivo estruturado (XML da NF-e ou planilha) no lugar da imagem colada no e-mail.

## 5. Pendências relacionadas (fora do escopo desta task)

- **B-FISC-01:** retenção de 11% praticada na entrada; confirmação por escrito ainda pendente (F1-T07).
- **CA-1-015/CA-1-016** (baseline de lead time e decisão Stelanto): pertencem à F1-T04.

## 6. Aceite

- [x] Champion confirma que a cadeia registrada representa o processo real e aprova o relatório.

**Aceite registrado em 2026-09-24:** Marcela confirmou: “Sim, a cadeia registrada representa o processo real. Relatório está sim aprovado.”
