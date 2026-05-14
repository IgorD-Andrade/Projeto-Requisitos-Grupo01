# Regras de Negócio da Solução (RN) - GAC

## Histórico de Versões

| Data | Versão | Descrição | Autor |
| --- | --- | --- | --- |
| 08/05/2026 | 1.0 | Criação inicial do documento de regras de negócio do sistema GAC | João Pedro |
| 14/05/2026 | 1.1 | Refinamento das regras de negócio relacionadas ao fluxo de empréstimo e rastreamento | João Pedro |

---

# 1. Regras de Negócio

---

## RN01 - Projetores possuem identificação única

### Descrição

Cada projetor cadastrado no sistema deve possuir uma única identificação vinculada a uma tag NFC/RFID exclusiva.

---

## RN02 - Projetores devem estar cadastrados antes da alocação

### Descrição

Um projetor somente poderá ser emprestado ou rastreado caso esteja previamente cadastrado e ativo no sistema.

---

## RN03 - Projetores disponíveis podem ser alocados

### Descrição

Somente projetores com status "Disponível" poderão ser selecionados para empréstimo.

---

## RN04 - Atendente confirma empréstimo de projetor

### Descrição

Toda solicitação de empréstimo realizada por um professor deve ser confirmada por um atendente responsável.

---

## RN05 - Sistema atualiza status após empréstimo

### Descrição

Após confirmação do empréstimo, o sistema deve alterar automaticamente o status do projetor para "Em uso".

---

## RN06 - Sistema registra movimentações dos projetores

### Descrição

Toda movimentação realizada com projetores deve ser armazenada no histórico do sistema.

---

## RN07 - Projetores emprestados devem ser devolvidos

### Descrição

Todo projetor com empréstimo ativo deve possuir registro de devolução para retornar ao status "Disponível".

---

## RN08 - Projetores em manutenção não podem ser alocados

### Descrição

Projetores com status "Em manutenção" não poderão ser disponibilizados para empréstimo.

---

## RN09 - Usuários acessam funcionalidades conforme perfil

### Descrição

Usuários autenticados devem acessar apenas funcionalidades compatíveis com seus níveis de permissão.

---

## RN10 - Sistema registra responsável pelas operações

### Descrição

Todas as operações realizadas no sistema devem registrar o usuário responsável pela ação.

---

# 2. Checklist de Validação da Regra de Negócio

## 2.1 Estrutura mínima

- [x] Identificador único e padronizado.
- [x] Nome da regra no formato sujeito + verbo + objeto.
- [x] Descrição clara, direta e sem ambiguidades.

---

## 2.2 Qualidade da regra

- [x] A regra descreve apenas uma decisão/comportamento principal.
- [x] Condições de aplicação estão explícitas.
- [x] Resultado esperado da regra está explícito.
- [x] A regra é verificável e testável.

---

## 2.3 Consistência e rastreabilidade

- [x] Não há conflito com outras regras existentes.
- [x] As regras estão alinhadas com RF, RNF e visão da demanda.
- [x] As regras refletem o fluxo operacional do sistema GAC.

---

## 2.4 Prontidão

- [x] Conteúdo revisado.
- [x] Regras prontas para análise, desenvolvimento e testes.
