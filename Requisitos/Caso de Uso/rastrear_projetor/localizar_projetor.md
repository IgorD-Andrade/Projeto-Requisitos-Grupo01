# Caso de Uso – F2.1 Localizar Projetor

## Histórico de Versões

| Data       | Versão | Descrição                               | Autor |
|-----------|--------|------------------------------------------|-------|
| 31/05/2026 | 1.0    | Criação do caso de uso Localizar Projetor | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Localizar Projetor

## 1.2 Objetivo

Permitir que o usuário identifique rapidamente **onde um projetor se encontra** (local/sala ou setor) e, quando aplicável, **quem é o responsável atual**, utilizando busca por identificadores ou leitura da tag NFC/RFID.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Atendente

## 2.2 Secundários

- Professor (quando realiza consultas de localização via interface própria)
- Tag NFC/RFID
- Sistema de Banco de Dados

---

# 3. Precondições

- O projetor deve estar **cadastrado** no sistema.
- O sistema deve estar operacional e com acesso ao banco de dados.
- Quando a consulta for feita via NFC, o dispositivo deve estar habilitado para leitura da tag.
- O usuário (Atendente ou Professor) deve estar autenticado, quando a política de acesso exigir login.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O usuário acessa o sistema GAC e seleciona a opção **"Localizar Projetor"**.

### P2.
O sistema apresenta uma tela de busca permitindo identificar o projetor por:
- leitura de **tag NFC/RFID**; ou  
- **patrimônio**; ou  
- outro identificador cadastrado (por exemplo, código interno).

### P3.
O usuário escolhe o método de identificação:

- Se optar por **leitura de tag**, aproxima o dispositivo do projetor para ler a tag NFC/RFID; ou  
- Se optar por **patrimônio/código**, informa o valor no campo correspondente.

### P4.
O sistema localiza o projetor no cadastro, a partir da tag ou do identificador informado.

### P5.
O sistema consulta o banco de dados para obter:
- localização atual registrada (sala/setor ou setor responsável);  
- situação de uso (Disponível, Em uso, Em manutenção);  
- se houver empréstimo ativo, o Professor responsável.

### P6.
O sistema exibe na tela as informações de localização e situação do projetor, incluindo:

- Patrimônio e modelo;  
- Localização atual (sala/setor ou “Setor de atendimento”);  
- Status (Disponível, Em uso, Em manutenção, etc.);  
- Professor responsável atual (quando houver empréstimo ativo);  
- Data/hora da última movimentação registrada.

### P7.
Opcionalmente, o usuário pode solicitar a visualização do **histórico de movimentações** (acessando F2.2 – Consultar histórico de movimentação).

### P8.
O usuário visualiza as informações e encerra a consulta ou realiza nova busca.

---

# 5. Fluxos Alternativos

## A1. Localização por filtros de contexto (sem identificador direto)

### A1.1
No passo P2, além da identificação direta, o sistema oferece filtros como:
- Local/sala;  
- Status (por exemplo, Em uso, Disponível, Em manutenção).

### A1.2
O usuário informa um ou mais filtros, por exemplo:
- “Listar projetores atualmente **Em uso**”; ou  
- “Listar projetores na **Sala X**”.

### A1.3
O sistema lista todos os projetores que atendem aos filtros, com:
- patrimônio;  
- modelo;  
- localização;  
- status.

### A1.4
O usuário seleciona um projetor da lista para ver o detalhe de localização.

### A1.5
O fluxo continua a partir do passo P5.

---

## A2. Acesso pelo Professor a partir de outra funcionalidade

### A2.1
Durante o uso de outra funcionalidade (por exemplo, **Consultar Disponibilidade F4.3**), o Professor seleciona a opção **"Ver localização"** para um projetor listado.

### A2.2
O sistema já possui o identificador do projetor selecionado e salta diretamente para o passo P5.

### A2.3
O Professor visualiza a localização e retorna à tela de origem.

---

# 6. Fluxos de Exceção

## E1. Projetor não localizado

### E1.1
No passo P4, o sistema não encontra projetor associado à tag ou ao identificador informado.

### E1.2
O sistema exibe a mensagem:

**ER001 – Projetor não localizado. Verifique a tag ou o identificador informado.**

### E1.3
O usuário pode:
- tentar nova busca (retornando ao passo P2); ou  
- encerrar o caso de uso.

---

## E2. Falha ao consultar o banco de dados

### E2.1
No passo P5, ocorre erro de comunicação com o banco de dados ou indisponibilidade temporária.

### E2.2
O sistema exibe a mensagem:

**ER002 – Não foi possível recuperar a localização do projetor. Tente novamente mais tarde.**

### E2.3
O sistema registra log técnico para auditoria.

### E2.4
O caso de uso é encerrado.

---

# 7. Pós-condições

- O usuário obtém a **localização atual** e o **status** do projetor consultado.
- Nenhum dado de empréstimo, devolução ou cadastro é alterado: trata-se de uma operação de **consulta**.
- Consultas com erro ou falha de acesso ficam registradas em log para suporte técnico.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Localização de Projetor

| Campo / Elemento                       | Obrigatório | Formato                 | Regra de Validação                                              |
|----------------------------------------|------------|-------------------------|------------------------------------------------------------------|
| Tag NFC/RFID                           | Não        | Leitura automática      | Quando utilizada, deve estar vinculada a um projetor cadastrado  |
| Patrimônio / Identificador             | Não        | Texto / Código          | Quando utilizado, deve seguir o padrão de cadastro do sistema    |
| Botão "Ler Tag NFC/RFID"               | Não        | Ação                    | Dispara a leitura da tag no dispositivo compatível               |
| Botão "Buscar"                         | Não        | Ação                    | Efetua a busca pelo identificador informado                      |
| Filtro por local/sala                  | Não        | Seleção/Texto          | Opcional, para listar projetores por localização                 |
| Filtro por status                      | Não        | Seleção                 | Ex.: Disponível, Em uso, Em manutenção                           |
| Patrimônio (resultado)                 | Não        | Texto somente leitura   | Preenchido automaticamente a partir do cadastro                  |
| Modelo                                 | Não        | Texto somente leitura   | Preenchido automaticamente                                       |
| Localização atual                      | Não        | Texto                   | Ex.: Sala 101, Setor de Atendimento, Manutenção, etc.            |
| Status atual                           | Não        | Texto/Label             | Ex.: Disponível, Em uso, Em manutenção                           |
| Professor responsável atual            | Não        | Texto                   | Exibido quando houver empréstimo ativo                           |
| Data/Hora da última movimentação       | Não        | Data/Hora               | Preenchida a partir do histórico de movimentações                |
| Link/Botão "Ver histórico"             | Não        | Ação                    | Abre a tela/relatório de histórico de movimentações (F2.2)       |

---

# 9. Frequência de Utilização

Alta.

A funcionalidade é utilizada com frequência por Atendentes e, em alguns cenários, por Professores, para localizar rapidamente onde está um projetor e quem é o responsável atual, apoiando o atendimento e o planejamento de uso em aulas e eventos.
