# Especificação de Requisitos Não Funcionais

## Histórico de Versões

| Data | Versão | Descrição | Autor |
| --- | --- | --- | --- |
| 08/05/2026 | 1.0 | Criação inicial do documento de requisitos não funcionais do sistema GAC | João Pedro |
| 14/05/2026 | 1.1 | Refinamento e detalhamento dos requisitos não funcionais | João Pedro |

---

# 1. Requisitos de Produto

Especificam características de desempenho, segurança, usabilidade e confiabilidade da plataforma GAC.

---

## 1.1. Eficiência de Desempenho

### 1.1.1. Comportamento temporal

O sistema deve responder operações de leitura de tags NFC/RFID e consultas em até 3 segundos em condições normais de uso.

---

### 1.1.2. Capacidade

O sistema deve suportar múltiplas operações simultâneas de empréstimo, devolução e rastreamento sem degradação significativa de desempenho.

---

### 1.1.3. Uso de recursos

O sistema deve operar adequadamente em dispositivos móveis e computadores institucionais sem consumo excessivo de memória ou processamento.

---

## 1.2. Flexibilidade (Portabilidade)

### 1.2.1. Escalabilidade

O sistema deve permitir expansão futura para gerenciamento de outros ativos além de projetores.

---

### 1.2.2. Adaptabilidade

O sistema deve funcionar em diferentes dispositivos com suporte a NFC, incluindo smartphones Android compatíveis.

---

### 1.2.3. Instalabilidade

A aplicação deve permitir implantação simples em ambiente web institucional.

---

## 1.3. Confiabilidade

### 1.3.1. Disponibilidade

O sistema deve permanecer disponível durante o horário de funcionamento da instituição.

---

### 1.3.2. Recuperabilidade

O sistema deve minimizar perda de informações em caso de falhas inesperadas.

---

### 1.3.3. Integridade

As informações dos projetores e movimentações devem permanecer consistentes durante operações simultâneas.

---

## 1.4. Segurança

### 1.4.1. Confidencialidade

O sistema deve restringir acesso às funcionalidades administrativas apenas para usuários autorizados.

---

### 1.4.2. Integridade

O sistema deve impedir alterações indevidas nos registros de empréstimos, devoluções e manutenções.

---

### 1.4.3. Não repúdio

Toda operação realizada deve registrar o usuário responsável pela ação.

---

### 1.4.4. Autenticidade

O sistema deve autenticar usuários através de login e senha antes de permitir acesso às funcionalidades.

---

## 1.5. Capacidade de Interação (Usabilidade)

### 1.5.1. Facilidade de aprendizado

A interface deve permitir que usuários realizem operações básicas sem necessidade de treinamento avançado.

---

### 1.5.2. Operabilidade

As funcionalidades de empréstimo e devolução devem estar acessíveis de forma simples e intuitiva.

---

### 1.5.3. Proteção contra erros do usuário

O sistema deve apresentar mensagens de validação e confirmação durante operações críticas.

---

### 1.5.4. Responsividade

A interface deve adaptar-se adequadamente a computadores e dispositivos móveis.

---

## 1.6. Manutenibilidade

### 1.6.1. Modularidade

O sistema deve possuir estrutura modular para facilitar manutenção e evolução futura.

---

### 1.6.2. Modificabilidade

Novas funcionalidades e tipos de ativos devem poder ser adicionados sem impacto significativo nos módulos existentes.

---

## 1.7. Compatibilidade

### 1.7.1. Interoperabilidade

O sistema deve permitir integração com dispositivos e tags NFC/RFID utilizados pela instituição.

---

### 1.7.2. Coexistência

O sistema deve funcionar adequadamente em conjunto com os demais sistemas institucionais utilizados no ambiente acadêmico.

---

# 2. Requisitos Externos

## 2.1. Legislativo

O sistema deve respeitar políticas institucionais relacionadas ao armazenamento e uso de dados dos usuários.

---

# 3. Requisitos Organizacionais

## 3.1. Operacionais

O sistema será utilizado por administradores, atendentes e professores para gerenciamento de projetores.

---

## 3.2. Desenvolvimento

O projeto deverá utilizar controle de versão Git/GitHub para gerenciamento do código e documentação.

---

# 4. Checklist de Validação do Artefato (RNF)

## 4.1. Estrutura e escopo

- [x] O documento possui histórico de versões preenchido.
- [x] O escopo da solução está claro no documento.
- [x] Há requisitos registrados nas seções aplicáveis.
- [x] Os requisitos estão alinhados ao contexto do projeto.

---

## 4.2. Qualidade dos requisitos

- [x] Cada requisito está escrito de forma objetiva e verificável.
- [x] Os requisitos possuem critérios mensuráveis ou observáveis.
- [x] Não há requisitos duplicados ou conflitantes.

---

## 4.3. Conformidade e rastreabilidade

- [x] Requisitos de segurança foram contemplados.
- [x] Requisitos de integração NFC/RFID foram contemplados.
- [x] Os requisitos estão alinhados com a visão da demanda e funcionalidades do sistema.

---

## 4.4. Prontidão para uso

- [x] Os requisitos podem ser utilizados como base para implementação.
- [x] O documento está pronto para revisão e evolução futura.
