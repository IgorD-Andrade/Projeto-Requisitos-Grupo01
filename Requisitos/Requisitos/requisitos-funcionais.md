# Requisitos Funcionais

## Histórico de Versões

| Data | Versão | Descrição | Autor |
| --- | --- | --- | --- |
| 08/05/2026 | 1.0 | Criação inicial do documento de requisitos funcionais do sistema GAC | João Pedro |

---

## 1. Introdução

Este documento apresenta os requisitos funcionais da plataforma GAC (Gestão de Ativos CCT), responsável pelo controle, rastreamento e gerenciamento de projetores através de identificação digital por tags NFC/RFID.

---

## 2. Requisitos Funcionais

### RF01 - Cadastro de projetores

O sistema deve permitir cadastrar projetores contendo:

- Número de patrimônio
- Modelo
- Marca
- Localização
- Estado do equipamento
- Identificação por tag NFC/RFID

**Prioridade:** Alta  
**Atores:** Administrador

---

### RF02 - Atualização de dados de projetores

O sistema deve permitir atualizar informações cadastrais dos projetores.

**Prioridade:** Média  
**Atores:** Administrador

---

### RF03 - Inativação de projetores

O sistema deve permitir inativar projetores fora de uso ou indisponíveis.

**Prioridade:** Média  
**Atores:** Administrador

---

### RF04 - Consulta de projetores

O sistema deve permitir consultar projetores cadastrados utilizando filtros.

**Prioridade:** Alta  
**Atores:** Administrador, Atendente

---

### RF05 - Rastreamento de projetores

O sistema deve permitir visualizar a localização atual do projetor.

**Prioridade:** Alta  
**Atores:** Atendente

---

### RF06 - Histórico de movimentações

O sistema deve permitir consultar o histórico de movimentações realizadas pelos projetores.

**Prioridade:** Alta  
**Atores:** Administrador

---

### RF07 - Leitura de tag NFC/RFID

O sistema deve permitir identificar rapidamente um projetor através da leitura da tag NFC/RFID.

**Prioridade:** Alta  
**Atores:** Atendente

---

### RF08 - Registro de empréstimo

O sistema deve permitir registrar empréstimos de projetores para usuários autorizados.

**Prioridade:** Alta  
**Atores:** Atendente

---

### RF09 - Registro de devolução

O sistema deve permitir registrar devoluções de projetores e atualizar seus estados.

**Prioridade:** Alta  
**Atores:** Atendente

---

### RF10 - Consulta de disponibilidade

O sistema deve permitir consultar projetores disponíveis para empréstimo.

**Prioridade:** Alta  
**Atores:** Professor, Atendente

---

### RF11 - Registro de manutenção

O sistema deve permitir registrar manutenções preventivas e corretivas dos projetores.

**Prioridade:** Média  
**Atores:** Técnico, Administrador

---

### RF12 - Consulta de status de manutenção

O sistema deve permitir consultar o status de manutenção dos projetores.

**Prioridade:** Média  
**Atores:** Professor, Atendente

---

### RF13 - Realocação de projetores

O sistema deve permitir registrar a transferência de projetores entre salas ou setores.

**Prioridade:** Média  
**Atores:** Administrador

---

### RF14 - Troca de projetor defeituoso

O sistema deve permitir substituir projetores defeituosos por outros disponíveis.

**Prioridade:** Média  
**Atores:** Atendente

---

### RF15 - Autenticação de usuários

O sistema deve permitir autenticação de usuários através de login e senha.

**Prioridade:** Alta  
**Atores:** Administrador, Atendente

---

### RF16 - Controle de permissões

O sistema deve controlar permissões conforme o perfil do usuário.

**Prioridade:** Alta  
**Atores:** Sistema

---

### RF17 - Geração de relatórios

O sistema deve permitir gerar relatórios de movimentações, empréstimos e manutenções.

**Prioridade:** Média  
**Atores:** Administrador
