# Caso de Uso – F1.2 Atualizar Dados de Projetor

## Histórico de Versões

| Data       | Versão | Descrição                                     | Autor |
|-----------|--------|-----------------------------------------------|-------|
| 31/05/2026 | 1.0    | Criação do caso de uso Atualizar Dados de Projetor | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Atualizar Dados de Projetor

## 1.2 Objetivo

Permitir que o Administrador altere informações cadastrais de um projetor (como modelo, localização, status cadastral, tag NFC/RFID associada e outros atributos), mantendo o registro atualizado e consistente no sistema GAC.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Administrador

## 2.2 Secundários

- Sistema de Banco de Dados  
- Tag NFC/RFID (quando utilizada para localizar o projetor)

---

# 3. Precondições

- O projetor deve estar **cadastrado** no sistema.
- O Administrador deve estar **autenticado** e possuir permissão para alterar cadastros.
- O sistema deve estar operacional e com acesso ao banco de dados.
- Quando a identificação for via NFC, o dispositivo deve estar habilitado para leitura da tag.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O Administrador acessa o sistema GAC e seleciona a opção **"Atualizar Dados de Projetor"**.

### P2.
O sistema apresenta uma tela para identificar o projetor, permitindo:
- leitura da **tag NFC/RFID**; ou  
- busca por **patrimônio**; ou  
- outro identificador cadastrado (por exemplo, código interno).

### P3.
O Administrador identifica o projetor:
- aproximando o leitor da tag NFC/RFID; ou  
- digitando o patrimônio/identificador e clicando em **"Buscar"**.

### P4.
O sistema localiza o projetor no cadastro e exibe os **dados atuais**, tais como:
- patrimônio;  
- modelo;  
- fabricante (se houver);  
- localização atual registrada;  
- status cadastral (ativo/inativo);  
- identificação/tag NFC/RFID associada;  
- observações.

### P5.
O Administrador altera os campos necessários, por exemplo:
- atualização de modelo ou informações complementares;  
- ajuste de localização padrão do projetor;  
- correção de dados de patrimônio (quando permitido);  
- substituição/atualização da tag NFC/RFID associada;  
- atualização de observações cadastrais.

### P6.
O sistema realiza validações de consistência, como:
- unicidade do patrimônio;  
- unicidade da tag NFC/RFID (uma tag não pode estar associada a mais de um projetor);  
- obrigatoriedade de campos principais.

### P7.
Estando os dados válidos, o Administrador confirma a atualização.

### P8.
O sistema grava as alterações no banco de dados, mantendo o histórico de modificações (quando aplicável).

### P9.
O sistema exibe mensagem de sucesso, confirmando que os dados do projetor foram atualizados.

---

# 5. Fluxos Alternativos

## A1. Atualização apenas de localização

### A1.1
No passo P5, o Administrador altera apenas a **localização padrão** do projetor (por exemplo, mudança definitiva de sala/setor).

### A1.2
O sistema destaca que essa alteração se refere à localização cadastral (não confundir com movimentações temporárias de empréstimo).

### A1.3
O fluxo segue normalmente a partir do passo P6, registrando a nova localização padrão do projetor.

---

## A2. Atualização apenas da tag NFC/RFID

### A2.1
No passo P5, o Administrador seleciona a opção de **substituir tag NFC/RFID** (por exemplo, em caso de tag danificada).

### A2.2
O sistema solicita que o Administrador faça a leitura da **nova tag**.

### A2.3
O sistema verifica se a nova tag já está associada a outro projetor.

### A2.4
Não havendo conflito, o sistema associa a nova tag ao projetor e, opcionalmente, registra em histórico qual tag foi substituída.

### A2.5
O fluxo segue a partir do passo P7.

---

# 6. Fluxos de Exceção

## E1. Projetor não localizado

### E1.1
No passo P4, o sistema não encontra projetor associado à tag ou ao identificador informado.

### E1.2
O sistema exibe a mensagem:

