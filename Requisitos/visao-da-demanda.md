# Visão da Demanda (VD)

## Histórico de Versões

| Data | Versão | Descrição | Autor |
| --- | --- | --- | --- |
| 29/04/2026 | 1.0 | Criação inicial do documento de visão da demanda do sistema GAC | João Pedro |
| 30/04/2026 | 1.1 | Adição da parte interessada para tratar o domínio de negócio | João Pedro |
| 08/05/2026 | 1.2 | Levantamento das necessidades e funcionalidades do sistema | João Pedro |
| 22/05/2026 | 1.2 | Adição do diagrama de casos de uso, diagrama de implantação e diagrama de componenes | Igor |

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
- **Objetivo:** Localizar, retirar e Transferir ativos de forma rápida e confiável.

### 5.2 Atendente Validador

- **Descrição:** Responsável pelo registro e controle da movimentação dos ativos.
- **Objetivo:** Garantir que todas as movimentações sejam registradas corretamente.

### 5.3 Administrador de Inventário

- **Descrição:** Responsável pela gestão geral dos ativos.
- **Objetivo:** Manter a base de dados atualizada e confiável, além de gerar relatórios.


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

#### F4.4 Confirmar recebimento de projetor pela leitura da tag

- **Descrição:** Permite ao professor confirmar o recebimento e a responsabilidade pelo projetor através da leitura da tag NFC/RFID associada ao equipamento.
- **Incluída**
- **Atores:** Professor
- **Frequência:** Alta
- **Valor:** Alto

---

### Necessidade 5: Realocar projetores

#### F5.1 Transferir projetor entre salas/setores

- **Descrição:** Permite registrar mudança de localização do projetor.
- **Incluída**
- **Atores:** Professor
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

O sistema GAC será implantado como uma **plataforma web centralizada**, acessada via navegador pelos diferentes perfis de usuários (professores, atendentes e administradores) e integrada a leitores NFC/RFID para identificação dos projetores.

Em alto nível, a solução é composta por:

- **Frontend web** nos dispositivos dos usuários, para interação com o sistema;
- **Backend central (API REST)** responsável pelas regras de negócio;
- **Banco de dados relacional único**, para persistência e histórico das informações;
- Serviços de **autenticação**, **relatórios** e **integração com leitores NFC/RFID**.

Essa visão é detalhada nos diagramas UML apresentados na subseção a seguir.

### 7.1. Diagramas UML

A arquitetura e a estrutura da solução GAC são representadas por três diagramas UML:

- o **Diagrama de Caso de Uso**, que mostra os atores e as funcionalidades (F1.1 a F8.2);
- o **Diagrama de Componentes**, que mostra como as funcionalidades são agrupadas em módulos de software;
- o **Diagrama de Implantação**, que mostra como esses módulos são distribuídos nos ambientes de execução (dispositivos, servidores e nuvem).

#### 7.1.1. Diagrama de Caso de Uso

O diagrama de casos de uso do GAC ilustra os atores e as principais interações com o sistema, garantindo a cobertura de todas as funcionalidades definidas na seção 6.

<img src="Especificação de Casos de Uso/Diagrama_de_casos_de_uso.jpg" width="80%">

**Atores principais:**

- Professor
- Atendente Validador
- Administrador de Inventário

**Grupos de casos de uso (funcionalidades):**

- **F1.x – Gerenciar cadastro de projetores**  
  Cadastro, atualização, inativação e consulta de projetores.

- **F2.x – Rastrear projetores**  
  Localização, histórico de movimentações e leitura de tags NFC/RFID.

- **F3.x – Gerenciar manutenção de projetores**  
  Registro de manutenção e consulta de status.

- **F4.x e F6.1 – Gerenciar empréstimos e troca de projetores**  
  Registro de empréstimo, devolução, consulta de disponibilidade e troca de projetor com defeito.

- **F5.1 – Realocar projetores**  
  Transferência de projetores entre salas/setores e entre professores.

- **F7.x – Acesso e segurança**  
  Autenticação de usuários e controle de permissões.

- **F8.x – Relatórios e auditoria**  
  Relatórios de movimentações e de manutenção.

#### 7.1.2. Diagrama de Componentes

O diagrama de componentes descreve os principais **módulos de software** do GAC e suas dependências, mostrando a arquitetura lógica da solução.

<img src="Especificação de Casos de Uso/Diagrama_de_componentes.png" width="80%">

**Componentes de frontend:**

- **GAC-InterfaceProfessor (Frontend)**  
  Interface web usada pelo Professor Solicitante, focada em:
  - consulta de disponibilidade de projetores (F4.3);
  - consulta de status de manutenção (F3.2).

- **GAC-InterfaceAdministrativa (Frontend)**  
  Interface web para Administrador de Inventário e Atendente Validador, apoiando:
  - gestão de projetores (F1.x);
  - rastreamento e histórico (F2.x);
  - empréstimos, devoluções e trocas (F4.x, F6.1);
  - geração de relatórios (F8.x).

**Componentes de backend / API REST:**

