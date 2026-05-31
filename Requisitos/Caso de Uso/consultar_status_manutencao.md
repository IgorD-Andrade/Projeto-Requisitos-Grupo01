# Caso de Uso – F3.2 Consultar Status de Manutenção

## Histórico de Versões

| Data       | Versão | Descrição                                      | Autor |
|-----------|--------|-----------------------------------------------|-------|
| 31/05/2026 | 1.0    | Criação do caso de uso Consultar Status de Manutenção | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Consultar Status de Manutenção

## 1.2 Objetivo

Permitir que o usuário consulte se um projetor está disponível, em manutenção, aguardando manutenção ou outro status relacionado, visualizando também informações básicas sobre a manutenção atual ou mais recente.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Professor  
- Atendente

## 2.2 Secundários

- Sistema de Banco de Dados  
- Tag NFC/RFID (quando a consulta é feita via leitura da tag)

---

# 3. Precondições

- O usuário (Professor ou Atendente) deve estar **autenticado**, quando o acesso exigir login.
- O projetor deve estar **cadastrado** no sistema.
- O sistema deve estar operacional e com acesso ao banco de dados.
- Quando a consulta for feita via NFC, o dispositivo deve estar habilitado para leitura da tag.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O usuário acessa o sistema GAC e seleciona a opção **"Consultar Status de Manutenção"**.

### P2.
O sistema oferece opções de identificação do projetor:
- leitura de **tag NFC/RFID**; ou  
- busca por **patrimônio** (ou outro identificador cadastrado).

### P3.
O usuário escolhe o método de identificação:

- Se optar por **leitura de tag**, aproxima o dispositivo do projetor para ler a tag NFC/RFID; ou  
- Se optar por **patrimônio**, informa o código do projetor no campo correspondente.

### P4.
O sistema localiza o projetor no cadastro, a partir da tag ou do patrimônio informado.

### P5.
O sistema consulta o **status atual** do projetor em relação à manutenção, como por exemplo:
- Disponível (sem manutenção ativa);  
- Em manutenção;  
- Aguardando manutenção;  
- Manutenção concluída recentemente.

### P6.
O sistema exibe na tela as informações de status, incluindo:

- Patrimônio e modelo do projetor;  
- Status atual de manutenção;  
- Quando houver manutenção ativa:
  - tipo de manutenção (preventiva/corretiva);
  - data de abertura da manutenção;
  - responsável pelo registro (Técnico/Administrador);
  - observações registradas (resumo).


### P7.
O usuário visualiza as informações e encerra a consulta.

---

# 5. Fluxos Alternativos

## A1. Usuário refina a consulta por filtros

### A1.1
No passo P2, além da identificação direta, o sistema permite filtros como:
- listar projetores **em manutenção**;
- listar projetores **aguardando manutenção**.

### A1.2
O usuário seleciona o filtro desejado.

### A1.3
O sistema apresenta uma lista de projetores que atendem ao filtro, com:
- patrimônio;
- modelo;
- status de manutenção;
- data da última alteração de status.

### A1.4
O usuário seleciona um projetor da lista.

### A1.5
O fluxo continua a partir do passo P5, exibindo o status detalhado daquele projetor.

---

## A2. Consulta realizada pelo Professor a partir da tela de disponibilidade

### A2.1
Durante a utilização de outra funcionalidade (por exemplo, consulta de disponibilidade F4.3), o Professor seleciona a opção **"Ver status de manutenção"** para um projetor listado.

### A2.2
O sistema já possui o identificador do projetor e salta diretamente para o passo P5, exibindo o status de manutenção e o resumo das ocorrências.

### A2.3
O Professor retorna à tela de origem após visualizar as informações.

---

# 6. Fluxos de Exceção

## E1. Projetor não localizado

### E1.1
No passo P4, o sistema não encontra projetor associado à tag ou ao patrimônio informado.

### E1.2
O sistema exibe a mensagem:

**ER001 – Projetor não localizado. Verifique a tag ou o patrimônio informado.**

### E1.3
O caso de uso é encerrado, ou o usuário retorna ao passo P2 para nova tentativa.

---

## E2. Falha ao consultar o banco de dados

### E2.1
No passo P5, ocorre erro de comunicação com o banco de dados ou indisponibilidade temporária.

### E2.2
O sistema exibe a mensagem:

**ER002 – Não foi possível recuperar o status de manutenção. Tente novamente mais tarde.**

### E2.3
O sistema registra log técnico para auditoria.

### E2.4
O caso de uso é encerrado.

---

# 7. Pós-condições

- O usuário obtém a **informação atualizada** sobre o status de manutenção do projetor consultado.
- Nenhum dado é alterado no sistema; trata-se de uma **operação apenas de leitura**.
- Eventuais erros de consulta ficam registrados em log para análise técnica.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Consulta de Status de Manutenção

| Campo / Elemento                       | Obrigatório | Formato                 | Regra de Validação                                              |
|----------------------------------------|------------|-------------------------|------------------------------------------------------------------|
| Tag NFC/RFID                           | Não        | Leitura automática      | Quando utilizada, deve estar vinculada a um projetor cadastrado  |
| Patrimônio                             | Não        | Texto / Código          | Quando utilizado, deve seguir o padrão de cadastro do sistema    |
| Botão "Ler Tag NFC/RFID"               | Não        | Ação                    | Dispara a leitura da tag no dispositivo compatível               |
| Botão "Buscar Projetor"                | Não        | Ação                    | Efetua a busca pelo patrimônio informado                         |
| Patrimônio (resultado)                 | Não        | Texto somente leitura   | Preenchido automaticamente a partir do cadastro                  |
| Modelo                                 | Não        | Texto somente leitura   | Preenchido automaticamente                                       |
| Status de manutenção atual             | Não        | Texto/Label             | Ex.: Disponível, Em manutenção, Aguardando manutenção            |
| Data de abertura da manutenção atual   | Não        | Data/Hora               | Exibida quando há manutenção ativa                               |
| Responsável pelo registro da manutenção| Não        | Texto                   | Exibido quando há manutenção ativa                               |
| Observações da manutenção atual        | Não        | Texto somente leitura   | Exibido quando houver                                            |
| Lista de manutenções recentes          | Não        | Tabela/Lista            | Opcional, mostra histórico resumido                              |

---

# 9. Frequência de Utilização

Alta.

A funcionalidade é utilizada com frequência por Professores e Atendentes para verificar rapidamente se um projetor está disponível para uso ou se encontra em manutenção, apoiando o planejamento de aulas e o atendimento no setor responsável.