# Fase 1 — Tarefas

<!-- fase-format:2 -->

Cada linha é uma tarefa da Jornada de Execução. **Tudo que cabe num card cabe nesta linha** — se um
campo não estiver aqui, ele não tem como ser preenchido, porque é este arquivo que cria a tarefa.

```
- [ ] Título da tarefa @responsável !30/09/2026 #projeto [interno]   <!-- id:… -->
      > descrição da tarefa, uma ou mais linhas
  - [ ] subtarefa (basta indentar 2 espaços)                         <!-- id:… -->
    - [ ] sub-subtarefa (indente mais 2)                             <!-- id:… -->
```

| marcador | o que define | se você não escrever |
|---|---|---|
| `- [ ]` / `- [/]` / `- [x]` | a fazer / em andamento / concluída | a fazer |
| `@nome` | responsável (`@"Nome Composto"` com aspas) | fica **sem responsável** |
| `!dd/mm/aaaa` | prazo | fica **sem prazo** |
| `#projeto` / `#aculturamento` | tipo | Projeto de IA |
| `[interno]` | o cliente **não** vê esta tarefa | o cliente vê |
| `> texto` na linha de baixo | descrição (aparece ao abrir o card) | sem descrição |
| indentar 2 espaços | vira subtarefa da tarefa acima (vale em qualquer profundidade) | tarefa de topo |

Os marcadores só valem **no fim da linha** — `Revisar #3 do contrato` continua sendo um título.
Um título que TERMINA na forma de um marcador sai escapado com `\\` (`Ligar para \\@joao`); a barra é
só para o parser e nunca aparece no card. Você não precisa escrever isso à mão.
Marque `[x]` para concluir e adicione linhas novas à vontade: elas entram no quadro na próxima
sincronização e voltam aqui com o `<!-- id:… -->` preenchido. **Não apague o marcador de id** das
tarefas que já têm um.

- [ ] Definir a política de dados e as permissões de quem vê o quê @Luisa !25/09/2026 #projeto
  > SPEC-1-003 (CA-1-012) · Leva 1. Definir com o champion a política mínima de dados (retenção, cópias, ambiente, uso por IA) e a matriz de papéis×permissões (quem vê salários, CPF, contas, PIX, pensão). Prova: política e matriz aprovadas por escrito (documento assinado/registrar no Drive). Pré-condição: nenhuma. Ponto de parada: champion aprovar por escrito. Estado final: B-GOV-01 com insumo pronto; dado real continua bloqueado até a task seguinte ativar o controle.
- [ ] Ativar controle de acesso e trilha de auditoria no sistema @Luisa !26/09/2026 #projeto
  > SPEC-1-003 (CA-1-010, CA-1-011, CA-1-013) · Leva 1. Configurar RBAC/RLS conforme a matriz aprovada (deny by default), trilha de auditoria de leitura/escrita dos campos sensíveis e os campos t0/t1 de lead time por competência. Prova: papel sem permissão é negado (prova negativa) e leitura/escrita autorizada gera trilha; t0 registrado ao abrir competência. Evidência: capturas + log da trilha. Pré-condição: política aprovada (task anterior). Ponto de parada: plataforma sem RLS nativo → bloqueio nomeado. Estado final: dado real liberado condicionado apenas à política assinada; t0/t1 instrumentados.
- [ ] Provar como o Stelanto e o Flipchart exportam seus dados @Luisa !29/09/2026 #projeto
  > SPEC-1-004 (CA-1-014, CA-1-017) · Leva 2. Executar prova técnica read-only: o que o Stelanto e o Campos Solo–Flipchart exportam (formato, campos, granularidade, via), com screenshot/arquivo real de cada um; coletar amostra do arquivo que a contabilidade devolve (via Magda/contador). Prova: relatório de prova com evidência real por sistema e recomendação de formato para a importação (ou bloqueio nomeado + fallback declarado). Evidência: relatório + anexos. Pré-condição: acessos concedidos pelo champion. Ponto de parada: acesso negado → bloqueio nomeado. Estado final: B-IMP-01 respondido com evidência; formato da importação decidido.
