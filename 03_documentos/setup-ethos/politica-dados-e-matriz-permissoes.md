# Política de dados e matriz de permissões — RH/DP Pucci

**Versão:** 0.1
**Status:** RASCUNHO PARA APROVAÇÃO DA CHAMPION
**Task:** F1-T01
**SPEC:** `04-fase-atual/specs/spec-1-003.md`
**Champion:** Marcela
**Escopo:** fechamento mensal da pré-folha da Pucci Ambiental

> Este documento é a proposta operacional da política mínima de dados. Ele só entra em vigor
> depois de aprovação escrita da champion. Até lá, nenhum dado real deve ser inserido no sistema.
> A aprovação desta política também não substitui a ativação do ambiente e dos controles técnicos
> previstos na F1-T02.

## 1. Decisões obrigatórias

1. **Finalidade limitada:** os dados são tratados somente para operar, conferir, homologar e
   arquivar o fechamento mensal da pré-folha, além das obrigações administrativas, fiscais e
   trabalhistas aplicáveis.
2. **Dado real bloqueado:** salários, CPF, contas, PIX, pensão alimentícia e qualquer outro dado
   pessoal real ficam bloqueados até a aprovação escrita desta política e a ativação comprovada
   dos controles técnicos de acesso e auditoria.
3. **Deny by default:** todo papel começa sem acesso. O acesso só existe quando estiver expresso
   na matriz abaixo e concedido pela champion.
4. **Menor privilégio:** cada pessoa recebe somente o acesso necessário à sua responsabilidade.
   Acesso de uma pessoa não pode ser compartilhado com outra.
5. **Conta individual:** não são permitidas contas genéricas ou credenciais compartilhadas para
   acessar o sistema.
6. **Rastreabilidade:** leitura, alteração, exportação e mudança de permissão em campo sensível
   devem gerar registro append-only com quem, quando, ação e registro/campo afetado.
7. **Contabilidade fora do sistema:** a Dominium continua responsável pelo processamento legal da
   folha. A Pucci consolida, valida e compara; não recalcula encargos legais.

## 2. Dados abrangidos

| Classe | Exemplos | Tratamento mínimo |
|---|---|---|
| Identificação restrita | nome, CPF, vínculo e dados cadastrais do colaborador | acesso individual, finalidade de pré-folha e exportação mínima |
| Remuneração restrita | salário, benefícios, adicionais, prêmios, vales e valores de pensão | acesso por papel, sem cópia não controlada e com trilha |
| Pagamento restrito | banco, agência, conta e chave PIX | acesso somente ao Financeiro e à Champion, conforme matriz |
| Ponto e alocação | marcações, ajustes, justificativas, projetos e rateio | acesso operacional e homologação conforme matriz |
| Fiscal/contratual | notas fiscais, tomador, CNPJ, retenção e projeto | acesso operacional e financeiro conforme matriz |
| Política e auditoria | política, matriz, concessões, exceções e logs | acesso da Champion; consulta controlada pelos demais papéis |

## 3. Retenção, cópias e descarte

### 3.1 Retenção

- O registro da competência permanece enquanto for necessário para o fechamento, conferência,
  obrigações legais, fiscais, trabalhistas, contratuais e auditoria aplicáveis.
- Ao terminar a necessidade operacional, a Champion ou pessoa formalmente designada revisa a
  necessidade de retenção e registra a decisão de manter, anonimizar ou eliminar.
- Nenhum prazo legal é presumido neste documento. Os prazos específicos devem ser confirmados
  com a contabilidade e, quando necessário, com orientação jurídica antes do descarte.
- A eliminação deve ser documentada com data, responsável, escopo eliminado e fundamento da
  decisão. Se a eliminação imediata não for possível por obrigação legal, o dado fica bloqueado
  para novo uso e é mantido apenas pelo período necessário.

### 3.2 Cópias e exportações

- Não copiar dados restritos para computador pessoal, pendrive, planilha compartilhada sem
  controle, e-mail pessoal, WhatsApp ou ferramenta de IA.
- Exportações devem conter somente os campos necessários, ser solicitadas por uma pessoa com
  permissão de exportação e gerar trilha de auditoria.
- O envio à contabilidade é humano e controlado: pacote mínimo, destinatário confirmado e
  autorização registrada. Não há integração automática autorizada nesta task.
- Cópias de backup devem permanecer no ambiente controlado, seguir a retenção do registro de
  origem e não podem ser usadas para criar uma segunda base operacional.
- Fixtures de desenvolvimento, demonstração e teste devem ser sintéticas. Dado real não entra
  em desenvolvimento, homologação ou teste.

## 4. Ambientes e uso por IA

