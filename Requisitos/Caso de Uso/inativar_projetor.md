# Caso de Uso – F1.3 Inativar Projetor

## Histórico de Versões

| Data       | Versão | Descrição                               | Autor |
|-----------|--------|------------------------------------------|-------|
| 31/05/2026 | 1.0    | Criação do caso de uso Inativar Projetor | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Inativar Projetor

## 1.2 Objetivo

Permitir que o Administrador inative um projetor que não deve mais ser utilizado em operações de empréstimo (por exemplo, por obsolescência, perda, dano irreparável ou baixa patrimonial), garantindo que ele deixe de ser oferecido como disponível, sem perder o histórico de movimentações e manutenções.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Administrador

## 2.2 Secundários

- Sistema de Banco de Dados

---

# 3. Precondições

- O projetor deve estar **cadastrado** no sistema.
- O Administrador deve estar **autenticado** e ter permissão para gerenciar cadastro de projetores.
- O sistema deve estar operacional e com acesso ao banco de dados.
- Idealmente, o projetor **não deve possuir empréstimo ativo** (ver fluxo de exceção E2).

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O Administrador acessa o sistema GAC e seleciona a opção **"Inativar Projetor"**.

### P2.
O sistema apresenta uma tela para identificar o projetor, permitindo:
- busca por **patrimônio**; ou  
- busca por outros identificadores cadastrados; ou  
- seleção a partir de uma lista de projetores ativos.

### P3.
O Administrador informa o patrimônio/identificador ou seleciona o projetor na lista e confirma a busca.

### P4.
O sistema localiza o projetor no cadastro e exibe seus dados principais:
- patrimônio;  
- modelo;  
- localização padrão;  
- status cadastral atual;  
- situação de uso (Disponível, Em uso, Em manutenção).

### P5.
O Administrador verifica as informações e seleciona a opção **"Inativar projetor"**.

### P6.
O sistema solicita que o Administrador informe o **motivo da inativação**, por exemplo:
- dano irreparável;  
- perda/roubo;  
- desativação definitiva;  
- baixa patrimonial.

### P7.
O Administrador preenche o motivo da inativação e, se necessário, observações adicionais.

### P8.
O sistema verifica se o projetor:
- **não possui empréstimo ativo**; e  
- não está em processo de troca em andamento.

### P9.
Estando as condições atendidas, o sistema altera o **status cadastral** do projetor para **"Inativo"**.

### P10.
O sistema registra em histórico:
- data e hora da inativação;  
- usuário (Administrador) que realizou a operação;  
- motivo informado.

### P11.
O sistema exibe mensagem de sucesso confirmando a inativação do projetor.

---

# 5. Fluxos Alternativos

## A1. Inativação de projetor já em manutenção sem empréstimo ativo

### A1.1
No passo P4, o sistema indica que o projetor está com status **"Em manutenção"**, mas sem empréstimo ativo.

### A1.2
O Administrador decide prosseguir com a inativação (por exemplo, após laudo técnico de dano irreparável).

### A1.3
O sistema apresenta alerta informando que o projetor está em manutenção e será inativado mesmo assim.

### A1.4
O Administrador confirma a intenção de inativar.

### A1.5
O fluxo segue a partir do passo P6, permitindo registrar o motivo (por exemplo, dano irreparável) e concluir a inativação.

---

# 6. Fluxos de Exceção

## E1. Projetor não localizado

### E1.1
No passo P4, o sistema não encontra projetor associado ao patrimônio/identificador informado.

### E1.2
O sistema exibe a mensagem:

**ER001 – Projetor não localizado. Verifique o identificador informado.**

### E1.3
O Administrador pode tentar nova busca (retornando ao passo P3) ou encerrar o caso de uso.

---

## E2. Projetor com empréstimo ativo

### E2.1
No passo P8, o sistema verifica que o projetor possui **empréstimo ativo**.

### E2.2
O sistema exibe a mensagem:

**ER002 – Projetor com empréstimo ativo. Regularize o empréstimo antes de inativar.**

### E2.3
O sistema não altera o status do projetor.

### E2.4
O Administrador deve encerrar ou ajustar o empréstimo (por meio das funcionalidades F4.2 – Registrar devolução ou F6.1 – Trocar projetor com defeito) antes de tentar inativar novamente.

---

## E3. Falha ao atualizar status cadastral

### E3.1
No passo P9 ou P10, ocorre erro de comunicação com o banco de dados ou outra falha técnica.

### E3.2
O sistema exibe a mensagem:

**ER003 – Não foi possível concluir a inativação do projetor. Tente novamente.**

### E3.3
O sistema registra log técnico para auditoria.

### E3.4
O caso de uso é encerrado **sem alterar** o status cadastral do projetor.

---

# 7. Pós-condições

- O projetor passa a ter status cadastral **"Inativo"**, deixando de ser oferecido para novas operações de empréstimo ou consulta como equipamento disponível.
- O histórico registra o evento de inativação, incluindo motivo, data, hora e usuário responsável.
- Demais informações de histórico de movimentações e manutenções anteriores são **preservadas** para fins de auditoria.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Inativação de Projetor

| Campo / Elemento              | Obrigatório | Formato           | Regra de Validação                                              |
|-------------------------------|------------|-------------------|------------------------------------------------------------------|
| Patrimônio / Identificador    | Sim        | Texto / Código    | Deve corresponder a um projetor cadastrado                      |
| Botão "Buscar"                | Sim        | Ação              | Carrega os dados do projetor                                    |
| Patrimônio (resultado)        | Não        | Texto leitura     | Preenchido automaticamente após a busca                         |
| Modelo                        | Não        | Texto leitura     | Preenchido automaticamente                                      |
| Localização padrão            | Não        | Texto leitura     | Preenchido automaticamente                                      |
| Status cadastral atual        | Não        | Texto/Label       | Ex.: Ativo, Inativo                                             |
| Situação de uso               | Não        | Texto/Label       | Ex.: Disponível, Em uso, Em manutenção                          |
| Motivo da inativação          | Sim        | Lista/Texto       | Deve ser informado (dano irreparável, perda, baixa, etc.)       |
| Observações                   | Não        | Texto até 500 car.| Campo opcional                                                   |
| Botão "Confirmar Inativação" | Sim        | Ação              | Dispara validações e altera o status para Inativo               |

---

# 9. Frequência de Utilização

Baixa.

A funcionalidade será utilizada em momentos pontuais, quando um projetor deixar de fazer parte da operação regular (por baixa patrimonial, roubo, perda ou dano irreparável), garantindo que o cadastro reflita apenas equipamentos efetivamente disponíveis para uso no sistema GAC.
