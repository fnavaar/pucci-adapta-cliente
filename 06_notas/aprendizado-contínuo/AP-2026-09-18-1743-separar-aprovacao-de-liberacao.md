# AP-2026-09-18-1743 — Separar aprovação documental de liberação técnica

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T01 / `04-fase-atual/specs/spec-1-003.md`
- Sinal: a aprovação escrita da política atende o CA-1-012, mas a própria política mantém os dados reais bloqueados até a ativação e prova dos controles técnicos da F1-T02.
- Evidência: `03_documentos/setup-ethos/politica-dados-e-matriz-permissoes.md`, versão 0.1 aprovada; critérios de liberação técnica mantidos na seção 7.
- Regra reutilizável: fechar o gate documental e o gate técnico separadamente; aprovação de política não autoriza inserir dado real sem RBAC, auditoria e instrumentação comprovados.
- Quando aplicar: ao concluir tasks de governança que antecedem o uso de dados sensíveis.
- Quando não aplicar: não usar esta regra para impedir fixtures sintéticas ou documentação sem dados reais.
- Confiança: alta — regra explícita na SPEC, na task e no documento aprovado.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
