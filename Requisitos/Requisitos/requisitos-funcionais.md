# Requisitos Funcionais

# 1. Introdução

Este documento apresenta os requisitos funcionais da plataforma GAC (Gestão de Ativos CCT), responsável pelo controle, rastreamento e gerenciamento de projetores através de identificação digital por tags NFC/RFID.

---

# 2. Requisitos Funcionais

## 2.1 Cadastro e Identificação de Projetores

### RF01 - Cadastro de projetores

O sistema deve permitir cadastrar projetores contendo:

- Número de patrimônio
- Modelo
- Marca
- Estado atual
- Localização
- Código identificador da tag NFC/RFID

**Prioridade:** Alta  
**Atores:** Atendente, Administrador

---

### RF02 - Vinculação de tag NFC/RFID

O sistema deve permitir associar uma tag NFC/RFID única a cada projetor cadastrado.

**Prioridade:** Alta  
**Atores:** Atendente

---

### RF03 - Atualização de dados de projetores

O sistema deve permitir editar informações cadastrais dos projetores.

**Prioridade:** Média  
**Atores:** Administrador

---

### RF04 - Inativação de projetores

O sistema deve permitir inativar projetores fora de uso ou indisponíveis.

**Prioridade:** Média  
**Atores:** Administrador

---

### RF05 - Consulta de projetores

O sistema deve permitir consultar projetores cadastrados utilizando filtros.

**Prioridade:** Alta  
**Atores:** Administrador, Atendente

---

## 2.2 Alocação e Empréstimo de Projetores

### RF06 - Leitura de tag para alocação

O sistema deve permitir identificar automaticamente um projetor através da aproximação do dispositivo móvel à tag NFC/RFID.

**Prioridade:** Alta  
**Atores:** Professor, Atendente

---

### RF07 - Exibição de dados do projetor

Após a leitura da tag, o sistema deve exibir:

- Identificação do projetor
- Estado atual
- Localização
- Disponibilidade
- Informações de uso

**Prioridade:** Alta  
**Atores:** Professor, Atendente

---

### RF08 - Solicitação de alocação

O sistema deve permitir que o professor solicite a alocação do projetor identificado pela tag NFC/RFID.

**Prioridade:** Alta  
**Atores:** Professor

---

### RF09 - Confirmação de alocação

O sistema deve permitir que o atendente confirme ou rejeite a solicitação de alocação do projetor.

**Prioridade:** Alta  
**Atores:** Atendente

---

### RF10 - Atualização de status do projetor

Após confirmação da alocação, o sistema deve atualizar automaticamente o status do projetor para "Em uso".

**Prioridade:** Alta  
**Atores:** Sistema

---

### RF11 - Consulta de disponibilidade

O sistema deve permitir consultar projetores disponíveis para empréstimo.

**Prioridade:** Alta  
**Atores:** Professor, Atendente

---

## 2.3 Devolução e Realocação

### RF12 - Registro de devolução

O sistema deve permitir registrar a devolução de um projetor através da leitura da tag NFC/RFID.

**Prioridade:** Alta  
**Atores:** Atendente

---

### RF13 - Atualização após devolução

Após a devolução, o sistema deve atualizar o status do projetor para "Disponível".

**Prioridade:** Alta  
**Atores:** Sistema

---

### RF14 - Realocação de projetores

O sistema deve permitir registrar a transferência de projetores entre salas ou setores.

**Prioridade:** Média  
**Atores:** Administrador

---

## 2.4 Manutenção e Substituição

### RF15 - Registro de defeito

O sistema deve permitir registrar defeitos identificados nos projetores.

**Prioridade:** Média  
**Atores:** Atendente

---

### RF16 - Encaminhamento para manutenção

O sistema deve permitir alterar o status do projetor para "Em manutenção".

**Prioridade:** Média  
**Atores:** Atendente, Administrador

---

### RF17 - Consulta de status de manutenção

O sistema deve permitir consultar o status de manutenção dos projetores.

**Prioridade:** Média  
**Atores:** Professor, Atendente

---

### RF18 - Troca de projetor defeituoso

O sistema deve permitir disponibilizar outro projetor ao professor em caso de defeito do equipamento alocado.

**Prioridade:** Média  
**Atores:** Atendente

---

## 2.5 Rastreamento e Auditoria

### RF19 - Histórico de movimentações

O sistema deve armazenar histórico completo de:

- empréstimos
- devoluções
- trocas
- realocações
- manutenções

**Prioridade:** Alta  
**Atores:** Administrador

---

### RF20 - Consulta de localização

O sistema deve permitir consultar a localização atual do projetor.

**Prioridade:** Alta  
**Atores:** Atendente, Administrador

---

### RF21 - Geração de relatórios

O sistema deve permitir gerar relatórios de movimentações, empréstimos e manutenções.

**Prioridade:** Média  
**Atores:** Administrador

---

## 2.6 Acesso e Segurança

### RF22 - Autenticação de usuários

O sistema deve permitir autenticação de usuários através de login e senha.

**Prioridade:** Alta  
**Atores:** Administrador, Atendente

---

### RF23 - Controle de permissões

O sistema deve controlar permissões conforme o perfil do usuário.

**Prioridade:** Alta  
**Atores:** Sistema
