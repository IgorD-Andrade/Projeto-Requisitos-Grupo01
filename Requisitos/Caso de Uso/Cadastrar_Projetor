# Caso de Uso – F1.1 Cadastro de Projetor

## 1. O que este caso de uso descreve?

Este caso de uso descreve o processo de cadastro de um novo projetor no sistema GAC, permitindo que o equipamento seja identificado, rastreado e gerenciado através de uma tag NFC/RFID.

---

## 2. Histórico de Versões

| Data | Versão | Descrição | Autor |
|--------|---------|---------|---------|
| 31/05/2026 | 1.0 | Criação inicial do caso de uso Cadastro de Projetor | João Pedro |

---

## 3. Identificação do Caso de Uso

### 3.1 Nome

Cadastrar Projetor

### 3.2 Objetivo

Permitir que o Administrador de Inventário registre um novo projetor no sistema, vinculando-o a uma tag NFC/RFID para possibilitar seu rastreamento, controle e gerenciamento.

### 3.3 Tipo

Concreto.

---

## 4. Atores

### 4.1 Primário

- Administrador de Inventário.

### 4.2 Secundários

- Tag NFC/RFID (fornece a identificação única do projetor).
- Banco de Dados (armazenamento das informações do projetor).

---

## 5. Pré-condições

- O Administrador de Inventário deve possuir permissão para gerenciar projetores.
- O sistema deve estar operacional.
- A tag NFC/RFID utilizada não pode estar associada a outro projetor.
- O banco de dados deve estar disponível para persistência das informações.

---

## 6. Fluxo Principal (Cenário de Sucesso)

### P1. Iniciar cadastro

O Administrador de Inventário acessa a funcionalidade **Cadastrar Projetor**.

### P2. Exibir formulário

O sistema apresenta o formulário de cadastro de projetor.

### P3. Informar dados

O Administrador de Inventário preenche os dados do projetor.

### P4. Ler tag NFC/RFID

O Administrador de Inventário aproxima o dispositivo da tag NFC/RFID do projetor.

### P5. Identificar tag

O sistema identifica a tag NFC/RFID lida.

### P6. Validar informações

O sistema valida os dados informados e a identificação da tag conforme a regra de negócio **RN01 - Projetores possuem identificação única**. **[E1] [E2] [E3]**

### P7. Verificar duplicidade

O sistema verifica se o patrimônio ou a tag NFC/RFID já estão cadastrados.

### P8. Salvar cadastro

Não havendo inconsistências, o sistema registra o projetor na base de dados.

### P9. Registrar histórico

O sistema registra a operação conforme a regra de negócio **RN10 - Sistema registra responsável pelas operações**.

### P10. Exibir confirmação

O sistema apresenta a mensagem **IN01 - Projetor cadastrado com sucesso**.

### P11. Encerrar caso de uso

O caso de uso é encerrado.

---

## 7. Fluxos Alternativos

### A1. Cadastro realizado sem localização definida

#### A1.1

No passo **P3**, o Administrador de Inventário não informa uma localização inicial.

#### A1.2

O sistema atribui a localização padrão definida pela instituição.

#### A1.3

O sistema segue para o passo **P6**.

---

### A2. Cadastro seguido de manutenção inicial

#### A2.1

No passo **P10**, o Administrador de Inventário informa que o projetor necessita de manutenção.

#### A2.2

O sistema disponibiliza acesso à funcionalidade **Registrar Manutenção**.

#### A2.3

O caso de uso é encerrado.

---

## 8. Fluxos de Exceção

### E1. Patrimônio já cadastrado

#### E1.1

No passo **P6**, o sistema identifica que o patrimônio informado já está cadastrado.

#### E1.2

O sistema apresenta a mensagem **ER01 - Patrimônio já cadastrado**.

#### E1.3

O sistema retorna ao passo **P3**.

---

### E2. Tag NFC/RFID já vinculada

#### E2.1

No passo **P6**, o sistema identifica que a tag NFC/RFID já está associada a outro projetor.

#### E2.2

O sistema apresenta a mensagem **ER02 - Tag NFC/RFID já vinculada a outro projetor**.

#### E2.3

O sistema retorna ao passo **P4**.

---

### E3. Campos obrigatórios não preenchidos

#### E3.1

No passo **P6**, o sistema identifica campos obrigatórios não preenchidos.

#### E3.2

O sistema destaca os campos pendentes.

#### E3.3

O sistema apresenta a mensagem **ER03 - Existem campos obrigatórios não preenchidos**.

#### E3.4

O sistema retorna ao passo **P3**.

---

### E4. Falha ao salvar cadastro

#### E4.1

No passo **P8**, ocorre falha na persistência dos dados.

#### E4.2

O sistema apresenta a mensagem **ER04 - Não foi possível concluir o cadastro no momento**.

#### E4.3

O sistema registra o erro para análise técnica.

#### E4.4

O caso de uso é encerrado.

---

## 9. Pós-condições

- O projetor encontra-se cadastrado na plataforma GAC.
- A tag NFC/RFID está vinculada ao projetor.
- O histórico de cadastro foi registrado.
- O projetor torna-se disponível para rastreamento, empréstimo e manutenção.

---

## 10. Interface Visual (IV1)

### IV1. Formulário de Cadastro de Projetor

| Campo | Obrigatório | Formato | Regra de Validação |
|---------|---------|---------|---------|
| Patrimônio | Sim | Texto ou Numérico | Deve ser único no sistema |
| Modelo | Sim | Texto | Entre 2 e 100 caracteres |
| Fabricante | Não | Texto | Até 100 caracteres |
| Número de Série | Sim | Texto | Não pode estar duplicado |
| Localização Inicial | Sim | Lista de seleção | Deve corresponder a uma sala ou setor cadastrado |
| Tag NFC/RFID | Sim | Código único | Não pode estar vinculada a outro projetor |
| Estado Inicial | Sim | Lista | Disponível, Em Manutenção ou Inativo |
| Observações | Não | Texto livre | Máximo de 500 caracteres |

---

## 11. Regras de Negócio Relacionadas

- RN01 – Projetores possuem identificação única.
- RN02 – Projetores devem estar cadastrados antes da alocação.
- RN10 – Sistema registra responsável pelas operações.

---

## 12. Frequência de Utilização

**Média**

O cadastro ocorre principalmente quando novos projetores são adquiridos ou incorporados ao patrimônio da instituição.

---

## 13. Referências

- Visão da Demanda (VD)
- Documento de Requisitos Funcionais
- Documento de Requisitos Não Funcionais
- Documento de Regras de Negócio
- Diagrama de Casos de Uso do Sistema GAC
