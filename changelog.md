# Changelog — Pucci Ambiental · adapta-cliente

## 2026-09-22 — F1-T03 selecionada; análise concluída, autorização pendente
- Próxima task elegível da Fase 1: **Provar como o Stelanto e o Flipchart exportam seus dados**.
- SPEC-1-004 · critérios CA-1-014 e CA-1-017 · Leva 2.
- Nenhum arquivo de produto foi alterado; nenhuma exportação foi executada.
- Pré-condições ainda pendentes: acesso read-only ao Stelanto e ao Campos Solo–Flipchart; amostra real devolvida pela contabilidade via Magda/contador.
- Próximo gate: autorização da champion para implementar a prova técnica e disponibilização dos acessos.

## 2026-09-22 — Marcela · Task F1-T02 concluída: controle de acesso, auditoria e t0/t1 homologados
- Revalidação final independente executada após a aprovação humana do passo 10.
- **CA-1-010 PASSOU:** papéis sem permissão foram negados ao acessar registro sensível (`none`/`homologator` com HTTP 404); a tentativa de alteração de PIX por `analyst` foi negada com HTTP 403.
- **CA-1-011 PASSOU:** leitura/escrita de campos sensíveis gerou trilha append-only consultável com ator, ação, registro e campos; edição/exclusão de `audit_logs` foi negada.
- **CA-1-012 PASSOU:** política e matriz foram aprovadas por escrito antes de qualquer dado real; somente fixtures sintéticas foram usadas.
- **CA-1-013 PASSOU:** `t0` foi definido automaticamente ao abrir a competência e `t1` ao encerrar; após recarga ambos persistiram; reabertura e alteração de `t0`/`t1` foram recusadas.
- QA da versão `0.0.6`: setup, análise estática, build, integrações e testes passaram.
- Homologação humana dos passos 3 a 10 passou no preview; nenhum dado real foi usado.
- A F1-T02 foi marcada concluída na árvore canônica `04_fase-atual/fase.md`; o percentual da fase passou para 2/8 (25%).
- A produção ainda serve bundle frontend anterior ao `0.0.6`; isso permanece como pendência operacional e não foi apresentado como publicação concluída.

## 2026-09-22 — F1-T02: passo 9 aprovado; passo 10 pendente
- Marcela confirmou a parte final do passo 9 no preview.
- Resultado: após recarregar, a competência continuou `closed` com o mesmo t0 e t1, e a trilha de auditoria permaneceu disponível ao clicar em `Atualizar trilha`.
- Passo 9 aprovado na homologação humana.
- Passo 10 é o último pendente; F1-T02 ainda não concluída.

## 2026-09-22 — F1-T02: passo 8 aprovado; passo 9 pendente
- Marcela confirmou o passo 8 no preview.
- Resultado: competência sintética encerrada com status `closed`, t1 preenchido automaticamente e t0 preservado.
- Passo 8 aprovado na homologação humana.
- Passos 8 e 9 permanecem pendentes; F1-T02 não concluída.

## 2026-09-22 — F1-T02: passo 7 aprovado; passo 8 pendente
- Marcela confirmou o passo 7 no preview.
- Resultado: competência sintética aberta com status `open`, t0 preenchido automaticamente e t1 vazio.
- Passo 7 aprovado na homologação humana.
- Passos 8 a 10 permanecem pendentes; F1-T02 não concluída.

## 2026-09-22 — F1-T02: passos 3 a 6 aprovados; passo 7 pendente
- Marcela confirmou os passos 3, 4, 5 e 6 no preview.
- Resultado: papel Champion / Gestora; fixture sintética criada com confirmação inline; registro consultado; trilha de auditoria exibida.
- Passo 6 aprovado na homologação humana.
- Passo 7 ficou como próxima ação.

## 2026-09-22 — DEBUG F1-T02: divergência entre preview e produção; registro intermediário superseded
- **Sintoma:** após a correção visual da versão `0.0.6`, houve divergência sobre a URL usada no teste.
- **Reprodução:** o preview serve bundle contendo `fixtureMessage` e a produção serve bundle sem `fixtureMessage`.
- **Causa:** a versão `0.0.6` está no preview; a produção ainda entrega bundle anterior.
- **Decisão:** a homologação humana continua no preview exato. Publicação em produção não foi executada sem autorização explícita.
- **Estado atual:** as confirmações humanas mais recentes aprovaram os passos 3, 4, 5 e 6; passos 7 a 10 continuam pendentes.

## 2026-09-22 — DEBUG F1-T02: confirmação visual da fixture corrigida
- **Sintoma:** no passo 4, a fixture sintética foi criada; o ID e os valores apareceram, mas a mensagem visual não foi percebida.
- **Reprodução/evidência:** backend registrou `POST /api/collections/sensitive_payroll/records` com HTTP 200; não houve erro de hook.
- **Causa raiz:** o feedback de sucesso estava no topo da página, fora do card da ação.
- **Correção:** feedback de criação da fixture passou a ser renderizado dentro do card, junto do botão, ID e registro. Skip RH Pucci versão `0.0.6`.
- **QA:** setup, análise estática, build, integrações e testes passaram.
- **Dados:** somente fixtures sintéticas; nenhum dado real usado.

## 2026-09-18 — F1-T02 implementada, teste humano pendente
- Núcleo de segurança publicado no Skip `RH Pucci`, versão `0.0.5`.
- Migração `0001_f1_t02_security_core` aplicada: roles, `sensitive_payroll`, `competencies` e `audit_logs`.
- Hooks server-side aplicam deny by default, impedem autoelevação, ocultam campos, registram leitura/escrita/exclusão e protegem t0/t1.
- Laboratório visual adicionado ao preview para login, fixtures sintéticas, competência e auditoria.
- QA do Skip passou em setup, análise estática, build, integrações e testes.
- Provas backend passaram para negação, leitura por papel, escrita por papel, auditoria append-only e t0/t1; nenhum dado real foi usado.
- F1-T02 permanece aberta aguardando teste humano da champion Marcela.
- Evidência detalhada: `03_documentos/setup-ethos/evidencia-f1-t02.md`.

## 2026-09-18 — Ambiente oficial definido: RH Pucci
- Projeto Skip criado na organização `Org de Luisa`: `RH Pucci` (projectId `59746`).
- Skip Cloud provisionado e em execução: `rh-pucci-3116c`.
- Preview: https://rh-pucci-3116c--preview.goskip.app
- Produção publicada conforme status verificado em 22/09/2026; a versão corrente ainda precisa ser publicada para produção.
- A partir da F1-T02, as tasks serão executadas nesse projeto, uma por vez.

## 2026-09-18 — DÚVIDA: ambiente canônico da F1-T02
- O repositório operacional contém duas árvores com nomes divergentes: `04-fase-atual/` (referenciada pelo AGENTS/STATUS/SPEC) e `04_fase-atual/` (contém a cópia de fase/SPECs).
- A dúvida de árvore permanece registrada para organização do handoff; a implementação técnica foi feita exclusivamente no projeto Skip oficial `RH Pucci`.

## 2026-09-18 · Marcela · Task F1-T01 concluída: política e matriz aprovadas
- Política de dados e matriz de permissões versão 0.1 aprovadas por escrito pela champion Marcela.
- Critério CA-1-012 revalidado: aprovação registrada antes de qualquer dado real.
- Verificação documental passou; nenhum padrão de segredo detectado.
- Dados reais continuam bloqueados até a ativação dos controles técnicos da F1-T02.
- Aprendizado candidato registrado em `06_notas/aprendizado-contínuo/AP-2026-09-18-1743-separar-aprovacao-de-liberacao.md`.
