# Requisitos Não Funcionais

# 1. Introdução

Este documento apresenta os requisitos não funcionais da plataforma GAC, relacionados a desempenho, segurança, usabilidade e integração com tags NFC/RFID.

---

# 2. Requisitos Não Funcionais

### RNF01 - Desempenho

O sistema deve responder operações de consulta e leitura de tags NFC/RFID em até 3 segundos em condições normais de uso.

---

### RNF02 - Disponibilidade

O sistema deve permanecer disponível durante o horário de funcionamento da instituição para garantir acesso contínuo às operações de empréstimo e devolução.

---

### RNF03 - Segurança

O sistema deve exigir autenticação de usuários através de login e senha para acesso às funcionalidades administrativas e operacionais.

---

### RNF04 - Controle de acesso

O sistema deve restringir funcionalidades conforme o perfil do usuário autenticado (Administrador, Atendente e Professor).

---

### RNF05 - Persistência de dados

Os dados dos projetores, movimentações e históricos devem ser armazenados de forma persistente em banco de dados.

---

### RNF06 - Auditoria

O sistema deve registrar logs das operações realizadas pelos usuários, incluindo empréstimos, devoluções e alterações cadastrais.

---

### RNF07 - Compatibilidade NFC/RFID

O sistema deve suportar integração com dispositivos móveis e tags NFC/RFID utilizados pela instituição.

---

### RNF08 - Usabilidade

O sistema deve possuir interface intuitiva e responsiva, permitindo utilização em computadores e dispositivos móveis.

---

### RNF09 - Integridade de dados

O sistema deve garantir consistência das informações durante operações de cadastro, movimentação e atualização de projetores.

---

### RNF10 - Escalabilidade

O sistema deve permitir expansão futura para gerenciamento de outros tipos de ativos além de projetores.
