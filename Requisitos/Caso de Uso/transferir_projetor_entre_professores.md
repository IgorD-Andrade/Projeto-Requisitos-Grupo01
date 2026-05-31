# Caso de Uso – F5.1 Transferir Projetor entre Professores

## Histórico de Versões

| Data       | Versão | Descrição                                           | Autor      |
|-----------|--------|-----------------------------------------------------|-----------|
| 31/05/2026 | 1.0    | Criação do caso de uso Transferir Projetor entre Professores | Igor |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Transferir Projetor entre Professores

## 1.2 Objetivo

Permitir que um Professor transfira a posse de um projetor para outro Professor, registrando essa transferência no sistema GAC, atualizando o responsável, a situação de empréstimo e o histórico de movimentações, mediante confirmação via leitura de tag NFC/RFID.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Professor (Professor que está transferindo a posse do projetor)

## 2.2 Secundários

- Professor Destinatário (Professor que receberá a posse do projetor)
- Tag NFC/RFID
- Sistema de Banco de Dados
- Sistema (Controle de Permissões)

---

# 3. Precondições

- O projetor deve estar **cadastrado** e **ativo** no sistema.
- O projetor deve possuir um **empréstimo ativo** vinculado ao Professor que está realizando a transferência.
- O Professor deve estar **autenticado** no sistema GAC e possuir permissão para efetuar a transferência.
- O Professor Destinatário deve possuir cadastro ativo no sistema.
- O dispositivo utilizado deve estar habilitado para leitura da tag NFC/RFID.
- O sistema deve estar operacional e com acesso ao banco de dados.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O Professor acessa o sistema GAC, estando autenticado, e seleciona a opção **"Transferir Projetor entre Professores"**.

### P2.
O sistema exibe uma tela solicitando:
- Identificação do projetor (via leitura de tag NFC/RFID);
- Identificação do **Professor Destinatário** (por exemplo, matrícula, CPF ou seleção em lista).

### P3.
O Professor aproxima o dispositivo leitor da **tag NFC/RFID** do projetor.

### P4.
O sistema lê a tag, identifica o projetor associado e busca os dados do **empréstimo ativo**.

### P5.
O sistema valida se:
- existe empréstimo ativo para aquele projetor; e
- o empréstimo está vinculado ao Professor que está logado.

### P6.
O sistema exibe um resumo das informações:
- Patrimônio e modelo do projetor;
- Professor atual responsável (Professor de Origem);
- Professor Destinatário informado;
- Data e hora do empréstimo atual;
- Localização atual registrada.

### P7.
O Professor confirma a identidade do Professor Destinatário (por conferência visual dos dados exibidos).

### P8.
Opcionalmente, o Professor Destinatário se autentica no sistema (por exemplo, informando usuário e senha) para confirmar que aceita a transferência.

### P9.
O Professor clica em **"Confirmar Transferência"**.

### P10.
O sistema valida as informações fornecidas e verifica:
- se o Professor Destinatário é um usuário válido e ativo;
- se o projetor ainda está com empréstimo ativo e não foi devolvido ou transferido por outro processo.

### P11.
O sistema registra a transferência no **histórico de movimentações**, encerrando o empréstimo anterior e criando um novo registro de empréstimo vinculado ao Professor Destinatário, mantendo o status do projetor como **"Em uso"**.

### P12.
O sistema atualiza o **responsável atual** pelo projetor para o Professor Destinatário e, se aplicável, a localização associada.

### P13.
O sistema registra data e hora da transferência, bem como os usuários envolvidos (Professor de Origem e Professor Destinatário).

### P14.
O sistema exibe mensagem de sucesso informando que a transferência foi concluída.

---

# 5. Fluxos Alternativos

## A1. Professor Destinatário não informado inicialmente

### A1.1
No passo P2, o Professor deixa o campo do Professor Destinatário em branco.

### A1.2
O sistema não permite prosseguir e exibe mensagem solicitando a seleção ou identificação do Professor Destinatário.

### A1.3
O cenário retorna ao passo P2 para preenchimento das informações.

