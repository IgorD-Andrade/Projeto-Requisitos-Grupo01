# Caso de Uso – F7.1 Autenticação de Usuários

## Histórico de Versões

| Data       | Versão | Descrição                                | Autor |
|-----------|--------|-------------------------------------------|-------|
| 31/05/2026 | 1.0    | Criação do caso de uso Autenticação de Usuários | Igor  |

---

# 1. Identificação do Caso de Uso

## 1.1 Nome

Autenticação de Usuários

## 1.2 Objetivo

Garantir que apenas usuários autorizados (Professores, Atendentes e Administradores) acessem o sistema GAC, validando credenciais e estabelecendo a sessão do usuário com seu respectivo perfil de acesso.

## 1.3 Tipo

Concreto.

---

# 2. Atores

## 2.1 Primário

- Usuário do Sistema  
  (Professor, Atendente ou Administrador de Inventário)

## 2.2 Secundários

- Serviço de Autenticação Externa  
- Sistema de Banco de Dados  
- Sistema (Controle de Permissões)

---

# 3. Precondições

- O usuário deve estar previamente **cadastrado** e **ativo** no sistema GAC (ou no diretório/autenticador externo utilizado).
- O sistema GAC deve estar operacional, com acesso ao serviço de autenticação e ao banco de dados.
- A página de login deve estar acessível via navegador.

---

# 4. Fluxo Principal (Cenário de Sucesso)

### P1.
O usuário acessa a URL do sistema GAC e é direcionado para a **tela de login**.

### P2.
O sistema exibe os campos para **usuário** (login) e **senha** e, opcionalmente, seleção de perfil ou unidade (se aplicável).

### P3.
O usuário informa suas credenciais:
- identificador de usuário (por exemplo, matrícula institucional, e-mail ou login);  
- senha de acesso.

### P4.
O usuário aciona o comando **"Entrar"** (ou equivalente).

### P5.
O sistema valida, localmente, o preenchimento mínimo (campos obrigatórios) e, em seguida, envia as credenciais ao **Serviço de Autenticação**.

### P6.
O Serviço de Autenticação verifica:
- se o usuário existe;  
- se a senha informada está correta;  
- se o usuário está ativo e autorizado a acessar o sistema.

### P7.
Em caso de sucesso, o Serviço de Autenticação retorna ao GAC:
- identificação única do usuário;  
- perfis ou papéis associados (Professor, Atendente, Administrador, etc.);  
- informações adicionais, se necessárias (nome, e-mail).

### P8.
O sistema GAC cria uma **sessão autenticada** para o usuário, registra o horário de login e associa o perfil retornado às permissões internas (F7.2 – Controle de permissões).

### P9.
O sistema redireciona o usuário para a **página inicial** adequada ao seu perfil, por exemplo:
- painel do Professor;  
- painel do Atendente;  
- painel administrativo.

### P10.
O usuário passa a ter acesso às funcionalidades autorizadas, conforme seu perfil.

---

# 5. Fluxos Alternativos

## A1. Usuário já autenticado acessa novamente

### A1.1
O usuário acessa a URL do sistema e já possui sessão ativa válida (por exemplo, cookie ou token ainda não expirado).

### A1.2
O sistema reconhece a sessão ativa e redireciona o usuário diretamente para a página inicial correspondente ao seu perfil, **sem solicitar novo login**.

### A1.3
O fluxo prossegue como no passo P10.

---

## A2. Lembrar usuário (quando permitido)

### A2.1
Na tela de login (passo P2), o sistema oferece a opção **"Lembrar meu usuário"**.

### A2.2
O usuário marca essa opção antes de efetuar o login.

### A2.3
Após autenticação bem-sucedida (passo P9), o sistema registra em armazenamento local seguro (por exemplo, cookie) apenas o identificador do usuário, para facilitar preenchimento futuro.

### A2.4
Em um próximo acesso, o campo de usuário é preenchido automaticamente, restando ao usuário informar apenas a senha.

---

# 6. Fluxos de Exceção

## E1. Credenciais inválidas

### E1.1
No passo P6, o Serviço de Autenticação identifica que:
- o usuário não existe; ou  
- a senha está incorreta; ou  
- o usuário está inativo ou bloqueado.

### E1.2
O sistema GAC recebe a resposta de falha e exibe mensagem:

**ER001 – Usuário ou senha inválidos, ou usuário inativo. Verifique suas credenciais.**

### E1.3
O sistema não cria sessão e retorna o fluxo para o passo P2, permitindo nova tentativa.

---

## E2. Falha no Serviço de Autenticação

### E2.1
No passo P5 ou P6, ocorre erro de comunicação com o Serviço de Autenticação (indisponibilidade, timeout, etc.).

### E2.2
O sistema GAC exibe a mensagem:

**ER002 – Serviço de autenticação indisponível no momento. Tente novamente mais tarde.**

### E2.3
O sistema registra log técnico da falha.

### E2.4
O caso de uso é encerrado, sem autenticar o usuário.

---

## E3. Tentativas excessivas de login

*(Aplica-se quando houver política de segurança para bloqueio de tentativas.)*

### E3.1
O sistema monitora o número de tentativas de login malsucedidas para o mesmo usuário ou origem.

### E3.2
Ao exceder o limite configurado (por exemplo, 5 tentativas), o sistema:
- bloqueia temporariamente novas tentativas para aquele usuário ou IP; e/ou  
- aciona o Serviço de Autenticação para bloquear o usuário.

### E3.3
O sistema exibe a mensagem:

**ER003 – Número máximo de tentativas excedido. Usuário temporariamente bloqueado.**

### E3.4
O caso de uso é encerrado.

---

# 7. Pós-condições

- Em caso de sucesso:
  - Uma **sessão autenticada** é criada para o usuário.
  - O sistema conhece o **perfil/permissões** do usuário, que serão utilizadas pelo caso de uso F7.2 – Controle de permissões.
  - Data, hora e, opcionalmente, o IP do login são registrados para auditoria.
- Em caso de falha:
  - Nenhuma sessão é criada.
  - Tentativas malsucedidas podem ser registradas para fins de segurança.

---

# 8. Interface Visual (IV1)

## IV1. Tela de Login / Autenticação

| Campo / Elemento            | Obrigatório | Formato        | Regra de Validação                                        |
|-----------------------------|------------|----------------|------------------------------------------------------------|
| Usuário / Login             | Sim        | Texto          | Não pode ser vazio                                        |
| Senha                       | Sim        | Texto (senha)  | Não pode ser vazia                                        |
| Seleção de perfil/unidade   | Não        | Seleção (combo)| Opcional, quando houver múltiplas unidades/perfis visíveis |
| Checkbox "Lembrar usuário"  | Não        | Booleano       | Opcional, apenas para preenchimento automático futuro      |
| Botão "Entrar"              | Sim        | Ação           | Dispara validação dos campos e chamada ao serviço de autenticação |
| Link "Esqueci minha senha"  | Não        | Ação/Link      | Opcional, redireciona para processo de recuperação (fora deste CDU) |
| Mensagem de erro (feedback) | Não        | Texto          | Exibe ER001, ER002 ou ER003, conforme o caso               |

---

# 9. Frequência de Utilização

Alta.

A funcionalidade é utilizada sempre que um usuário acessa o sistema GAC pela primeira vez em uma sessão ou após expiração do login, sendo requisito fundamental para garantir segurança e controle de acesso às demais funcionalidades (F1.x a F8.x).
