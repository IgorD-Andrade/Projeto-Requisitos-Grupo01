# Caso de Uso – F2.2 Consultar Histórico de Movimentação

## Histórico de Versões

| Data       | Versão | Descrição                                        | Autor |
|-----------|--------|--------------------------------------------------|-------|
| 01/06/2026 | 1.0    | Criação do caso de uso Consultar Histórico de Movimentação | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Consultar Histórico de Movimentação

## 1.2 Objetivo

Permitir que o usuário visualize o histórico completo de movimentações de um projetor (empréstimos, devoluções, transferências, trocas por defeito e manutenções), apoiando auditoria, rastreabilidade e análise de uso dos equipamentos.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Administrador

## 2.2 Secundários

- Atendente (quando autorizado a visualizar histórico)
- Sistema de Banco de Dados

---

# 3. Precondições

- O projetor deve estar **cadastrado** no sistema.
- O usuário (Administrador ou Atendente) deve estar **autenticado** e possuir permissão para consultar histórico.
- O sistema deve estar operacional e com acesso ao banco de dados.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O usuário acessa o sistema GAC e seleciona a opção **"Consultar Histórico de Movimentação"**.

### P2.
O sistema apresenta uma tela para seleção do projetor, permitindo:
- busca por **patrimônio**; ou  
- busca por outros identificadores cadastrados; ou  
- seleção em uma lista de projetores.

### P3.
O usuário informa o patrimônio/identificador ou seleciona o projetor na lista.

### P4.
O sistema localiza o projetor no cadastro.

### P5.
O sistema consulta no banco de dados todas as **movimentações relacionadas ao projetor**, incluindo, por exemplo:
- registros de empréstimo e devolução (F4.1, F4.2);  
- transferências entre salas/setores ou entre professores (F5.1);  
- trocas por defeito (F6.1);  
- entradas e saídas de manutenção (F3.x).

### P6.
O sistema organiza as movimentações em ordem cronológica (da mais recente para a mais antiga) e exibe em forma de lista/tabela, contendo para cada registro:
- tipo de movimentação (empréstimo, devolução, transferência, troca, manutenção etc.);  
- data e hora;  
- usuário responsável (Atendente/Administrador/Técnico/Professor, conforme o caso);  
- origem e destino (por exemplo, setor/sala, professor responsável);  
- observações registradas.

### P7.
Opcionalmente, o usuário aplica **filtros adicionais**, como:
- período (data inicial e final);  
- tipo de movimentação;  
- usuário responsável.

### P8.
O sistema refina a lista conforme os filtros aplicados e atualiza a exibição.

### P9.
O usuário analisa o histórico, podendo:
- exportar ou imprimir (quando disponível);  
- encerrar a consulta ou selecionar outro projetor para novo histórico.

---

# 5. Fluxos Alternativos

## A1. Acesso ao histórico a partir de outra funcionalidade

### A1.1
Durante o uso de outra funcionalidade (por exemplo, **Consultar Projetores – F1.4** ou **Localizar Projetor – F2.1**), o usuário seleciona a opção **"Ver histórico de movimentações"** para um projetor específico.

### A1.2
O sistema já possui o identificador do projetor e **pula** a etapa de seleção (P2–P3), indo diretamente para a consulta no banco (P5).

### A1.3
O fluxo continua normalmente a partir do passo P5, exibindo o histórico daquele projetor.

---

## A2. Consulta por período sem selecionar projetor específico

*(Opcional, se o sistema permitir visão geral de movimentações.)*

### A2.1
No passo P2, o sistema permite que o usuário informe apenas um **período de datas** e, opcionalmente, filtros por tipo de movimentação e usuário.

### A2.2
O usuário opta por consultar o histórico geral por período (sem restringir a um projetor específico).

### A2.3
O sistema lista as movimentações de **todos os projetores** que atendem aos filtros, exibindo também o patrimônio de cada um.

### A2.4
O usuário pode então selecionar um projetor específico na lista para ver apenas o histórico dele, retornando ao fluxo a partir do passo P5.

---

# 6. Fluxos de Exceção

## E1. Projetor não localizado

### E1.1
No passo P4, o sistema não encontra projetor associado ao patrimônio/identificador informado.

### E1.2
O sistema exibe a mensagem:

**ER001 – Projetor não localizado. Verifique o identificador informado.**

### E1.3
O usuário pode:
- tentar nova busca (retornando ao passo P3); ou  
- encerrar o caso de uso.

---

## E2. Nenhuma movimentação encontrada

### E2.1
No passo P5 ou P7, o sistema não encontra movimentações para o projetor (ou para os filtros aplicados).

### E2.2
O sistema exibe a mensagem:

**ER002 – Não foram encontradas movimentações para os critérios informados.**

### E2.3
O usuário pode:
- ajustar filtros (retornando ao passo P2 ou P7); ou  
- encerrar a consulta.

---

## E3. Falha ao consultar o banco de dados

### E3.1
No passo P5 ou P8, ocorre erro de comunicação com o banco de dados ou indisponibilidade temporária.

### E3.2
O sistema exibe a mensagem:

**ER003 – Não foi possível recuperar o histórico de movimentações. Tente novamente mais tarde.**

### E3.3
O sistema registra log técnico para auditoria.

### E3.4
O caso de uso é encerrado.

---

# 7. Pós-condições

- O usuário obtém uma **visão completa ou filtrada** do histórico de movimentações do projetor (ou conjunto de projetores) consultado.
- Nenhum dado é alterado no sistema; a funcionalidade é **apenas de leitura/consulta**.
- Consultas e eventuais falhas podem ser registradas em log para fins de auditoria e monitoramento.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Consulta de Histórico de Movimentação

| Campo / Elemento                 | Obrigatório | Formato           | Regra de Validação                                        |
|----------------------------------|------------|-------------------|------------------------------------------------------------|
| Patrimônio / Identificador       | Não*       | Texto / Código    | Usado para filtrar por projetor específico                |
| Filtro por período (data inicial)| Não        | Data              | Quando usado, deve ser ≤ data final                       |
| Filtro por período (data final)  | Não        | Data              | Quando usado, deve ser ≥ data inicial                     |
| Filtro por tipo de movimentação  | Não        | Seleção           | Ex.: Empréstimo, Devolução, Transferência, Manutenção etc.|
| Filtro por usuário responsável   | Não        | Texto/Seleção     | Opcional                                                   |
| Botão "Buscar" / "Filtrar"       | Não        | Ação              | Dispara a consulta conforme os filtros                    |
| Lista de movimentações           | Não        | Tabela/Lista      | Exibe data/hora, tipo, origem, destino, usuário, observações |
| Botão/Link "Exportar"            | Não        | Ação              | Quando disponível, exporta os dados (PDF/CSV etc.)        |

\* Pelo menos um critério deve ser informado (projetor ou período/outros filtros), conforme regra de negócio.

---

# 9. Frequência de Utilização

Média.

A funcionalidade é utilizada por Administradores (e, quando permitido, por Atendentes) para auditorias, conferência de uso, investigação de problemas com projetores e apoio à tomada de decisão sobre realocação, manutenção ou substituição de equipamentos.