- **GAC-ModuloEmprestimos (Backend/REST)**  
  Implementa regras de negócio de:
  - rastreamento e localização (F2.1, F2.2);
  - leitura de tag NFC/RFID em conjunto com o adaptador (F2.3);
  - registro de empréstimos e devoluções (F4.1, F4.2);
  - consulta de disponibilidade (F4.3);
  - troca de projetor com defeito (F6.1).

- **GAC-ModuloInventario&Manutencao (Backend/REST)**  
  Implementa regras de:
  - cadastro, atualização, inativação e consulta de projetores (F1.x);
  - registro e consulta de manutenções (F3.x);
  - transferência de projetores entre salas/setores (F5.1);
  - apoio à geração de relatórios (F8.x).

- **GAC-BancoDeDados**  
  Responsável pela persistência dos dados do GAC:
  - projetores, movimentações, manutenções, usuários e perfis;
  - base para relatórios de movimentação e manutenção.

**Componentes de integração e serviços externos:**

- **GAC-AdaptadorNFC-RFID**  
  Adaptador que integra o backend ao leitor/sistema NFC/RFID, recebendo leituras de tags e associando aos projetores (F2.3).

- **LeitorNFC-RFID-SistemaExterno**  
  Componente externo que realiza a leitura física das tags NFC/RFID.

- **Serviço de Autenticação / Controle de Acesso**  
  Responsável por autenticar usuários e informar perfis e permissões ao backend (apoio a F7.1 e F7.2).

- **Módulo de Relatórios**  
  Componente que gera relatórios de movimentação e manutenção (F8.1, F8.2), consumindo dados do banco.

Esse diagrama mostra como as funcionalidades F1.x a F8.x foram distribuídas em módulos coesos, alinhados com a Visão da Demanda.

#### 7.1.3. Diagrama de Implantação

O diagrama de implantação representa como os componentes do GAC são distribuídos nos **ambientes de execução** (dispositivos, servidores e nuvem), evidenciando a infraestrutura necessária para operar a solução.

<img src="Especificação de Casos de Uso/Diagrama_de_Implantacao.png" width="80%">

**Ambientes e nós principais:**

- **Dispositivos dos Usuários (Professores, Atendentes, Administradores)**  
  - Executam o cliente web GAC no navegador (`ClienteWebGAC.js`).  
  - Em estações específicas, executam uma variação integrada ao leitor (`ClienteAutowGAC.js`) para leitura automática de tags NFC/RFID (F2.3).

- **Servidor de Aplicação – GAC-Core (Backend / API REST)**  
  - Hospeda os módulos de backend (`GAC-ModuloEmprestimos` e `GAC-ModuloInventario&Manutencao`).  
  - Processa as regras de negócio ligadas a:
    - empréstimos, devoluções, rastreamento e troca de projetores (F2.x, F4.x, F6.1);
    - cadastro, atualização, inativação e transferência de projetores (F1.x, F5.1);
    - manutenção (F3.x);
    - autenticação/autorização (F7.x);
    - relatórios (F8.x).  
  - Acessa o banco de dados e orquestra chamadas ao serviço de autenticação e ao módulo de relatórios.

- **Servidor de Banco de Dados (GAC_DB)**  
  - Banco de dados relacional (por exemplo, AWS RDS) que armazena:
    - cadastros de projetores;
    - movimentações e histórico (empréstimos, devoluções, transferências);
    - registros de manutenção;
    - dados de usuários e perfis;
    - informações usadas em relatórios.

- **Servidor de Relatório**  
  - Serviço ou nó dedicado à geração de relatórios administrativos.  
  - Consome dados do `GAC_DB` para produzir:
    - relatórios de movimentações (F8.1);
    - relatórios de manutenção (F8.2).  
  - É acionado pelo backend quando o usuário solicita relatórios via interface administrativa.

- **Servidor de Autenticação Externa**  
  - Serviço responsável por autenticação de usuários (`ServicoAutenticacao`).  
  - Valida credenciais (F7.1) e fornece perfis/permissões para que o backend aplique o controle de acesso (F7.2).

- **Dispositivo com Leitor NFC/RFID**  
  - Estação que possui leitor NFC/RFID conectado ao cliente web.  
  - Permite leitura das tags associadas aos projetores (F2.3), enviando os dados para o backend `GAC-Core`, que resolve localização, histórico e demais ações.

**Comunicação entre nós (resumo):**

- Os dispositivos dos usuários se comunicam com o **Servidor de Aplicação – GAC-Core** via HTTP/HTTPS.  
- O backend acessa o **Servidor de Banco de Dados** para leitura/gravação.  
- O backend consome o **Serviço de Autenticação** e o **Servidor de Relatório** conforme necessário.  
- As estações com leitor NFC/RFID enviam as leituras ao backend, por meio do cliente web integrado.

Essa arquitetura de implantação está alinhada à proposta de uma solução **web centralizada**, com banco de dados único e integração com dispositivos NFC/RFID, conforme descrito na Visão da Demanda.
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
