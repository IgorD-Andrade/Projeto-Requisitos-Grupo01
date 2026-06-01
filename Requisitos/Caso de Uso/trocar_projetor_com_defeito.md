# Caso de Uso – F6.1 Trocar Projetor com Defeito

## Histórico de Versões

| Data       | Versão | Descrição                                    | Autor |
|-----------|--------|-----------------------------------------------|-------|
| 31/05/2026 | 1.0    | Criação do caso de uso Trocar Projetor com Defeito | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Trocar Projetor com Defeito

## 1.2 Objetivo

Permitir que o Atendente substitua um projetor que apresentou defeito por outro projetor disponível, garantindo que o equipamento defeituoso seja encaminhado para manutenção, que o novo projetor seja corretamente associado ao Professor responsável e que todas as movimentações sejam registradas no histórico.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Atendente

## 2.2 Secundários

- Professor (em posse do projetor com defeito)
- Técnico (posteriormente, responsável pela manutenção)
- Tag NFC/RFID
- Sistema de Banco de Dados
- Sistema (Controle de Permissões)

---

# 3. Precondições

- O projetor defeituoso deve estar **cadastrado** e possuir **empréstimo ativo** no sistema.
- O Professor responsável pelo projetor deve estar corretamente associado ao empréstimo ativo.
- Deve existir pelo menos um **projetor disponível** para substituição.
- O Atendente deve estar **autenticado** e possuir permissão para registrar trocas.
- O dispositivo utilizado deve estar habilitado para leitura de tags NFC/RFID.
- O sistema deve estar operacional e com acesso ao banco de dados.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O Atendente acessa o sistema GAC e seleciona a opção **"Trocar Projetor com Defeito"**.

### P2.
O sistema solicita a identificação do **projetor com defeito**:
- via leitura de **tag NFC/RFID**; ou  
- via **patrimônio**.

### P3.
O Atendente identifica o projetor defeituoso:
- aproximando o leitor da tag NFC/RFID; ou  
- informando o patrimônio do projetor.

### P4.
O sistema localiza o projetor no cadastro, verifica o **empréstimo ativo** e exibe:
- patrimônio e modelo;
- Professor responsável;
- data/hora do empréstimo;
- local de uso.

### P5.
O Atendente confirma que aquele é o projetor defeituoso e informa o **motivo da troca** (resumo do problema).

### P6.
O sistema verifica se o projetor:
- possui empréstimo ativo;  
- não está marcado como já devolvido ou já em manutenção.

### P7.
O sistema orienta o Atendente a selecionar um **projetor substituto**:
- por leitura de tag NFC/RFID; ou  
- por seleção de um projetor **Disponível** na lista.

### P8.
O Atendente identifica o projetor substituto (tag ou patrimônio).

### P9.
O sistema valida se o projetor substituto:
- está cadastrado e ativo;  
- está com status **"Disponível"** (sem empréstimo ativo e não em manutenção).

### P10.
O sistema apresenta um **resumo da troca**, incluindo:
- projetor defeituoso (patrimônio, modelo);  
- projetor substituto;  
- Professor responsável;  
- local de uso;  
- motivo da troca.

### P11.
O Atendente confirma a operação de troca.

### P12.
O sistema encerra o **empréstimo ativo** do projetor defeituoso, registrando que foi interrompido por defeito.

### P13.
O sistema cria um **novo empréstimo** para o projetor substituto, mantendo:
- o mesmo Professor responsável;  
- o mesmo período remanescente (quando aplicável);  
- o mesmo local de uso.

### P14.
O sistema altera o status do projetor defeituoso para **"Em manutenção"** (ou “Aguardando manutenção”) e registra uma ocorrência de manutenção vinculada (incluindo o motivo informado).

### P15.
O sistema atualiza o status do projetor substituto para **"Em uso"**.

### P16.
O sistema registra todas as movimentações no histórico (devolução antecipada por defeito, abertura de manutenção, novo empréstimo).

### P17.
O sistema exibe mensagem de sucesso, confirmando a troca.

---

# 5. Fluxos Alternativos

## A1. Escolha do projetor substituto a partir de lista de disponíveis

### A1.1
No passo P7, em vez de leitura por tag, o Atendente opta por **selecionar** o projetor substituto em uma lista de projetores disponíveis.

### A1.2
O sistema apresenta lista filtrada de projetores com status **"Disponível"**, permitindo:
- filtro por localização, modelo ou outro critério.

