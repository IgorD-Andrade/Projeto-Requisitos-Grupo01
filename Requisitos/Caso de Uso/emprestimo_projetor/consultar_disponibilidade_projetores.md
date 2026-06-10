# Caso de Uso – F4.3 Consultar Disponibilidade de Projetores

## Histórico de Versões

| Data       | Versão | Descrição                                         | Autor |
|-----------|--------|---------------------------------------------------|-------|
| 31/05/2026 | 1.0    | Criação do caso de uso Consultar Disponibilidade de Projetores | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Consultar Disponibilidade de Projetores

## 1.2 Objetivo

Permitir que o usuário visualize quais projetores estão disponíveis para empréstimo em um determinado período, considerando status atual, agendamentos e manutenções, apoiando o planejamento de uso em aulas e atividades.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primários

- Professor  
- Atendente

## 2.2 Secundários

- Sistema de Banco de Dados

---

# 3. Precondições

- O usuário deve estar **autenticado**, quando o acesso exigir login.
- Devem existir projetores **cadastrados** no sistema.
- O sistema deve estar operacional e com acesso ao banco de dados.
- As informações de empréstimos, devoluções e manutenção devem estar atualizadas.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O usuário (Professor ou Atendente) acessa o sistema GAC e seleciona a opção **"Consultar Disponibilidade de Projetores"**.

### P2.
O sistema apresenta uma tela de filtros de busca, permitindo informar, por exemplo:
- período desejado (data/hora de início e término);
- local/sala ou setor (opcional);
- tipo ou modelo de projetor (opcional).

### P3.
O usuário informa, no mínimo:
- período desejado para uso do projetor.

### P4.
O usuário aciona o comando **"Buscar"** ou equivalente.

### P5.
O sistema consulta o banco de dados e:
- identifica os projetores cadastrados e ativos;
- verifica, para o período informado:
  - se há empréstimos já registrados/agendados;
  - se o projetor está com status “Em manutenção” ou “Aguardando manutenção”.

### P6.
O sistema monta uma lista de projetores com o respectivo **status de disponibilidade** para o período solicitado, por exemplo:
- Disponível;
- Já emprestado;
- Em manutenção;
- Reservado (se houver agendamento futuro).

### P7.
O sistema exibe a lista de resultados, mostrando para cada projetor:
- patrimônio;
- modelo;
- localização atual;
- status de disponibilidade no período pesquisado.


### P8.
O usuário analisa a disponibilidade e encerra a consulta ou retorna para ajustar os filtros.

---

# 5. Fluxos Alternativos

## A1. Consulta rápida sem período específico

### A1.1
No passo P2, o sistema permite que o usuário consulte a **disponibilidade imediata**, sem informar período (ou utilizando o horário atual como referência).

### A1.2
O usuário opta pela consulta rápida.

### A1.3
O sistema considera apenas a situação atual dos projetores:
- disponíveis;
- emprestados;
- em manutenção.

### A1.4
O fluxo continua a partir do passo P6, exibindo os resultados de disponibilidade “neste momento”.

---

## A2. Filtro por local/sala

### A2.1
No passo P2, o usuário informa também o **local/sala** onde deseja verificar a disponibilidade.

### A2.2
O sistema restringe os resultados aos projetores vinculados àquele local/sala.

### A2.3
O fluxo continua a partir do passo P6, exibindo apenas os projetores daquela localização.

---

# 6. Fluxos de Exceção

## E1. Período inválido

### E1.1
No passo P3, o usuário informa um período onde a data/hora de término é anterior à data/hora de início.

### E1.2
O sistema identifica o erro e exibe a mensagem:

**ER001 – Período inválido. A data/hora final deve ser posterior à data/hora inicial.**

### E1.3
O usuário é retornado ao passo P3 para correção dos dados.

---

## E2. Nenhum projetor encontrado

### E2.1
No passo P6, o sistema não encontra nenhum projetor que atenda aos critérios (por exemplo, todos ocupados ou em manutenção no período).

### E2.2
O sistema exibe a mensagem:

**ER002 – Não foram encontrados projetores disponíveis para os critérios informados.**

### E2.3
O usuário pode:
- ajustar os filtros (voltando ao passo P2); ou  
- encerrar a consulta.

---

## E3. Falha ao acessar o banco de dados

### E3.1
No passo P5, ocorre erro de comunicação com o banco de dados ou indisponibilidade temporária.

### E3.2
O sistema exibe a mensagem:

**ER003 – Não foi possível consultar a disponibilidade no momento. Tente novamente mais tarde.**

### E3.3
O sistema registra log técnico para auditoria.

### E3.4
O caso de uso é encerrado.

---

# 7. Pós-condições

- O usuário obtém uma visão clara da **disponibilidade de projetores** para o período consultado.
- Nenhum dado de empréstimo, devolução ou manutenção é alterado: trata-se de uma operação de **leitura/consulta**.
- Eventuais tentativas com erro de consulta ficam registradas em log para análise técnica.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Consulta de Disponibilidade de Projetores

| Campo / Elemento               | Obrigatório | Formato                 | Regra de Validação                                          |
|--------------------------------|------------|-------------------------|-------------------------------------------------------------|
| Data/Hora de início            | Não (ver nota) | Data/Hora           | Quando informado, deve ser <= data/hora final              |
| Data/Hora de término           | Não (ver nota) | Data/Hora           | Quando informado, deve ser >= data/hora inicial            |
| Filtro por local/sala          | Não        | Seleção/Texto          | Opcional, usado para restringir a resultados de um local   |
| Filtro por modelo/tipo         | Não        | Seleção/Texto          | Opcional                                                    |
| Botão "Consultar" / "Buscar"   | Sim        | Ação                    | Dispara a busca conforme filtros                           |
| Lista de projetores (resultado)| Não        | Tabela/Lista            | Exibe patrimônio, modelo, localização e status             |
| Status de disponibilidade      | Não        | Texto/Ícone             | Ex.: Disponível, Emprestado, Em manutenção, Reservado      |
| Link/Botão "Detalhes"          | Não        | Ação                    | Abre detalhes do projetor selecionado                      |

**Nota:**  
- Na **consulta rápida**, o sistema pode assumir o horário atual como início e término (consulta “agora”) quando os campos de período não forem preenchidos.

---

# 9. Frequência de Utilização

Alta.

A funcionalidade é utilizada frequentemente por Professores, para planejar o uso de projetores nas aulas, e por Atendentes, para verificar rapidamente quais equipamentos estão disponíveis antes de registrar um novo empréstimo.
