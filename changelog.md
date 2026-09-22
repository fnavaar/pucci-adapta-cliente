# Changelog — Pucci Ambiental · adapta-cliente

## 2026-09-22 — DEBUG F1-T02: divergência entre preview e produção; passo 4 reaberto
- **Sintoma:** após a correção visual da versão `0.0.6`, Marcela informou novamente que `Operação concluída` não apareceu junto do ID.
- **Reprodução:** comparação direta dos HTML/bundles públicos: o preview serve `/assets/index-BCjpus0O.js`, contendo `fixtureMessage` e duas ocorrências de `Operação concluída`; a produção serve `/assets/index-9op2ZCVL.js`, sem `fixtureMessage` e com apenas a ocorrência global anterior.
- **Causa raiz confirmada da divergência:** o `apply_changes` gerou a versão `0.0.6` no preview, mas a URL de produção ainda não recebeu essa versão. O status `isPublished` não prova que a versão corrente esteja publicada.
- **Correção neste ciclo:** nenhuma nova alteração de produto; o preview já contém a correção. Publicação em produção não foi executada por falta de autorização explícita.
- **Gate:** o registro anterior que marcava o passo 4 como aprovado foi reaberto; a confirmação explícita mais recente da champion prevalece. F1-T02 permanece em correção até confirmar a URL usada ou publicar `0.0.6` com autorização.

## 2026-09-22 — F1-T02: passo 4 aprovado após correção visual; registro supersedido
- Marcela repetiu o passo 4 no preview da versão `0.0.6`.
- O registro foi posteriormente supersedido pela confirmação explícita de que a mensagem ainda não aparecia; a aprovação não é considerada válida até resolver a divergência de bundle.
- Passos 5 a 10 permanecem pendentes; F1-T02 não concluída.

## 2026-09-22 — DEBUG F1-T02: confirmação visual da fixture corrigida, novo teste humano pendente
- **Sintoma:** no passo 4 do teste humano, a fixture sintética foi criada; um novo ID e os valores sintéticos apareceram, mas a mensagem visual "Operação concluída" não foi percebida.
- **Reprodução/evidência:** backend registrou `POST /api/collections/sensitive_payroll/records` com HTTP 200; não houve erro de hook; o componente renderizava a mensagem somente no topo da página, fora do card da ação.
- **Causa raiz confirmada:** o feedback de sucesso estava globalmente no topo da tela; após a ação no card, ele podia ficar fora da área visível, embora a operação tivesse concluído.
- **Correção:** feedback de criação da fixture passou a ser renderizado também dentro do card da fixture, junto do botão, ID e registro. Skip RH Pucci versão `0.0.6`.
- **QA:** setup, análise estática, build, integrações e testes passaram.
- **Dados:** somente fixtures sintéticas; nenhum dado real usado.
- **Gate:** F1-T02 permaneceu aberta aguardando a repetição do passo 4; a aprovação registrada depois foi superseded pela divergência de URL identificada.

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
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção publicada conforme status verificado em 22/09/2026; a versão corrente ainda precisa ser publicada para produção.
- A partir da F1-T02, as tasks serão executadas nesse projeto, uma por vez.

## 2026-09-18 — DÚVIDA: ambiente canônico da F1-T02
- O repositório operacional contém duas árvores com nomes divergentes: `04-fase-atual/` (referenciada pelo AGENTS/STATUS/SPEC) e `04_fase-atual/` (contém a cópia de fase/SPECs).
- A dúvida de árvore permanece registrada para organização do handoff; a implementação técnica foi feita exclusivamente no projeto Skip oficial `RH Pucci`.

## 2026-09-18 · Marcela · Task F1-T01 concluída: política e matriz aprovadas
- Política de dados e matriz de permissões versão 0.1 aprovadas por escrito pela champion Marcela.
- Critério CA-1-012 revalidado: aprovação registrada antes de qualquer dado real.
- Verificação documental passou; nenhum padrão de segredo detectado.
- Dados reais permanecem bloqueados até a ativação comprovada dos controles técnicos da F1-T02.
- Aprendizado candidato registrado em `06_notas/aprendizado-contínuo/AP-2026-09-18-1743-separar-aprovacao-de-liberacao.md`.

## 2026-09-18 — F1-T01 — material produzido, aceite bloqueado
- Política de dados e matriz de permissões publicadas em `03_documentos/setup-ethos/politica-dados-e-matriz-permissoes.md`, versão 0.1 como rascunho para aprovação.
- Verificação estrutural do documento passou; nenhum dado real, RBAC ou trilha de auditoria foi ativado.
- A revisão humana foi registrada, mas a task permaneceu aberta até a aprovação escrita da champion Marcela.

## 2026-09-18 — Champion definido
- Marcela definida pela CEO como champion responsável pelos testes e aprovações do projeto RH Pucci.
- Registros de governança do handoff alinhados; nenhuma task foi iniciada.

## 2026-09-18 — Execução centralizada em Marcela
- Marcela autorizada a conduzir priorização, execução, validação, homologação e conclusão de todas as tasks.
- A participação anterior foi removida de papéis, ownership, homologação e referências operacionais do repo.
- Conflitos de responsável não devem pausar tasks; bloqueios reais de processo, evidência ou segurança continuam registrados.

## 2026-09-18 — Handoff inicial (Fase 1)
- Pasta operacional criada pela consultoria com a estrutura canônica.
- Jornada `04-fase-atual/fase.md` com F1-T01..T08 (fase-format:2).
- SPECs F1 (4) em `04-fase-atual/specs/`.
- Manifesto de integridade: `handoff-manifest.json`.
- Privacidade: escopo base/definitivo, análise crítica, requisitos e fases futuras ficam na consultoria.