### A1.3
O Atendente seleciona um projetor da lista.

### A1.4
O fluxo continua a partir do passo P9.

---

## A2. Registro de manutenção mais detalhado por Técnico

### A2.1
Após o passo P14, o sistema registra uma manutenção básica (aberta automaticamente) para o projetor defeituoso.

### A2.2
Em momento posterior, o Técnico acessa a funcionalidade **Registrar manutenção (F3.1)** para complementar os detalhes (tipo de manutenção, peças trocadas, solução aplicada).

### A2.3
Essa ação é tratada no caso de uso F3.1 e não altera o fluxo principal da troca.

---

# 6. Fluxos de Exceção

## E1. Projetor defeituoso não localizado

### E1.1
No passo P4, o sistema não encontra projetor associado à tag ou ao patrimônio informado.

### E1.2
O sistema exibe a mensagem:

**ER001 – Projetor não localizado. Verifique a tag ou o patrimônio informado.**

### E1.3
O caso de uso é encerrado, ou o Atendente retorna ao passo P3 para nova tentativa.

---

## E2. Projetor sem empréstimo ativo

### E2.1
No passo P6, o sistema verifica que **não existe empréstimo ativo** para o projetor identificado.

### E2.2
O sistema exibe a mensagem:

**ER002 – Não existe empréstimo ativo para este projetor. Troca não permitida.**

### E2.3
O caso de uso é encerrado.

---

## E3. Nenhum projetor substituto disponível

### E3.1
No passo P9, o sistema identifica que:
- não há projetores com status **"Disponível"** que atendam ao critério; ou  
- o projetor selecionado já foi emprestado nesse meio tempo.

### E3.2
O sistema exibe a mensagem:

**ER003 – Não há projetores disponíveis para substituição no momento.**

### E3.3
O Atendente pode:
- tentar selecionar outro projetor (voltando ao passo P7); ou  
- encerrar a tentativa de troca.

---

## E4. Falha ao registrar a troca

### E4.1
Entre os passos P12 e P16, ocorre erro de comunicação com o banco de dados ou falha técnica.

### E4.2
O sistema exibe a mensagem:

**ER004 – Não foi possível concluir a troca do projetor. Tente novamente.**

### E4.3
O sistema registra log técnico para auditoria.

### E4.4
O caso de uso é encerrado **sem alterar** os empréstimos e os status atuais dos projetores.

---

# 7. Pós-condições

- O projetor defeituoso passa a ter status **"Em manutenção"** (ou equivalente) e possui um registro de manutenção associado.
- O empréstimo anterior é encerrado, indicando que foi interrompido por defeito.
- Um novo empréstimo é criado para o projetor substituto, mantendo o Professor responsável.
- O projetor substituto passa a ter status **"Em uso"**.
- Todas as movimentações (devolução por defeito, abertura de manutenção, novo empréstimo) ficam registradas no **histórico de movimentações** para auditoria.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Troca de Projetor com Defeito

| Campo / Elemento                      | Obrigatório | Formato                 | Regra de Validação                                                  |
|---------------------------------------|------------|-------------------------|----------------------------------------------------------------------|
| Tag / Patrimônio do projetor defeituoso | Sim     | Leitura NFC ou Texto    | Deve estar cadastrado e possuir empréstimo ativo                     |
| Professor responsável (exibição)      | Não        | Texto somente leitura   | Obtido do empréstimo ativo                                           |
| Local de uso                          | Não        | Texto somente leitura   | Obtido do empréstimo ativo                                           |
| Motivo da troca (descrição do defeito)| Sim        | Texto até 500 caracteres| Deve ser preenchido com breve descrição do problema                  |
| Projetor substituto (tag/patrimônio)  | Sim        | Leitura NFC ou Seleção  | Deve estar cadastrado, ativo e com status "Disponível"               |
| Resumo da troca                       | Não        | Área de texto/resumo    | Exibe projetor antigo, projetor novo, Professor e local              |
| Botão "Confirmar Troca"              | Sim        | Ação                    | Dispara as validações e registra a troca                             |

---

# 9. Frequência de Utilização

Média.

A funcionalidade será utilizada em situações em que um projetor apresenta defeito durante o uso e precisa ser substituído rapidamente para não prejudicar aulas ou eventos, garantindo rastreabilidade e histórico adequado tanto do projetor defeituoso quanto do projetor substituto.
