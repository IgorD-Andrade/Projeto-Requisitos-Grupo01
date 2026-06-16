# GAC — Gestão de Ativos CCT

<img src="Requisitos/image/logo_projeto_GAC.png" width="20%">

## 📌 Sobre o Projeto

O GAC (Gestão de Ativos CCT) é uma plataforma desenvolvida para auxiliar no controle, rastreamento e gerenciamento de projetores e demais ativos físicos do Centro de Ciências e Tecnologia (CCT).

O sistema busca substituir processos manuais e descentralizados por uma solução digital integrada utilizando identificação por tags NFC/RFID.

---

# 🎯 Objetivo

O projeto tem como objetivo melhorar o controle patrimonial dos projetores, permitindo:

* Rastreamento em tempo real
* Controle de empréstimos e devoluções
* Registro de movimentações
* Gestão de manutenção
* Identificação digital via NFC/RFID

---

# 🚨 Problema Atual

Atualmente, o controle de ativos é realizado de forma manual, gerando:

* Perda de informações
* Falta de rastreabilidade
* Dificuldade no controle de empréstimos
* Ausência de histórico confiável
* Fragilidade na responsabilização dos usuários

---

# 💡 Solução Proposta

A plataforma GAC permitirá:

* Cadastro de projetores
* Associação de tags NFC/RFID aos ativos
* Rastreamento de equipamentos
* Registro de empréstimos e devoluções
* Controle de manutenção
* Histórico completo de movimentações
* Geração de relatórios administrativos

---

# 🛠️ Funcionalidades

## 📦 Gerenciamento de Projetores

* Cadastro de projetores
* Atualização de dados
* Inativação de equipamentos
* Consulta de projetores

## 📡 Rastreamento NFC/RFID

* Leitura de tags NFC/RFID
* Identificação automática do projetor
* Consulta de localização
* Histórico de movimentações

## 🔄 Empréstimo e Devolução

* Solicitação de alocação
* Confirmação de empréstimo
* Registro de devolução
* Atualização automática de status

## 🔧 Manutenção

* Registro de defeitos
* Controle de manutenção
* Troca de projetores defeituosos

## 🔐 Segurança

* Autenticação de usuários
* Controle de permissões
* Auditoria de operações

---

# 👥 Equipe

| Nome        | Função                         |
| ----------- | ------------------------------ |
| João Pedro  | Desenvolvimento e documentação |
| Igor        | Desenvolvimento e documentação |
| Asafe       | Desenvolvimento e documentação |

---

# 📂 Estrutura do Projeto

```text
.
├── pitch.html                    <-- Apresentação Executiva (Pitch) do Projeto
├── Requisitos/
│   ├── visao-da-demanda.md
|   |
│   ├── image/
│   │
│   ├── Requisitos/
│   │   ├── requisitos-nao-funcionais.md
│   │   └── regras-de-negocio.md
│   │
│   ├── Diagramas/
|   |   ├── # Modelo de Caso de Uso.md
|   |   ├── Diagrama de Implantacao.md
|   |   ├── Diagrama_Componentes_GAC.md
|   |   ├── Diagrama_de_Implantacao.png
|   |   ├── Diagrama_de_casos_de_uso.jpg
|   |   ├── Diagrama_de_componentes.png
│   │
│   └── CasosDeUso/
|   |   ├── acesso_segurança/
|   |   ├── emprestimo_projetor/
|   |   ├── gerenciar_cadastro_projetor/
|   |   ├── gerenciar_manutenção/
|   |   ├── rastrear_projetor/
|   |   ├── realocar_projetor/
|   |   ├── relatorios_auditoria/
|   |   ├── substituir_projetor/
