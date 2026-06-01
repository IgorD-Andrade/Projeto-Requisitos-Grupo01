# Caso de Uso – F7.2 Controle de Permissões

## 1. O que este caso de uso descreve?

Este caso de uso descreve o processo de gerenciamento e controle de permissões de acesso dentro do sistema GAC, permitindo definir quais funcionalidades cada usuário poderá acessar de acordo com seu perfil.

---

## 2. Histórico de Versões

| Data | Versão | Descrição | Autor |
|---------|---------|---------|---------|
| 01/06/2026 | 1.0 | Criação inicial do caso de uso Controle de Permissões | Asafe |

---

## 3. Identificação do Caso de Uso

### 3.1 Nome

Controle de Permissões

### 3.2 Objetivo

Permitir que o Administrador do Sistema gerencie permissões de acesso dos usuários da plataforma GAC, garantindo segurança, organização e controle das operações disponíveis para cada perfil.

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
- O Administrador deve possuir permissão para gerenciar acessos.
- O sistema deve estar operacional.
- O usuário que terá suas permissões alteradas deve estar cadastrado.

---

## 6. Fluxo Principal (Cenário de Sucesso)

### P1. Acessar funcionalidade

O Administrador do Sistema acessa a funcionalidade **Controle de Permissões**.

### P2. Exibir usuários

O sistema apresenta a lista de usuários cadastrados.

### P3. Selecionar usuário

O Administrador do Sistema seleciona o usuário desejado.

### P4. Exibir permissões

O sistema apresenta as permissões disponíveis e as permissões atuais do usuário.

### P5. Definir permissões

O Administrador do Sistema seleciona ou remove permissões conforme necessário.

### P6. Validar alterações

O sistema valida as alterações realizadas. **[E1] [E2]**

### P7. Salvar permissões

O sistema registra as alterações na base de dados.

### P8. Registrar histórico

O sistema registra a operação conforme a regra de negócio **RN10 – Sistema registra responsável pelas operações**.

### P9. Exibir confirmação

O sistema apresenta a mensagem **IN01 – Permissões atualizadas com sucesso**.

### P10. Encerrar caso de uso

O caso de uso é encerrado.

---

## 7. Fluxos Alternativos

### A1. Conceder acesso total

#### A1.1

No passo **P5**, o Administrador do Sistema seleciona todas as permissões disponíveis.

#### A1.2

O sistema registra a configuração.

#### A1.3

O sistema segue para o passo **P8**.

---

### A2. Revogar acesso específico

#### A2.1

No passo **P5**, o Administrador remove uma ou mais permissões.

#### A2.2

O sistema registra a alteração.

#### A2.3

O sistema segue para o passo **P8**.

---

## 8. Fluxos de Exceção

### E1. Usuário não localizado

#### E1.1

No passo **P3**, o sistema não localiza o usuário informado.

#### E1.2

O sistema apresenta a mensagem **ER01 – Usuário não encontrado**.

#### E1.3

O sistema retorna ao passo **P2**.

---

### E2. Nenhuma permissão selecionada

#### E2.1

No passo **P6**, o sistema identifica que nenhuma permissão foi definida.

#### E2.2

O sistema apresenta a mensagem **ER02 – É necessário definir ao menos uma permissão**.

#### E2.3

O sistema retorna ao passo **P5**.

---

### E3. Falha ao salvar alterações

#### E3.1

No passo **P7**, ocorre falha ao salvar as permissões.

#### E3.2

O sistema apresenta a mensagem **ER03 – Não foi possível atualizar as permissões no momento**.

#### E3.3

O sistema registra o erro para análise técnica.

#### E3.4

O caso de uso é encerrado.

---

## 9. Pós-condições

- As permissões do usuário foram atualizadas.
- A operação foi registrada no histórico do sistema.
- O acesso do usuário passa a obedecer às permissões definidas.

---

## 10. Interface Visual (IV1)

### IV1. Tela de Controle de Permissões

| Campo | Obrigatório | Formato | Regra de Validação |
|---------|---------|---------|---------|
| Usuário | Sim | Lista ou pesquisa | Deve existir no sistema |
| Perfil de Acesso | Sim | Lista | Administrador ou operador |
| Cadastro de Projetores | Não | Seleção | Permitir ou negar |
| Movimentações | Não | Seleção | Permitir ou negar |
| Manutenção | Não | Seleção | Permitir ou negar |
| Relatórios | Não | Seleção | Permitir ou negar |
| Observações | Não | Texto livre | Máximo de 500 caracteres |

---

## 11. Regras de Negócio Relacionadas

- RN08 – Cada usuário deve acessar apenas funcionalidades autorizadas.
- RN09 – Somente Administradores podem alterar permissões.
- RN10 – Sistema registra responsável pelas operações.

---

## 12. Frequência de Utilização

**Média**

Utilizado sempre que houver necessidade de conceder, alterar ou restringir acesso de usuários na plataforma GAC.

---

## 13. Referências

- Visão da Demanda (VD)
- Documento de Requisitos Funcionais
- Documento de Regras de Negócio
- Diagrama de Casos de Uso do Sistema GAC
