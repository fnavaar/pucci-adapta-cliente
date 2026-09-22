# AP-2026-09-22-1131 — Feedback de sucesso deve ficar junto da ação

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: F1-T02 / `04-fase-atual/specs/spec-1-003.md`
- Sinal: a criação de uma fixture sintética foi concluída e exibida, mas o feedback global no topo não foi percebido no teste humano.
- Evidência: teste humano do passo 4; logs do backend com `POST /api/collections/sensitive_payroll/records` HTTP 200; correção validada na versão `0.0.6`.
- Regra reutilizável: feedback de sucesso de uma ação operacional deve aparecer junto do controle acionado e do resultado produzido, sem depender de o usuário procurar uma mensagem global fora da área da ação.
- Quando aplicar: em fluxos do projeto com cards, tabelas ou ações abaixo da dobra.
- Quando não aplicar: não substituir mensagens globais para erros sistêmicos ou eventos que não tenham uma área de ação específica.
- Confiança: alta — sintoma reproduzido no teste humano, causa localizada no código e correção passou no QA completo.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