---

## A2. Confirmação apenas pelo Professor de Origem

*(Caso a autenticação do Professor Destinatário não seja obrigatória na primeira versão do sistema.)*

### A2.1
No passo P8, a autenticação do Professor Destinatário é opcional.

### A2.2
O Professor de Origem decide prosseguir sem autenticação do Destinatário.

### A2.3
O sistema registra no histórico que a transferência foi confirmada apenas pelo Professor de Origem.

### A2.4
O fluxo continua a partir do passo P10.

---

# 6. Fluxos de Exceção

## E1. Tag não reconhecida

### E1.1
No passo P4, o sistema não encontra projetor associado à tag lida.

### E1.2
O sistema exibe a mensagem:

**ER001 – Tag não cadastrada no sistema.**

### E1.3
O caso de uso é encerrado.

---

## E2. Projetor sem empréstimo ativo

### E2.1
No passo P5, o sistema verifica que **não existe empréstimo ativo** para o projetor identificado.

### E2.2
O sistema exibe a mensagem:

**ER002 – Não existe empréstimo ativo para este projetor.**

### E2.3
O caso de uso é encerrado.

---

## E3. Projetor não pertence ao Professor logado

### E3.1
No passo P5, o sistema identifica que o empréstimo ativo do projetor está vinculado a outro usuário que não o Professor autenticado.

### E3.2
O sistema exibe a mensagem:

**ER003 – Você não é o responsável atual por este projetor. Transferência não permitida.**

### E3.3
O caso de uso é encerrado.

---

## E4. Professor Destinatário inválido ou inativo

### E4.1
No passo P10, o sistema verifica que o Professor Destinatário não existe ou está inativo no cadastro.

### E4.2
O sistema exibe a mensagem:

**ER004 – Professor destinatário inválido ou inativo. Verifique os dados informados.**

### E4.3
O caso de uso é encerrado, sem realizar transferência.

---

## E5. Falha ao registrar transferência

### E5.1
No passo P11, ocorre erro de comunicação com o banco de dados ou falha técnica.

### E5.2
O sistema exibe a mensagem:

**ER005 – Não foi possível concluir a transferência. Tente novamente.**

### E5.3
O sistema registra log técnico para auditoria.

### E5.4
O caso de uso é encerrado sem modificar o responsável pelo projetor.

---

# 7. Pós-condições

- A transferência de posse do projetor entre professores fica registrada no **histórico de movimentações**.
- O **responsável atual** pelo projetor passa a ser o Professor Destinatário.
- O status do projetor permanece **"Em uso"**, agora vinculado ao novo responsável.
- A data e hora da transferência, bem como os identificadores dos professores envolvidos, são armazenados para auditoria.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Transferência de Projetor entre Professores

| Campo                          | Obrigatório | Formato          | Regra de Validação                                                   |
|--------------------------------|------------|------------------|-----------------------------------------------------------------------|
| Tag NFC/RFID                   | Sim        | Leitura automática | Deve existir no cadastro de projetores e ter empréstimo ativo        |
| Patrimônio                     | Não        | Texto            | Preenchido automaticamente a partir da tag                            |
| Modelo do projetor             | Não        | Texto            | Preenchido automaticamente                                            |
| Professor de Origem            | Não        | Texto            | Obtido do empréstimo ativo                                            |
| Professor Destinatário         | Sim        | Seleção/Texto    | Deve corresponder a usuário válido e ativo no sistema                 |
| Localização atual              | Não        | Texto            | Preenchido automaticamente, podendo ser exibido apenas para consulta  |
| Observações sobre a transferência | Não     | Texto até 500 caracteres | Campo opcional                                                        |
| Data/Hora da transferência     | Não        | Data/Hora        | Gerada automaticamente pelo sistema                                   |

---

# 9. Frequência de Utilização

Média.

A funcionalidade será utilizada principalmente em situações em que um Professor já está em posse do projetor e, por conveniência ou continuidade de atividades, transfere o equipamento diretamente para outro Professor, sem devolvê-lo primeiro ao setor de atendimento.