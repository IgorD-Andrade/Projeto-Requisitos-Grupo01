# Caso de Uso – F4.2 Registrar Devolução de Projetor

## Histórico de Versões

| Data | Versão | Descrição | Autor |
|------|---------|------------|--------|
| 31/05/2026 | 1.0 | Criação do caso de uso Registrar Devolução de Projetor | João Pedro |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Registrar Devolução de Projetor

## 1.2 Objetivo

Permitir que o Atendente registre a devolução de um projetor, atualizando sua disponibilidade, localização e histórico de movimentações.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Atendente

## 2.2 Secundários

- Professor (responsável pela devolução)
- Tag NFC/RFID
- Sistema de Banco de Dados

---

# 3. Precondições

- O projetor deve estar registrado no sistema.
- O projetor deve possuir empréstimo ativo.
- O atendente deve possuir permissão para registrar devoluções.
- O sistema deve estar operacional.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O Atendente seleciona a opção "Registrar Devolução".

### P2.
O sistema solicita a identificação do projetor.

### P3.
O Atendente aproxima o dispositivo da tag NFC/RFID do projetor.

### P4.
O sistema identifica o projetor associado à tag.

### P5.
O sistema exibe os dados do empréstimo ativo:
- Patrimônio;
- Modelo;
- Professor responsável;
- Data e hora da retirada;
- Complementos entregues.

### P6.
O Atendente verifica o estado físico do projetor e dos complementos devolvidos.

### P7.
O Atendente informa:
- Condição do projetor;
- Condição dos complementos;
- Observações, se necessário.

### P8.
O Atendente confirma a devolução.

### P9.
O sistema valida as informações fornecidas.

### P10.
O sistema registra a devolução no histórico de movimentações.

### P11.
O sistema atualiza o status do projetor para "Disponível".

### P12.
O sistema atualiza a localização do projetor para o setor responsável.

### P13.
O sistema registra data e hora da devolução.

### P14.
O sistema exibe mensagem de sucesso.

---

# 5. Fluxos Alternativos

## A1. Devolução com itens faltando

### A1.1
No passo P6, o Atendente identifica ausência de um ou mais complementos.

### A1.2
O sistema solicita a identificação dos itens não devolvidos.

### A1.3
O Atendente informa os itens pendentes.

### A1.4
O sistema registra a ocorrência.

### A1.5
O sistema conclui a devolução do projetor e marca o empréstimo como "Devolvido com Pendências".

### A1.6
Segue para o passo P14.

---

## A2. Projetor devolvido com defeito

### A2.1
No passo P7, o Atendente informa que o equipamento apresenta defeito.

### A2.2
O sistema solicita descrição do problema.

### A2.3
O Atendente registra a ocorrência.

### A2.4
O sistema altera o status do projetor para "Em Manutenção".

### A2.5
O sistema registra a ocorrência no histórico.

### A2.6
Segue para o passo P14.

---

# 6. Fluxos de Exceção

## E1. Tag não reconhecida

### E1.1
No passo P4, o sistema não encontra projetor associado à tag lida.

### E1.2
O sistema exibe mensagem:

**ER001 – Tag não cadastrada no sistema.**

### E1.3
O caso de uso é encerrado.

---

## E2. Não existe empréstimo ativo

### E2.1
No passo P5, o sistema verifica que não existe empréstimo ativo para o projetor.

### E2.2
O sistema exibe mensagem:

**ER002 – Não existe empréstimo ativo para este projetor.**

### E2.3
O caso de uso é encerrado.

---

## E3. Falha ao registrar devolução

### E3.1
No passo P10, ocorre erro de comunicação com o banco de dados.

### E3.2
O sistema exibe mensagem:

**ER003 – Não foi possível concluir a devolução. Tente novamente.**

### E3.3
O sistema registra log técnico para auditoria.

### E3.4
O caso de uso é encerrado.

---

# 7. Pós-condições

- A devolução fica registrada no histórico do projetor.
- O status do projetor é atualizado.
- A localização do projetor é atualizada.
- A data e hora da devolução são armazenadas.
- Eventuais defeitos ou pendências ficam registrados para auditoria futura.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Registro de Devolução

| Campo | Obrigatório | Formato | Regra de Validação |
|---------|------------|----------|-------------------|
| Tag NFC/RFID | Sim | Leitura automática | Deve existir no cadastro de projetores |
| Patrimônio | Não | Texto | Preenchido automaticamente |
| Professor responsável | Não | Texto | Obtido do empréstimo ativo |
| Data da retirada | Não | Data/Hora | Obtida do empréstimo ativo |
| Estado do projetor | Sim | Lista | Disponível, Danificado, Em Manutenção |
| Complementos devolvidos | Sim | Lista de seleção | Deve permitir marcar itens recebidos |
| Observações | Não | Texto até 500 caracteres | Campo opcional |
| Data/Hora da devolução | Não | Data/Hora | Gerada automaticamente |

---

# 9. Frequência de Utilização

Alta.

A funcionalidade é utilizada sempre que um projetor retorna ao setor responsável após utilização em aulas, eventos ou atividades acadêmicas.
