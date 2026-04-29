# Visão da Demanda (VD)

## Histórico de Versões

| Data | Versão | Descrição | Autor |
| --- | --- | --- | --- |
| 29/04/2026 | 1.0 | Criação inicial do documento de visão da demanda do sistema GAC | João Pedro |

---

## 1. Objetivo

<img src="image/logo_projeto_GAC.png" width="20%">

Este documento visa definir a proposta de valor da demanda da plataforma GAC (Gestão de Ativos CCT), que visa melhorar o controle e a rastreabilidade de ativos físicos, substituindo processos manuais e descentralizados por uma solução digital integrada.

---

## 2. Proposta de Valor

A solução permitirá:

- Redução de erros causados por registros manuais
- Rastreabilidade em tempo real dos ativos
- Maior responsabilização através de registros auditáveis
- Centralização das informações em uma única base de dados
- Melhoria na tomada de decisão por meio de relatórios e métricas

---

## 3. Descrição da Demanda

Atualmente, o controle de ativos é realizado de forma manual e com comunicação informal, o que gera inconsistências, perda de informações e falta de rastreabilidade.

Esse cenário dificulta responder perguntas como:
- Onde está o item?
- Quem utilizou?
- Qual o estado atual do equipamento?

Além disso, há fragilidade na responsabilização e ausência de histórico confiável.

A plataforma GAC surge como solução para digitalizar esse processo, permitindo o rastreamento completo do ciclo de vida dos ativos, desde sua retirada até sua devolução.

---

## 4. Partes Interessadas

| Nome | Papel | Responsabilidades | Representante | Nível de Influência |
|------|------|-----------------|--------------|---------------------|
| Direção do CCT | Cliente | Garantir controle patrimonial | - | Alto |
| Coordenação/Administração | Stakeholder | Gerenciar processos | - | Alto |
| Professores | Usuário final | Utilizar ativos | - | Médio |
| Atendentes | Usuário operacional | Registrar movimentações | - | Alto |
| Equipe de TI | Desenvolvimento | Implementar sistema | - | Médio |

---

## 5. Personas

### 5.1 Professor Solicitante

- **Descrição:** Professor que necessita utilizar equipamentos para atividades acadêmicas.
- **Objetivo:** Localizar e retirar ativos de forma rápida e confiável.

### 5.2 Atendente Validador

- **Descrição:** Responsável pelo registro e controle da movimentação dos ativos.
- **Objetivo:** Garantir que todas as movimentações sejam registradas corretamente.

### 5.3 Administrador de Inventário

- **Descrição:** Responsável pela gestão geral dos ativos.
- **Objetivo:** Manter a base de dados atualizada e confiável, além de gerar relatórios.

---

## 6. Necessidades e Funcionalidades

### Necessidade 1: Controle de movimentação de ativos

#### F1.1 Registro de retirada de ativo

- **Descrição:** Permite registrar a retirada de um ativo por um usuário.
- **Incluída**
- **Atores:** Atendente
- **Frequência:** Alta
- **Valor:** Alto

#### F1.2 Registro de devolução de ativo

- **Descrição:** Permite registrar a devolução e estado do ativo.
- **Incluída**
- **Atores:** Atendente
- **Frequência:** Alta
- **Valor:** Alto

---

### Necessidade 2: Rastreabilidade e histórico

#### F2.1 Consulta de histórico de ativos

- **Descrição:** Permite visualizar todo o histórico de uso de um ativo.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Média
- **Valor:** Alto

---

### Necessidade 3: Gestão e auditoria

#### F3.1 Geração de relatórios

- **Descrição:** Geração de relatórios para controle e auditoria.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Média
- **Valor:** Alto

---

## 7. Arquitetura da Demanda

O sistema será composto por uma plataforma web centralizada, acessada por diferentes perfis de usuários (professores, atendentes e administradores).

A aplicação contará com:

- Interface para registro e consulta de ativos
- Backend responsável pelo processamento e armazenamento de dados
- Banco de dados centralizado para garantir integridade e histórico

---

## Checklist de Validação do Documento de Visão

- [x] O objetivo está claro e alinhado ao problema/necessidade
- [x] A proposta de valor é relevante
- [x] As partes interessadas estão identificadas
- [x] Existem personas descritas
- [x] Funcionalidades relacionadas a atores
- [x] Valor e frequência definidos
- [ ] Arquitetura ilustrada (opcional adicionar diagrama)
- [x] Linguagem clara e objetiva

---
