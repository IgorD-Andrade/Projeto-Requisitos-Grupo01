# Caso de Uso – F8.1 Gerar Relatório de Movimentações

## 1. O que este caso de uso descreve?

Este caso de uso descreve o processo de geração do relatório de movimentações dos projetores cadastrados no sistema GAC, permitindo ao Administrador de Inventário acompanhar entradas, saídas, transferências e alterações de localização dos ativos físicos do Centro de Ciências e Tecnologia (CCT).

---

## 2. Histórico de Versões

| Data | Versão | Descrição | Autor |
|---------|---------|---------|---------|
| 01/06/2026 | 1.0 | Criação inicial do caso de uso Gerar Relatório de Movimentações | Asafe |

---

## 3. Identificação do Caso de Uso

### 3.1 Nome

Gerar Relatório de Movimentações

### 3.2 Objetivo

Permitir que o Administrador de Inventário visualize e gere relatórios com o histórico de movimentações dos projetores cadastrados no sistema GAC, auxiliando no acompanhamento, controle patrimonial e rastreabilidade dos ativos.

### 3.3 Tipo

Concreto.

---

## 4. Atores

### 4.1 Primário

- Administrador de Inventário.

### 4.2 Secundários

- Banco de Dados.

---

## 5. Pré-condições

- O Administrador de Inventário deve possuir permissão para acessar relatórios.
- O sistema deve estar operacional.
- Devem existir movimentações registradas no sistema.
- O banco de dados deve estar disponível para consulta.

---

## 6. Fluxo Principal (Cenário de Sucesso)

### P1. Acessar funcionalidade

O Administrador de Inventário acessa a funcionalidade **Gerar Relatório de Movimentações**.

### P2. Exibir filtros

O sistema apresenta os filtros disponíveis para consulta das movimentações.

### P3. Informar critérios

O Administrador de Inventário preenche os critérios desejados.

### P4. Validar informações

O sistema valida os filtros informados. **[E1] [E2]**

### P5. Consultar movimentações

O sistema consulta os registros de movimentações conforme os critérios definidos.

### P6. Organizar relatório

O sistema organiza as informações encontradas.

### P7. Exibir relatório

O sistema apresenta o relatório ao Administrador de Inventário.

### P8. Registrar operação

O sistema registra a geração do relatório conforme a regra de negócio **RN10 – Sistema registra responsável pelas operações**.

### P9. Encerrar caso de uso

O caso de uso é encerrado.

---

## 7. Fluxos Alternativos

### A1. Exportar relatório

#### A1.1

No passo **P7**, o Administrador de Inventário solicita exportação do relatório.

#### A1.2

O sistema gera o arquivo no formato solicitado.

#### A1.3

O sistema retorna ao passo **P7**.

---

### A2. Aplicar novo filtro

#### A2.1

No passo **P7**, o Administrador de Inventário deseja alterar os filtros.

#### A2.2

O sistema retorna ao passo **P3**.

---

## 8. Fluxos de Exceção

### E1. Filtros inválidos

#### E1.1

No passo **P4**, o sistema identifica critérios inconsistentes.

#### E1.2

O sistema apresenta a mensagem **ER01 – Filtros informados são inválidos**.

#### E1.3

O sistema retorna ao passo **P3**.

---

### E2. Nenhuma movimentação encontrada

#### E2.1

No passo **P5**, o sistema não encontra registros.

#### E2.2

O sistema apresenta a mensagem **ER02 – Nenhuma movimentação encontrada para os critérios informados**.

#### E2.3

O sistema encerra o caso de uso.

---

### E3. Falha na geração do relatório

#### E3.1

No passo **P6**, ocorre falha no processamento do relatório.

#### E3.2

O sistema apresenta a mensagem **ER03 – Não foi possível gerar o relatório no momento**.

#### E3.3

O sistema registra o erro para análise técnica.

#### E3.4

O caso de uso é encerrado.

---

## 9. Pós-condições

- O relatório de movimentações foi apresentado ao Administrador.
- A operação foi registrada no histórico do sistema.
- Nenhum dado cadastral dos projetores foi alterado.

---

## 10. Interface Visual (IV1)

### IV1. Relatório de Movimentações

| Campo | Obrigatório | Formato | Regra de Validação |
|---------|---------|---------|---------|
| Data Inicial | Sim | Data | Deve ser menor ou igual à Data Final |
| Data Final | Sim | Data | Deve ser válida |
| Tipo de Movimentação | Não | Lista | Entrada, saída ou transferência |
| Projetor | Não | Texto | Deve corresponder a projetor cadastrado |
| Localização | Não | Lista | Deve existir no sistema |
| Formato de Exportação | Não | Lista | PDF ou planilha |

---

## 11. Regras de Negócio Relacionadas

- RN03 – Toda movimentação deve ser registrada.
- RN10 – Sistema registra responsável pelas operações.

---

## 12. Frequência de Utilização

**Alta**

Utilizado frequentemente para auditoria patrimonial, rastreamento e acompanhamento das movimentações dos projetores do CCT.

---

## 13. Referências

- Visão da Demanda (VD)
- Documento de Requisitos Funcionais
- Documento de Regras de Negócio
- Diagrama de Casos de Uso do Sistema GAC
