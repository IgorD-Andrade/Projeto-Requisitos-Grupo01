# Caso de Uso – F3.1 Registrar Manutenção

## 1. O que este caso de uso descreve?

Este caso de uso descreve o processo de registro de manutenção de projetores no sistema GAC, permitindo que o Administrador do Sistema documente intervenções realizadas nos ativos, acompanhe seu histórico técnico e mantenha o controle atualizado do estado de funcionamento.

---

## 2. Histórico de Versões

| Data | Versão | Descrição | Autor |
|---------|---------|---------|---------|
| 01/06/2026 | 1.0 | Criação inicial do caso de uso Registrar Manutenção | Asafe |

---

## 3. Identificação do Caso de Uso

### 3.1 Nome

Registrar Manutenção

### 3.2 Objetivo

Permitir o registro das manutenções realizadas em projetores cadastrados, armazenando informações técnicas e atualizando o status do equipamento no sistema.

### 3.3 Tipo

Concreto.

---

## 4. Atores

### 4.1 Primário

- Administrador do Sistema.

### 4.2 Secundários

- Banco de Dados.

---

## 5. Pré-condições

- O Administrador do Sistema deve estar autenticado.
- O projetor deve estar previamente cadastrado.
- O sistema deve estar operacional.
- O usuário deve possuir permissão para registrar manutenção.

---

## 6. Fluxo Principal (Cenário de Sucesso)

### P1. Acessar funcionalidade

O Administrador do Sistema acessa a funcionalidade **Registrar Manutenção**.

### P2. Selecionar projetor

O sistema apresenta a lista de projetores cadastrados.

### P3. Informar manutenção

O Administrador seleciona o projetor desejado e informa os dados da manutenção.

### P4. Validar informações

O sistema valida os dados preenchidos. **[E1] [E2]**

### P5. Registrar manutenção

O sistema salva o registro na base de dados.

### P6. Atualizar status

O sistema atualiza o status do projetor conforme a manutenção registrada.

### P7. Registrar histórico

O sistema registra a operação conforme a regra de negócio **RN10 – Sistema registra responsável pelas operações**.

### P8. Exibir confirmação

O sistema apresenta a mensagem **IN01 – Manutenção registrada com sucesso**.

### P9. Encerrar caso de uso

O caso de uso é encerrado.

---

## 7. Fluxos Alternativos

### A1. Manutenção concluída

#### A1.1

No passo **P3**, o Administrador informa que a manutenção foi finalizada.

#### A1.2

O sistema altera o status do projetor para **Disponível**.

#### A1.3

O sistema segue para o passo **P7**.

---

### A2. Manutenção em andamento

#### A2.1

No passo **P3**, o Administrador informa que a manutenção ainda está em andamento.

#### A2.2

O sistema mantém o status do projetor como **Em Manutenção**.

#### A2.3

O sistema segue para o passo **P7**.

---

## 8. Fluxos de Exceção

### E1. Projetor não localizado

#### E1.1

No passo **P2**, o sistema não encontra o projetor informado.

#### E1.2

O sistema apresenta a mensagem **ER01 – Projetor não encontrado**.

#### E1.3

O sistema retorna ao passo **P2**.

---

### E2. Dados obrigatórios não preenchidos

#### E2.1

No passo **P4**, o sistema identifica ausência de informações obrigatórias.

#### E2.2

O sistema apresenta a mensagem **ER02 – Preencha os campos obrigatórios**.

#### E2.3

O sistema retorna ao passo **P3**.

---

### E3. Falha ao registrar manutenção

#### E3.1

No passo **P5**, ocorre falha no armazenamento.

#### E3.2

O sistema apresenta a mensagem **ER03 – Não foi possível registrar a manutenção no momento**.

#### E3.3

O sistema registra o erro para análise técnica.

#### E3.4

O caso de uso é encerrado.

---

## 9. Pós-condições

- A manutenção foi registrada no sistema.
- O status do projetor foi atualizado.
- O histórico técnico do equipamento foi atualizado.
- A operação ficou registrada com identificação do responsável.

---

## 10. Interface Visual (IV1)

### IV1. Formulário de Registro de Manutenção

| Campo | Obrigatório | Formato | Regra de Validação |
|---------|---------|---------|---------|
| Projetor | Sim | Lista de seleção | Deve existir no sistema |
| Data da Manutenção | Sim | Data | Deve ser válida |
| Tipo de Manutenção | Sim | Lista | Preventiva ou corretiva |
| Problema Identificado | Sim | Texto livre | Entre 5 e 500 caracteres |
| Serviço Realizado | Sim | Texto livre | Entre 5 e 500 caracteres |
| Técnico Responsável | Não | Texto | Até 100 caracteres |
| Status do Equipamento | Sim | Lista | Disponível ou Em Manutenção |
| Observações | Não | Texto livre | Máximo de 500 caracteres |

---

## 11. Regras de Negócio Relacionadas

- RN06 – Todo registro de manutenção deve ficar associado ao projetor correspondente.
- RN07 – O status do equipamento deve refletir a manutenção registrada.
- RN10 – Sistema registra responsável pelas operações.

---

## 12. Frequência de Utilização

**Alta**

Utilizado sempre que houver manutenção preventiva ou corretiva em qualquer projetor cadastrado.

---

## 13. Referências

- Visão da Demanda (VD)
- Documento de Requisitos Funcionais
- Documento de Regras de Negócio
- Diagrama de Casos de Uso do Sistema GAC
