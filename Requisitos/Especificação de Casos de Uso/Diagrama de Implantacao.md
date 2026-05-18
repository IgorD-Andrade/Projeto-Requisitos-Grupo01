# Diagrama de Implantação do Sistema GAC



## 1. Objetivo do artefato

Este artefato descreve o **diagrama de implantação (deployment)** do sistema GAC – Gestão de Ativos CCT.  
Ele mostra **onde** os componentes de software são instalados e **como** se distribuem nos diferentes nós físicos (servidores, nuvem AWS e dispositivos dos usuários), a partir da arquitetura definida na Visão da Demanda.

## 2. Diagrama de Implantação do GAC

A figura a seguir apresenta o diagrama de implantação do sistema GAC.

![GAC – Diagrama de Implantação](Diagrama_de_Implantacao.png)

---

## 3. Nós principais (máquinas/ambientes)

### 3.1 Dispositivo do Usuário

- **Descrição:** computador ou notebook utilizado por professores, atendentes e administradores.
- **Software implantado:**  
  - `ClienteWebGAC.js` (aplicação web carregada no navegador).
- **Função:** interface de acesso ao sistema GAC, permitindo realizar:
  - consultas de disponibilidade (F4.3),  
  - registro de empréstimos e devoluções (F4.1, F4.2),  
  - cadastro e consulta de projetores (F1.x),  
  - consulta de manutenção (F3.2), relatórios (F8.x) etc.

### 3.2 Servidor de Aplicação – GAC-Core

- **Descrição:** servidor (na nuvem AWS) que hospeda a lógica de negócio da solução.
- **Software implantado:**  
  - `GAC-Core` (backend / API REST do GAC).
- **Responsabilidades principais:**
  - Processar **empréstimos, devoluções e localização** (F2.x, F4.x, F6.1).  
  - Processar **cadastro, atualização, inativação e transferência de projetores** (F1.x, F5.1).  
  - Processar **registros de manutenção e consulta de status** (F3.1, F3.2).  
  - Orquestrar chamadas ao serviço de autenticação e ao módulo de relatórios.  
  - Acessar o banco de dados GAC.

### 3.3 Servidor de Banco de Dados

- **Descrição:** nó de banco de dados relacional na AWS (por exemplo, RDS PostgreSQL ou MySQL).
- **Software implantado:**  
  - `GAC_DB` (banco de dados da aplicação).
- **Função:** armazenar de forma centralizada e consistente:
  - cadastro de projetores;  
  - movimentações e histórico (empréstimos, devoluções, transferências – F2.2, F4.x, F5.1);  
  - registros de manutenção (F3.x);  
  - dados de autenticação e perfis de usuário;  
  - informações utilizadas nos relatórios (F8.x).

### 3.4 Servidor de Relatório

- **Descrição:** servidor dedicado (ou serviço na nuvem) para geração de relatórios administrativos.
- **Software implantado:**  
  - `ExternoAutenticacaoApp` ou módulo equivalente de relatórios do GAC.
- **Função:** gerar relatórios e exportações relacionados a:
  - movimentações de projetores (F8.1);  
  - manutenções e status dos equipamentos (F8.2).
- **Integrações:**
  - Consome dados do `GAC_DB`.  
  - É acionado pelo backend `GAC-Core` quando o usuário solicita relatórios via interface administrativa.

### 3.5 Servidor de Autenticação Externa

- **Descrição:** serviço independente (interno ou terceiro) responsável por autenticação e, eventualmente, autorização.
- **Software implantado:**  
  - `ServicoAutenticacao` (aplicação de autenticação).
- **Função:**
  - Validar credenciais de usuário (F7.1 – Autenticação de usuários).  
  - Fornecer informações de perfil/permissões para o backend aplicar o controle de acesso (F7.2 – Controle de permissões).
- **Integrações:**
  - Comunica-se com o `GAC-Core` para autenticar logins vindos do `ClienteWebGAC.js`.

### 3.6 Dispositivo do Cliente com Leitor (quando aplicável)

- **Descrição:** estação que possui o **leitor NFC/RFID** conectado e o cliente web carregado.
- **Software implantado:**  
  - `ClienteAutowGAC.js` (variação do cliente web, capaz de integrar-se ao leitor).  
- **Função:**
  - Realizar **leitura automática das tags NFC/RFID** associadas aos projetores (F2.3).  
  - Enviar a identificação lida para o backend `GAC-Core`, que resolve a localização, histórico e demais ações.

---

## 4. Comunicação entre nós

De forma resumida:

- **Dispositivo do Usuário**  
  ↔ comunica-se via HTTP/HTTPS com o **Servidor de Aplicação – GAC-Core** (API REST).

- **Servidor de Aplicação – GAC-Core**  
  ↔ acessa o **Servidor de Banco de Dados** para leitura/gravação dos dados.  
  ↔ chama o **Servidor de Autenticação Externa** para autenticar usuários.  
  ↔ aciona o **Servidor de Relatório** para geração de relatórios (F8.1, F8.2).

- **Dispositivo com Leitor NFC/RFID**  
  ↔ executa o cliente web especializado (`ClienteAutowGAC.js`), que conversa com o backend da mesma forma que o `ClienteWebGAC.js`, mas incluindo os dados recebidos do leitor físico (F2.3).

---

## 5. Coerência com a Visão da Demanda

O diagrama de implantação é coerente com a **Visão da Demanda** do GAC porque:

- Representa uma **plataforma web centralizada** (cliente web + servidor de aplicação).  
- Inclui um **banco de dados centralizado** que garante histórico e rastreabilidade.  
- Considera o uso de **tags NFC/RFID** através de dispositivo com leitor integrado.  
- Prevê serviços de **autenticação e relatórios**, refletindo as necessidades de:
  - acesso e segurança (F7.1, F7.2);  
  - auditoria e relatórios (F8.1, F8.2).

---