**ER001 – Projetor não localizado. Verifique a tag ou o identificador informado.**

### E1.3
O Administrador pode tentar nova busca (retornando ao passo P3) ou encerrar o caso de uso.

---

## E2. Patrimônio já existente

### E2.1
No passo P6, o sistema identifica que o **novo patrimônio** informado já está cadastrado para outro projetor.

### E2.2
O sistema exibe a mensagem:

**ER002 – Patrimônio informado já está em uso por outro projetor.**

### E2.3
O Administrador deve corrigir o valor (voltando ao passo P5) ou desistir da atualização.

---

## E3. Tag NFC/RFID já associada a outro projetor

### E3.1
No passo A2.3 ou P6, o sistema detecta que a tag NFC/RFID informada já está vinculada a outro projetor.

### E3.2
O sistema exibe a mensagem:

**ER003 – Tag NFC/RFID já associada a outro projetor. Selecione outra tag.**

### E3.3
O Administrador deve informar outra tag (retornando ao passo A2.2 ou P5) ou cancelar a atualização da tag.

---

## E4. Falha ao atualizar dados

### E4.1
No passo P8, ocorre erro de comunicação com o banco de dados ou outra falha técnica.

### E4.2
O sistema exibe a mensagem:

**ER004 – Não foi possível salvar as alterações. Tente novamente.**

### E4.3
O sistema registra log técnico para auditoria.

### E4.4
O caso de uso é encerrado sem alterar os dados cadastrados do projetor.

---

# 7. Pós-condições

- Os dados cadastrais do projetor ficam **atualizados** no sistema, refletindo as alterações realizadas pelo Administrador.
- Quando houver mudança de tag, a nova tag NFC/RFID passa a estar corretamente associada ao projetor.
- As alterações podem ficar registradas em **histórico de modificações**, permitindo auditoria futura (conforme regras de negócio).

---

# 8. Interface Visual (IV1)

## IV1. Tela de Atualização de Dados de Projetor

| Campo / Elemento               | Obrigatório | Formato                 | Regra de Validação                                              |
|--------------------------------|------------|-------------------------|------------------------------------------------------------------|
| Tag NFC/RFID (identificação)   | Não        | Leitura automática      | Quando usada, deve estar vinculada a um projetor cadastrado      |
| Patrimônio (busca)             | Não        | Texto / Código          | Usado para localizar o projetor quando a tag não é utilizada     |
| Botão "Buscar"                 | Não        | Ação                    | Carrega dados do projetor selecionado                            |
| Patrimônio (edição)           | Sim*       | Texto / Código          | Pode ser editável ou somente leitura, conforme regra de negócio  |
| Modelo                         | Sim        | Texto                   | Não pode ser vazio                                              |
| Fabricante / Marca             | Não        | Texto                   | Opcional                                                         |
| Localização padrão (sala/setor)| Sim        | Seleção/Texto           | Deve seguir padrão de cadastro da instituição                    |
| Status cadastral (Ativo/Inativo)| Sim       | Seleção                 | Define se o projetor pode ser utilizado em operações de empréstimo |
| Tag NFC/RFID associada         | Não        | Leitura automática/Texto| Quando alterada, não pode estar associada a outro projetor       |
| Observações                    | Não        | Texto até 500 caracteres| Campo opcional                                                   |
| Botão "Salvar" / "Atualizar"   | Sim        | Ação                    | Dispara validações e grava as alterações                         |

\* Conforme decisão de regra de negócio, o campo Patrimônio pode ser apenas leitura (somente em casos especiais de correção) ou não editável na maioria dos cenários.

---

# 9. Frequência de Utilização

Média.

A funcionalidade será utilizada sempre que houver necessidade de corrigir, completar ou ajustar dados de um projetor já cadastrado (por exemplo, mudança definitiva de sala, atualização de modelo, substituição de tag NFC/RFID ou alterações cadastrais identificadas em auditorias).
