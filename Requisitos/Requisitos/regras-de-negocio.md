# Regras de Negócio

# 1. Introdução

Este documento descreve as regras de negócio da plataforma GAC relacionadas ao gerenciamento e rastreamento de projetores através de tags NFC/RFID.

---

# 2. Regras de Negócio

### RN01 - Identificação única

Cada projetor deve possuir uma identificação única vinculada a uma única tag NFC/RFID.

---

### RN02 - Cadastro obrigatório

Nenhum projetor poderá ser alocado ou rastreado sem estar previamente cadastrado no sistema.

---

### RN03 - Empréstimo restrito

Somente projetores com status "Disponível" poderão ser alocados para uso.

---

### RN04 - Confirmação de empréstimo

Toda solicitação de empréstimo deve ser confirmada por um atendente responsável.

---

### RN05 - Atualização automática de status

Após confirmação do empréstimo, o sistema deve alterar automaticamente o status do projetor para "Em uso".

---

### RN06 - Registro obrigatório de movimentações

Toda movimentação realizada com o projetor deve ser registrada no histórico do sistema.

---

### RN07 - Registro de devolução

Todo projetor emprestado deve possuir registro de devolução para retornar ao status "Disponível".

---

### RN08 - Bloqueio por manutenção

Projetores em manutenção não podem ser disponibilizados para empréstimo.

---

### RN09 - Controle de permissões

Usuários devem acessar apenas funcionalidades compatíveis com seus perfis de acesso.

---

### RN10 - Registro de responsável

Toda operação realizada deve registrar o usuário responsável pela ação.
