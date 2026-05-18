# Visão da Demanda (VD)

## Histórico de Versões

| Data | Versão | Descrição | Autor |
| --- | --- | --- | --- |
| 29/04/2026 | 1.0 | Criação inicial do documento de visão da demanda do sistema GAC | João Pedro |
| 30/04/2026 | 1.1 | Adição da parte interessada para tratar o domínio de negócio | João Pedro |
| 08/05/2026 | 1.2 | Levantamento das necessidades e funcionalidades do sistema | João Pedro |

---

## 1. Objetivo

<img src="image/logo_projeto_GAC.png" width="20%">

Este documento visa definir a proposta de valor da plataforma GAC (Gestão de Ativos CCT), que busca melhorar o controle e a rastreabilidade de projetores do CCT por meio de identificação digital utilizando tags NFC/RFID, substituindo processos manuais e descentralizados por uma solução integrada.

---

## 2. Proposta de Valor

A solução permitirá:

- Redução de erros causados por registros manuais
- Rastreabilidade em tempo real dos ativos
- Maior responsabilização através de registros auditáveis
- Centralização das informações em uma única base de dados
- Melhoria na tomada de decisão por meio de relatórios e métricas
- Automatização da identificação e movimentação de ativos através de tags NFC/RFID

---

## 3. Descrição da Demanda

Atualmente, o controle de ativos é realizado de forma manual e com comunicação informal, o que gera inconsistências, perda de informações e falta de rastreabilidade.

Esse cenário dificulta responder perguntas como:
- Onde está o item?
- Quem utilizou?
- Qual o estado atual do equipamento?

Além disso, há fragilidade na responsabilização e ausência de histórico confiável.

A plataforma GAC surge como solução para digitalizar esse processo, permitindo o rastreamento completo do ciclo de vida dos ativos, desde sua retirada até sua devolução.

Cada ativo será associado a uma tag de identificação (NFC/RFID), permitindo registro rápido de retirada, devolução e consulta de informações através da leitura da tag, aumentando a precisão e reduzindo falhas humanas.

---

## 4. Partes Interessadas

| Nome | Papel | Responsabilidades | Representante | Nível de Influência |
|------|------|-----------------|--------------|---------------------|
| Direção do CCT | Cliente | Garantir controle patrimonial | Jakson | Alto |
| Coordenação/Administração | Stakeholder | Gerenciar processos | Fabiana | Alto |
| Professores | Usuário final | Utilizar ativos | Marcelo Bezerra | Médio |
| Atendentes | Usuário operacional | Registrar movimentações | Kildery | Alto |
| Equipe de TI | Desenvolvimento | Implementar sistema | Grupo01 | Médio |

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

### 5.4 Administrador de Inventário

- **Descrição:** Responsável por Registrar Manutenções e Controle de permissões.
- **Objetivo:** Manter o sistema operando.


---

## 6. Necessidades e Funcionalidades

### Necessidade 1: Gerenciar cadastro de projetores

#### F1.1 Cadastro de projetor

- **Descrição:** Permite cadastrar projetores com informações como patrimônio, modelo, localização e identificação por tag NFC/RFID.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Alta
- **Valor:** Alto

#### F1.2 Atualizar dados de projetor

- **Descrição:** Permite editar informações cadastrais dos projetores.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Média
- **Valor:** Alto

#### F1.3 Inativar projetor

- **Descrição:** Permite desativar projetores fora de uso.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Baixa
- **Valor:** Médio

#### F1.4 Consultar projetores

- **Descrição:** Permite consultar projetores cadastrados e seus estados atuais.
- **Incluída**
- **Atores:** Administrador, Atendente
- **Frequência:** Alta
- **Valor:** Alto

---

### Necessidade 2: Rastrear projetores

#### F2.1 Localizar projetor

- **Descrição:** Permite identificar a localização atual do projetor.
- **Incluída**
- **Atores:** Atendente
- **Frequência:** Alta
- **Valor:** Alto

#### F2.2 Consultar histórico de movimentação

- **Descrição:** Permite visualizar todas as movimentações realizadas pelo projetor.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Média
- **Valor:** Alto

#### F2.3 Leitura de tag NFC/RFID

- **Descrição:** Permite identificar rapidamente um projetor através da leitura da tag.
- **Incluída**
- **Atores:** Atendente
- **Frequência:** Alta
- **Valor:** Alto

---

### Necessidade 3: Gerenciar manutenção de projetores

#### F3.1 Registrar manutenção

- **Descrição:** Permite registrar manutenções preventivas e corretivas.
- **Incluída**
- **Atores:** Técnico/Administrador
- **Frequência:** Média
- **Valor:** Alto

#### F3.2 Consultar status de manutenção

- **Descrição:** Permite verificar se um projetor está disponível ou em manutenção.
- **Incluída**
- **Atores:** Atendente, Professor
- **Frequência:** Alta
- **Valor:** Alto

---

### Necessidade 4: Gerenciar empréstimo de projetores

#### F4.1 Registrar aluguel/empréstimo

- **Descrição:** Permite registrar a retirada de projetores por usuários autorizados.
- **Incluída**
- **Atores:** Atendente
- **Frequência:** Alta
- **Valor:** Alto

#### F4.2 Registrar devolução

- **Descrição:** Permite registrar a devolução do projetor e atualizar seu status.
- **Incluída**
- **Atores:** Atendente
- **Frequência:** Alta
- **Valor:** Alto

#### F4.3 Consultar disponibilidade

- **Descrição:** Permite visualizar projetores disponíveis para empréstimo.
- **Incluída**
- **Atores:** Professor, Atendente
- **Frequência:** Alta
- **Valor:** Alto

---

### Necessidade 5: Realocar projetores

#### F5.1 Transferir projetor entre salas/setores

- **Descrição:** Permite registrar mudança de localização do projetor.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Média
- **Valor:** Médio

---

### Necessidade 6: Substituir projetores defeituosos

#### F6.1 Trocar projetor com defeito

- **Descrição:** Permite substituir um projetor indisponível por outro disponível.
- **Incluída**
- **Atores:** Atendente
- **Frequência:** Média
- **Valor:** Alto

---

### Necessidade 7: Acesso e segurança

#### F7.1 Autenticação de usuários

- **Descrição:** Permite login de usuários autorizados no sistema.
- **Incluída**
- **Atores:** Administrador, Atendente
- **Frequência:** Alta
- **Valor:** Alto

#### F7.2 Controle de permissões

- **Descrição:** Define permissões conforme o perfil do usuário.
- **Incluída**
- **Atores:** Sistema
- **Frequência:** Alta
- **Valor:** Alto

---

### Necessidade 8: Relatórios e auditoria

#### F8.1 Gerar relatório de movimentações

- **Descrição:** Gera relatórios de empréstimos, devoluções e movimentações.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Média
- **Valor:** Alto

#### F8.2 Gerar relatório de manutenção

- **Descrição:** Gera relatórios de projetores em manutenção.
- **Incluída**
- **Atores:** Administrador
- **Frequência:** Média
- **Valor:** Médio

---

## 7. Arquitetura da Demanda

O sistema será composto por uma plataforma web centralizada, acessada por diferentes perfis de usuários (professores, atendentes e administradores). Além da plataforma web, o sistema utilizará identificação digital por tags NFC/RFID acopladas aos ativos, permitindo integração entre os equipamentos físicos e o sistema de rastreamento.

A aplicação contará com:

- Interface para registro e consulta de ativos
- Backend responsável pelo processamento e armazenamento de dados
- Banco de dados centralizado para garantir integridade e histórico

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
