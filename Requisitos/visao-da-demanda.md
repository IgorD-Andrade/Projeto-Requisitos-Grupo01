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

| Nome | Papel | Responsabilidades | Representante |
|------|------|-----------------|--------------|
| Direção do CCT | Cliente | Garantir controle patrimonial | - |
| Coordenação/Administração | Stakeholder | Gerenciar processos e padronização | - |
| Professores | Usuário final | Solicitar e utilizar ativos | - |
| Atendentes | Usuário operacional | Registrar movimentações | - |
| Equipe de TI | Desenvolvimento | Implementar e manter o sistema | - |

---

## 5. Personas

Descreva perfis típicos dos usuários ou sistemas que interagem com a solução.

**Exemplo:**

### 5.1. Aluno

- **Descrição:** Estudante de graduação que busca estágio obrigatório.
- **Objetivo:** Conseguir estágio e acompanhar o processo online.

### 5.2. Professor Orientador

- **Descrição:** Docente responsável por aprovar relatórios de estágio.

## 6. Necessidades e Funcionalidades

Relacione as necessidades e funcionalidades, detalhando para cada uma os atores, frequência e valor.

**Exemplo:**

### Necessidade 1: Solicitar estágio

#### F1.1 Cadastro de solicitação de estágio

- **Descrição:** Permite ao aluno cadastrar uma nova solicitação de estágio.
- **Incluída**
- **Atores:** Aluno
- **Frequência:** Alta
- **Valor:** Alto

### Necessidade 2: Aprovar relatório

#### F2.1 Aprovação de relatório de estágio

- **Descrição:** Permite ao professor aprovar ou rejeitar relatórios enviados.
- **Incluída**
- **Atores:** Professor Orientador
- **Frequência:** Média
- **Valor:** Alto

## 7. Arquitetura da Demanda

Inclua um diagrama simples (pode ser desenhado à mão e digitalizado, ou feito em ferramenta online) mostrando os principais componentes e integrações.

**Exemplo:**

> O sistema será composto por três módulos principais: Portal do Aluno, Portal do Professor e Módulo Administrativo. Integração com sistema acadêmico via API REST.

Sugestão: utilize mapas de histórias ou diagramas de caso de uso (UML) para ilustrar.

---

## Checklist de Validação do Documento de Visão

- [ ] O objetivo está claro e alinhado ao problema/necessidade?
- [ ] A proposta de valor é mensurável e relevante?
- [ ] Todas as partes interessadas estão listadas com papéis definidos?
- [ ] Existem pelo menos duas personas descritas?
- [ ] Todas as necessidades e funcionalidades estão relacionadas a atores?
- [ ] Há indicação de valor e frequência para cada funcionalidade?
- [ ] A arquitetura está ilustrada (mesmo que de forma simples)?
- [ ] O documento está escrito em linguagem clara e objetiva?

---

> Consulte exemplos e dicas em: [Guia de Elaboração da Visão](../../../Elicitacao/VisaoDemanda.md)
