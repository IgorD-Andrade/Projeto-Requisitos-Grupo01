# Caso de Uso – F2.3 Leitura de Tag NFC/RFID

## 1. O que este caso de uso descreve?

Este caso de uso descreve o processo de identificação de um projetor através da leitura de sua tag NFC/RFID, permitindo acesso rápido às informações do equipamento e às funcionalidades relacionadas ao seu gerenciamento.

---

## 2. Histórico de Versões

| Data | Versão | Descrição | Autor |
|--------|---------|---------|---------|
| 31/05/2026 | 1.0 | Criação inicial do caso de uso Leitura de Tag NFC/RFID | João Pedro |

---

## 3. Identificação do Caso de Uso

### 3.1 Nome

Ler Tag NFC/RFID

### 3.2 Objetivo

Permitir que o Atendente identifique rapidamente um projetor através da leitura de sua tag NFC/RFID e visualize suas informações no sistema.

### 3.3 Tipo

Concreto.

---

## 4. Atores

### 4.1 Primário

- Atendente Validador.

### 4.2 Secundários

- Tag NFC/RFID.
- Banco de Dados.

---

## 5. Pré-condições

- O projetor deve estar previamente cadastrado no sistema.
- O projetor deve possuir uma tag NFC/RFID vinculada.
- O dispositivo utilizado deve possuir suporte à leitura NFC/RFID.
- O sistema deve estar operacional.

---

## 6. Fluxo Principal (Cenário de Sucesso)

### P1. Iniciar leitura

O Atendente Validador acessa a funcionalidade **Ler Tag NFC/RFID**.

### P2. Solicitar aproximação

O sistema exibe a tela de leitura e solicita a aproximação da tag.

### P3. Aproximar dispositivo

O Atendente Validador aproxima o dispositivo da tag NFC/RFID do projetor.

### P4. Capturar identificação

O sistema captura o identificador único da tag.

### P5. Localizar projetor

O sistema consulta o projetor associado à tag conforme a regra de negócio **RN01 – Projetores possuem identificação única**. **[E1]**

### P6. Recuperar informações

O sistema recupera as informações do projetor.

### P7. Exibir dados

O sistema apresenta:

- Patrimônio
- Modelo
- Número de série
- Localização atual
- Status atual
- Última movimentação registrada

### P8. Disponibilizar ações

O sistema disponibiliza as funcionalidades permitidas ao usuário.

### P9. Encerrar caso de uso

O caso de uso é encerrado.

---

## 7. Fluxos Alternativos

### A1. Consulta detalhada do projetor

#### A1.1

No passo **P7**, o Atendente Validador seleciona a opção **Visualizar Detalhes**.

#### A1.2

O sistema apresenta informações complementares do projetor.

#### A1.3

O sistema retorna ao passo **P8**.

---

### A2. Consulta do histórico de movimentações

#### A2.1

No passo **P8**, o usuário seleciona a opção **Consultar Histórico**.

#### A2.2

O sistema exibe o histórico de movimentações do projetor.

#### A2.3

O sistema retorna ao passo **P8**.

---

## 8. Fluxos de Exceção

### E1. Tag não cadastrada

#### E1.1

No passo **P5**, o sistema não encontra projetor associado à tag lida.

#### E1.2

O sistema apresenta a mensagem **ER01 - Tag NFC/RFID não cadastrada**.

#### E1.3

O sistema retorna ao passo **P2**.

---

### E2. Falha na leitura da tag

#### E2.1

No passo **P4**, a leitura da tag não é concluída.

#### E2.2

O sistema apresenta a mensagem **ER02 - Falha na leitura da tag. Aproxime novamente o dispositivo.**

#### E2.3

O sistema retorna ao passo **P2**.

---

### E3. Falha de comunicação com o banco de dados

#### E3.1

No passo **P6**, ocorre falha ao consultar os dados do projetor.

#### E3.2

O sistema apresenta a mensagem **ER03 - Não foi possível recuperar os dados do projetor.**

#### E3.3

O sistema registra o erro para análise técnica.

#### E3.4

O caso de uso é encerrado.

---

## 9. Pós-condições

- As informações do projetor foram apresentadas ao usuário.
- Nenhuma informação do projetor foi alterada.
- O acesso à consulta pode ser registrado em log para auditoria.

---

## 10. Interface Visual (IV1)

### IV1. Tela de Leitura de Tag

| Elemento | Descrição |
|-----------|-----------|
| Área de leitura NFC/RFID | Aguarda aproximação da tag |
| Patrimônio | Identificador patrimonial do projetor |
| Modelo | Modelo do equipamento |
| Número de Série | Identificação do fabricante |
| Localização Atual | Sala ou setor onde o projetor se encontra |
| Status | Disponível, Em Uso, Em Manutenção ou Inativo |
| Última Movimentação | Última operação registrada para o projetor |

---

## 11. Regras de Negócio Relacionadas

- RN01 – Projetores possuem identificação única.
- RN06 – Sistema registra movimentações dos projetores.
- RN10 – Sistema registra responsável pelas operações.

---

## 12. Frequência de Utilização

**Alta**

A leitura da tag NFC/RFID é utilizada frequentemente durante operações de empréstimo, devolução, localização e manutenção dos projetores.

---

## 13. Referências

- Visão da Demanda (VD)
- Documento de Requisitos Funcionais
- Documento de Regras de Negócio
- Diagrama de Casos de Uso do Sistema GAC
