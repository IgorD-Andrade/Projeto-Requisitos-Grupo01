# Caso de Uso – F4.1 Registrar Aluguel/Empréstimo

## Histórico de Versões

| Data       | Versão | Descrição                                           | Autor |
|-----------|--------|------------------------------------------------------|-------|
| 01/06/2026 | 1.0    | Criação do caso de uso Registrar Aluguel/Empréstimo | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Registrar Aluguel/Empréstimo de Projetor

## 1.2 Objetivo

Permitir que o Atendente registre o aluguel/empréstimo de um projetor para um Professor, definindo o período de uso, atualizando o status e a localização do projetor, e registrando a movimentação no histórico, com apoio de leitura de tag NFC/RFID para identificação do equipamento.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Atendente

## 2.2 Secundários

- Professor (solicitante que receberá o projetor)  
- Tag NFC/RFID  
- Sistema de Banco de Dados  
- Sistema (Controle de Permissões)

---

# 3. Precondições

- O projetor deve estar **cadastrado** e **ativo** no sistema.
- O projetor deve estar com status **"Disponível"** (sem empréstimo ativo).
- O Professor deve possuir cadastro ativo no sistema.
- O Atendente deve estar **autenticado** e possuir permissão para registrar empréstimos.
- O dispositivo utilizado deve estar habilitado para leitura da tag NFC/RFID (quando a identificação for feita por NFC).
- O sistema deve estar operacional e com acesso ao banco de dados.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O Atendente acessa o sistema GAC e seleciona a opção **"Registrar Aluguel/Empréstimo"**.

### P2.
O sistema apresenta uma tela solicitando:
- identificação do projetor (via leitura de tag NFC/RFID ou patrimônio);  
- identificação do Professor solicitante;  
- período previsto de uso (data/hora de início e término, quando aplicável).

### P3.
O Atendente identifica o projetor:
- aproximando o leitor da **tag NFC/RFID** do projetor; ou  
- informando o **patrimônio** do projetor.

### P4.
O sistema localiza o projetor no cadastro e verifica seu status atual.

### P5.
O sistema valida se:
- o projetor está **Disponível** (sem empréstimo ativo);  
- o projetor não está em manutenção ou aguardando manutenção.

### P6.
O Atendente informa ou seleciona o **Professor solicitante** (por exemplo, matrícula, CPF ou nome).

### P7.
O sistema valida se o Professor possui cadastro ativo e está apto a receber empréstimo.

### P8.
O Atendente informa os dados do empréstimo, tais como:
- data/hora de início (pode ser a data/hora atual);  
- data/hora de término prevista (quando houver política de prazo);  
- localização inicial de uso (sala/setor);  
- complementos entregues (cabos, controles, adaptadores).

### P9.
O Atendente confirma o registro do empréstimo.

### P10.
O sistema valida todas as informações fornecidas e verifica se, no intervalo informado, não há conflito com outro empréstimo para o mesmo projetor.

### P11.
O sistema registra o **empréstimo** no histórico de movimentações, incluindo:
- projetor;  
- Professor responsável;  
- Atendente que registrou;  
- datas e horários;  
- complementos;  
- local de uso.

### P12.
O sistema atualiza o status do projetor para **"Em uso"** e ajusta a localização (por exemplo, sala do Professor ou local de utilização).

### P13.
O sistema registra a data/hora do registro de empréstimo e o usuário responsável pela operação.

### P14.
O sistema exibe mensagem de sucesso, confirmando o empréstimo.

---

# 5. Fluxos Alternativos

## A1. Empréstimo sem definição de período de término

### A1.1
No passo P8, o Atendente não informa a data/hora de término.

### A1.2
O sistema considera o empréstimo como:
- **"Empréstimo em aberto"**, com término indefinido, ou  
- aplica uma regra padrão de prazo (conforme regra de negócio, se existir).

### A1.3
O fluxo continua a partir do passo P9.

---

## A2. Identificação do Professor via cartão/credencial

### A2.1
No passo P6, além da busca manual, o sistema permite leitura de um identificador (por exemplo, cartão institucional) para identificar o Professor.

### A2.2
O Atendente passa o cartão/credencial no leitor apropriado.

### A2.3
O sistema identifica automaticamente o Professor e preenche seus dados na tela.