- O dado real só pode existir no ambiente autorizado para produção, depois de B-ENV-01 resolvido
  e dos controles de acesso/auditoria comprovados.
- O ambiente de desenvolvimento ou teste usa exclusivamente dados fictícios ou anonimizados de
  forma irreversível.
- É proibido inserir dado pessoal ou sensível real em prompts, chats, embeddings, treinamento,
  ferramentas externas ou serviços públicos de IA.
- A Fase 1 não autoriza IA para processar dados reais. Qualquer exceção futura exige nova decisão
  escrita da Champion, avaliação de finalidade, segurança, contrato e proteção de dados.

## 5. Concessão, revisão e revogação

- A Champion aprova a matriz, novas concessões e exceções.
- A concessão deve identificar pessoa, papel, escopo, data de início e motivo.
- A permissão deve ser revista quando houver admissão, mudança de função, afastamento ou saída.
- Na saída ou perda de necessidade, o acesso é revogado antes do próximo uso operacional possível.
- Tentativas de acesso negado, alteração de permissão e exportações entram na trilha de auditoria.
- Incidente, envio incorreto ou suspeita de cópia deve ser comunicado imediatamente à Champion;
  a ocorrência, o escopo conhecido e a contenção adotada devem ser registrados.

## 6. Matriz inicial de papéis e permissões

### 6.1 Legenda

- **V** = visualizar
- **E** = inserir ou alterar no escopo operacional do papel
- **A** = aprovar/homologar
- **X** = exportar, somente quando necessário e com registro
- **—** = sem acesso

A permissão de exportar não implica autorização para enviar por canal não controlado. Toda
combinação não indicada é negada por padrão.

### 6.2 Matriz proposta

| Domínio/campos | Champion/Gestora — Marcela | Analista RH/DP — Aline ou Marcela em operação | Financeiro — Magda | Dominium | Sem permissão |
|---|---:|---:|---:|---:|---:|
| Identificação e CPF | VEAX | VE | V | — | — |
| Salário e remuneração | VEAX | VE | VEX | — | — |
| Conta bancária e PIX | VEAX | — | VEAX | — | — |
| Pensão alimentícia | VEAX | VE | VE | — | — |
| Ponto, ajustes e justificativas | VEAX | VE | — | — | — |
| Projetos, alocação e rateio | VEAX | VE | VEX | — | — |
| Notas fiscais, tomador e retenção | VEAX | VE | VEAX | — | — |
| Política, concessões e exceções | VEAX | V | V | — | — |
| Logs de auditoria | VX | V dos próprios atos e escopo autorizado | V dos próprios atos e escopo autorizado | — | — |

### 6.3 Limites da matriz

1. **Marcela — Champion/Gestora:** administra a política, aprova acessos e exceções e tem acesso
   operacional amplo para o aceite do fechamento. A permissão de alterar dados não elimina a
   necessidade de justificar a alteração e gerar trilha.
2. **Aline/Marcela — Analista RH/DP:** opera cadastro, ponto, alocação, remuneração e pensão.
   Não acessa conta bancária ou PIX pela matriz inicial.
3. **Magda — Financeiro:** trata remuneração, pagamentos, PIX e informações fiscais necessárias
   ao financeiro. Não altera ponto nem justificativas.
4. **Dominium — Contabilidade:** não recebe conta de usuário no sistema. Recebe apenas exportação
   mínima, autorizada e registrada, quando o processo exigir.
5. **Sem permissão:** não visualiza nem consulta campos sensíveis, inclusive por busca, relatório,
   exportação ou API.
6. **Agente/consultor:** trabalha somente com documentação e fixtures sintéticas; não recebe dado
   real. Qualquer acesso futuro exigirá papel específico aprovado pela Champion.

## 7. Provas exigidas antes de liberar dado real

A política será considerada operacional somente quando houver:

- aprovação escrita da Champion com data e versão;
- ambiente autorizado;
- prova negativa de acesso para papel sem permissão;
- prova de leitura/escrita autorizada com trilha consultável;
- concessão e revogação de acesso registradas;
- t0 e t1 instrumentados por competência;
- registro de qualquer exceção à matriz.

A ativação técnica, as provas de acesso/auditoria e os campos t0/t1 pertencem à F1-T02. Esta
F1-T01 entrega a política e a matriz para aprovação; não ativa esses controles.

## 8. Registro de aprovação

- **Champion:** Marcela
- **Versão aprovada:** pendente
- **Decisão:** pendente de aprovação escrita
- **Data:** pendente
- **Observações/exceções aprovadas:** pendente

**Referências:** `01_projeto/constituicao.md`, `01_projeto/objetivo-e-visao.md`,
`04-fase-atual/specs/spec-1-003.md`, `STATUS.md`.