- [ ] Medir o tempo do fechamento atual e registrar a decisão sobre o Stelanto @Luisa !30/09/2026 #projeto
  > SPEC-1-004 (CA-1-015, CA-1-016) · Leva 2. Acompanhar ≥1 fechamento real registrando t0/t1 (já instrumentados) e touch time estimado → baseline do lead time; registrar com o champion a decisão Stelanto (integrar agora × substituir depois) com base nos dados da prova. Prova: baseline registrado no sistema/relatório; decisão registrada por escrito. Evidência: relatório de baseline + documento de decisão. Pré-condição: t0/t1 ativos (Leva 1) e fechamento real ocorrendo. Ponto de parada: fechamento não ocorrer no período → pendência declarada com motivo. Estado final: B-MET-01 e B-STE-01 fechados (ou pendência explícita).
- [ ] Cadastrar colaboradores, projetos e tomadores no sistema @Luisa !01/10/2026 #projeto
  > SPEC-1-002 (apoio a CA-1-005) · Leva 3. Montar o cadastro mestre (colaboradores, projetos/obras, contratos, tomadores/CNPJs) com fixtures sintéticos até a política liberar dado real; após a política assinada, cadastrar os dados reais. Prova: cadastro consultável por colaborador/projeto/tomador. Evidência: captura do cadastro. Pré-condição: ambiente autorizado (B-ENV-01). Ponto de parada: dado real sem política → recusa (correto). Estado final: base cadastral pronta para importar alocação.
- [ ] Importar a alocação do mês e validar o rateio de 30 dias @Luisa !02/10/2026 #projeto
  > SPEC-1-002 (CA-1-005, CA-1-006, CA-1-007) · Leva 3. Implementar a importação no formato provado (ou fallback de entrada assistida), consolidar o rateio por colaborador×projeto sem digitação e validar o fechamento contra 30 dias com sinalização de lacuna/excedente; reimportação substitui atomicamente após confirmação. Prova: rateio importado com zero digitação; colaborador com 28 dias sinalizado; reimportação atômica; linha inválida rejeitada sem gravação parcial. Evidência: capturas do rateio e das sinalizações. Pré-condição: formato provado (Leva 2) + cadastro (task anterior). Ponto de parada: formato inviável → acionar fallback declarado. Estado final: fim da digitação manual da TAB III A demonstrável.
- [ ] Consolidar a ficha mensal de remuneração e as notas fiscais com retenção @Luisa !06/10/2026 #projeto
  > SPEC-1-002 (CA-1-008, CA-1-009) · Leva 4. Lançar/confirmar a ficha mensal de remuneração e eventos por colaborador (salário, benefícios, adicionais incl. cargo de confiança 40%, prêmios, vales, pensão — versionado) e registrar as NFs do período com vínculo a projeto/tomador/CNPJ e valor retido (base do INSS conforme confirmação por escrito — B-FISC-01). Prova: ficha consultável por colaborador/competência; NF bloqueada sem tomador. Evidência: capturas. Pré-condição: cadastro + rateio (Leva 3). Ponto de parada: base do INSS não confirmada por escrito → bloqueio nomeado. Estado final: base da pré-folha completa na competência.
- [ ] Operar a competência no sistema: checklist e ajustes de ponto com homologação @Luisa !07/10/2026 #projeto
  > SPEC-1-001 (CA-1-001, CA-1-002, CA-1-003, CA-1-004) · Leva 4. Abrir a competência com o checklist de 20 itens (status/responsável), registrar ajustes de ponto com justificativa obrigatória (recusa de `-`/vazio) e encaminhar à homologação de Luisa/Marcela com trilha de decisão; pendências de homologação visíveis no checklist. Prova: competência abre com checklist completo; `-` recusado; homologação com trilha; pendências visíveis. Evidência: capturas + aceite humano do champion no roteiro completo (abrir competência → registrar ajuste → recusar `-` → homologar → ver checklist). Pré-condição: RBAC ativo (Leva 1); cadastro (Leva 3). Ponto de parada: política de ponto contradisser a recusa de `-` → validar com champion. Estado final: fechamento mensal operável no sistema de ponta a ponta da F1.