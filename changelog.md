# Changelog — Pucci Ambiental · adapta-cliente

## 2026-09-18 — Ambiente oficial definido: RH Pucci
- Projeto Skip criado na organização `Org de Luisa`: `RH Pucci` (projectId `59746`).
- Skip Cloud provisionado e em execução: `rh-pucci-3116c`.
- Preview: https://rh-pucci-3116c--preview.goskip.app
- Backend: https://rh-pucci-3116c.shrd00.internal.goskip.dev
- Produção ainda não publicada.
- A partir da F1-T02, as tasks serão executadas nesse projeto, uma por vez. A criação do ambiente não iniciou a implementação da F1-T02.

## 2026-09-18 — DÚVIDA: ambiente canônico da F1-T02
- O repositório operacional contém duas árvores com nomes divergentes: `04-fase-atual/` (referenciada pelo AGENTS/STATUS/SPEC) e `04_fase-atual/` (contém a cópia de fase/SPECs).
- Foram encontrados projetos Skip de RH, mas nenhum vínculo explícito com este handoff: `Sistema RH Web` (ID 34231), `Dashboard RH (Supabase) Clone` (ID 32508) e `Portal RH Colaboradores` (ID 33433).
- Antes de implementar RBAC/RLS, auditoria e t0/t1, confirmar qual ambiente é oficial e qual árvore é canônica. Não alterar nenhum dos protótipos por suposição.

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