### A2.4
O fluxo continua a partir do passo P8.

---

# 6. Fluxos de Exceção

## E1. Projetor não localizado

### E1.1
No passo P4, o sistema não encontra projetor associado à tag ou ao patrimônio informado.

### E1.2
O sistema exibe a mensagem:

**ER001 – Projetor não localizado. Verifique a tag ou o patrimônio informado.**

### E1.3
O Atendente pode tentar nova identificação (retornando ao passo P3) ou encerrar o caso de uso.

---

## E2. Projetor indisponível para empréstimo

### E2.1
No passo P5, o sistema identifica que o projetor:
- já possui **empréstimo ativo**, ou  
- está com status **"Em manutenção"** ou equivalente.

### E2.2
O sistema exibe a mensagem:

**ER002 – Projetor indisponível para empréstimo (em uso ou em manutenção).**

### E2.3
O caso de uso é encerrado, sem registrar empréstimo para aquele projetor.

---

## E3. Professor não localizado ou inativo

### E3.1
No passo P7, o sistema não encontra Professor com os dados fornecidos, ou encontra cadastro inativo.

### E3.2
O sistema exibe a mensagem:

**ER003 – Professor não localizado ou inativo. Verifique os dados informados.**

### E3.3
O caso de uso é encerrado, ou o Atendente retorna ao passo P6 para corrigir as informações.

---

## E4. Conflito de agendamento

*(Aplicável quando o sistema tratar agendamentos futuros.)*

### E4.1
No passo P10, o sistema identifica que já existe empréstimo/agendamento para o mesmo projetor que conflita com o período informado.

### E4.2
O sistema exibe a mensagem:

**ER004 – Já existe empréstimo/agendamento para este projetor no período informado.**

### E4.3
O Atendente deve ajustar o período (retornando ao passo P8) ou escolher outro projetor.

---

## E5. Falha ao registrar empréstimo

### E5.1
No passo P11, ocorre erro de comunicação com o banco de dados ou outra falha técnica.

### E5.2
O sistema exibe a mensagem:

**ER005 – Não foi possível concluir o registro do empréstimo. Tente novamente.**

### E5.3
O sistema registra log técnico para auditoria.

### E5.4
O caso de uso é encerrado sem criação de empréstimo.

---

# 7. Pós-condições

- Um **registro de empréstimo** é criado no histórico de movimentações, associando projetor, Professor responsável, período e Atendente.
- O status do projetor é atualizado para **"Em uso"**.
- A localização atual do projetor é atualizada para refletir o local de uso informado.
- A data e hora do registro, bem como o usuário responsável, ficam armazenadas para auditoria.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Registro de Aluguel/Empréstimo

| Campo / Elemento                 | Obrigatório | Formato                 | Regra de Validação                                                  |
|----------------------------------|------------|-------------------------|----------------------------------------------------------------------|
| Tag NFC/RFID                     | Não        | Leitura automática      | Quando utilizada, deve estar vinculada a um projetor cadastrado e disponível |
| Patrimônio do projetor          | Não        | Texto / Código          | Usado quando a tag não for lida; deve existir no cadastro           |
| Professor solicitante           | Sim        | Seleção/Texto           | Deve corresponder a usuário válido e ativo                          |
| Data/Hora de início             | Sim        | Data/Hora               | Pode ser preenchida automaticamente com a data/hora atual           |
| Data/Hora de término prevista   | Não        | Data/Hora               | Quando informada, deve ser posterior à data/hora de início          |
| Local de uso (sala/setor)       | Não        | Texto/Seleção           | Opcional; quando informado, deve seguir padrão da instituição       |
| Complementos entregues          | Não        | Lista de seleção        | Ex.: cabo HDMI, controle remoto, adaptador                          |
| Observações                     | Não        | Texto até 500 caracteres| Campo opcional                                                       |
| Botão "Confirmar Empréstimo"    | Sim        | Ação                    | Dispara validações e registra o empréstimo                          |

---

# 9. Frequência de Utilização

Alta.

A funcionalidade é utilizada sempre que um projetor é retirado para uso em aulas, eventos ou atividades acadêmicas, sendo uma das operações centrais do fluxo de empréstimos do sistema GAC.
