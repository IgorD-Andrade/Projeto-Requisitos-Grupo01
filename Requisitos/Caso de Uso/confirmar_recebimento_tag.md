# Caso de Uso – F4.4 Confirmar Recebimento de Projetor pela Leitura da Tag

## 1. O que este caso de uso descreve?

Este caso de uso descreve o processo de confirmação de recebimento de um projetor pelo professor responsável. Durante a confirmação, o sistema registra a posse temporária do equipamento e os acessórios entregues juntamente com o projetor.

---

## 2. Histórico de Versões

| Data | Versão | Descrição | Autor |
|--------|---------|---------|---------|
| 31/05/2026 | 1.0 | Criação inicial do caso de uso Confirmar Recebimento de Projetor | João Pedro |

---

## 3. Identificação do Caso de Uso

### 3.1 Nome

Confirmar Recebimento de Projetor

### 3.2 Objetivo

Permitir que o professor confirme o recebimento do projetor e dos acessórios associados, assumindo responsabilidade temporária pelo equipamento durante o período de utilização.

### 3.3 Tipo

Concreto.

---

## 4. Atores

### 4.1 Primário

- Professor Solicitante.

### 4.2 Secundários

- Atendente Validador.
- Tag NFC/RFID.
- Banco de Dados.

---

## 5. Pré-condições

- Deve existir uma solicitação de empréstimo aprovada.
- O projetor deve estar disponível para empréstimo.
- O projetor deve possuir tag NFC/RFID cadastrada.
- O professor deve estar autenticado no sistema.
- O atendente deve ter iniciado o processo de entrega.

---

## 6. Fluxo Principal (Cenário de Sucesso)

### P1. Iniciar confirmação

O Professor Solicitante acessa a funcionalidade de confirmação de recebimento.

### P2. Solicitar leitura da tag

O sistema solicita a aproximação da tag NFC/RFID do projetor.

### P3. Realizar leitura

O Professor Solicitante aproxima o dispositivo da tag NFC/RFID.

### P4. Identificar projetor

O sistema identifica o projetor associado à tag conforme a regra de negócio **RN01 – Projetores possuem identificação única**. **[E1]**

### P5. Exibir informações

O sistema apresenta:

- Patrimônio
- Modelo
- Número de série
- Estado atual
- Localização atual

### P6. Exibir acessórios

O sistema apresenta a lista de acessórios vinculados ao empréstimo.

Exemplos:

- Cabo HDMI
- Cabo VGA
- Adaptador HDMI
- Controle remoto
- Extensão elétrica
- Fonte de alimentação

### P7. Confirmar recebimento

O Professor Solicitante verifica os itens recebidos e seleciona a opção **Confirmar Recebimento**.

### P8. Registrar responsabilidade

O sistema registra:

- Professor responsável;
- Projetor entregue;
- Acessórios entregues;
- Data e hora da confirmação.

### P9. Atualizar status

O sistema altera o status do projetor para **Em Uso**.

### P10. Registrar movimentação

O sistema registra a operação no histórico conforme a regra de negócio **RN06 – Sistema registra movimentações dos projetores**.

### P11. Exibir confirmação

O sistema apresenta a mensagem **IN01 - Recebimento confirmado com sucesso**.

### P12. Encerrar caso de uso

O caso de uso é encerrado.

---

## 7. Fluxos Alternativos

### A1. Professor registra observação

#### A1.1

No passo **P7**, o Professor Solicitante informa uma observação.

#### A1.2

O sistema registra a observação juntamente com o empréstimo.

#### A1.3

O sistema segue para o passo **P8**.

---

### A2. Acessório não entregue

#### A2.1

No passo **P6**, o Professor Solicitante informa que um dos acessórios listados não foi entregue.

#### A2.2

O sistema registra a divergência.

#### A2.3

O sistema notifica o Atendente Validador.

#### A2.4

O sistema segue para o passo **P7**.

---

## 8. Fluxos de Exceção

### E1. Tag não reconhecida

#### E1.1

No passo **P4**, o sistema não encontra projetor associado à tag.

#### E1.2

O sistema apresenta a mensagem **ER01 - Tag NFC/RFID não cadastrada**.

#### E1.3

O sistema retorna ao passo **P2**.

---

### E2. Projetor indisponível

#### E2.1

No passo **P4**, o sistema identifica que o projetor não está disponível para empréstimo.

#### E2.2

O sistema apresenta a mensagem **ER02 - Projetor indisponível para confirmação de recebimento**.

#### E2.3

O caso de uso é encerrado.

---

### E3. Falha no registro da confirmação

#### E3.1

No passo **P8**, ocorre erro ao registrar a confirmação.

#### E3.2

O sistema apresenta a mensagem **ER03 - Não foi possível concluir a operação**.

#### E3.3

O sistema registra o erro para análise técnica.

#### E3.4

O caso de uso é encerrado.

---

## 9. Pós-condições

- O professor torna-se responsável pelo projetor durante o período de empréstimo.
- Os acessórios entregues ficam associados ao empréstimo.
- O status do projetor é alterado para "Em Uso".
- A movimentação é registrada no histórico do sistema.
- O registro fica disponível para auditoria e rastreamento.

---

## 10. Interface Visual (IV1)

### IV1. Tela de Confirmação de Recebimento

| Campo | Obrigatório | Descrição |
|---------|---------|---------|
| Patrimônio | Sim | Identificação patrimonial do projetor |
| Modelo | Sim | Modelo do projetor |
| Número de Série | Sim | Identificação do fabricante |
| Professor Responsável | Sim | Usuário que receberá o equipamento |
| Data e Hora | Sim | Gerado automaticamente pelo sistema |
| Lista de Acessórios | Sim | Itens entregues junto ao projetor |
| Observações | Não | Comentários sobre a entrega |
| Confirmação de Recebimento | Sim | Aceite do professor |

---

## 11. Regras de Negócio Relacionadas

- RN01 – Projetores possuem identificação única.
- RN05 – Sistema atualiza status após empréstimo.
- RN06 – Sistema registra movimentações dos projetores.
- RN10 – Sistema registra responsável pelas operações.
- RN11 – Professor confirma recebimento do projetor.

---

## 12. Frequência de Utilização

**Alta**

Utilizado sempre que um projetor for entregue a um professor para uso em atividades acadêmicas.

---

## 13. Referências

- Visão da Demanda (VD)
- Documento de Requisitos Funcionais
- Documento de Regras de Negócio
- Documento de Requisitos Não Funcionais
- Diagrama de Casos de Uso do Sistema GAC
