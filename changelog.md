# Changelog — Pucci Ambiental · adapta-cliente

## 2026-09-22 — F1-T02: passo 6 aprovado; passo 7 pendente
- Marcela confirmou o passo 6 no preview.
- Resultado: a trilha de auditoria apareceu com ator, ação, registro e campos.
- Com as confirmações humanas mais recentes, os passos 3, 4, 5 e 6 estão aprovados.
- Passos 7 a 10 permanecem pendentes; F1-T02 não concluída.

## 2026-09-22 — F1-T02: passo 5 aprovado; passo 6 pendente
- Marcela confirmou o passo 5 no preview da versão `0.0.6`.
- Resultado: o registro sintético foi consultado e colaborador, CPF, salário, pensão, conta e PIX apareceram.
- Passo 5 aprovado na homologação humana.
- Passos 6 a 10 permanecem pendentes; F1-T02 não concluída.

## 2026-09-22 — DEBUG F1-T02: divergência entre preview e produção; registro intermediário supersedido
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
- Dados reais permanecem bloqueados até a ativação dos controles técnicos da F1-T02.
- Aprendizado candidato registrado em `06_notas/aprendizado-contínuo/AP-2026-09-18-1743-separar-aprovacao-de-liberacao.md`.
