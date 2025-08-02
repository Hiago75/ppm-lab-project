# Requisitos Funcionais

## Visão  
Este documento descreve as funcionalidades mínimas do módulo de Gestão de Propostas de Projetos, parte do laboratório de arquitetura PPM.

---

## RF01 - Cadastro de Proposta

**Descrição:**  
O sistema deve permitir que o usuário cadastre uma proposta de projeto.

**Campos/Entradas:**
- Identificador
- Nome
- Usuário/Equipe responsável
- Justificativa
- Orçamento estimado

**Saídas/Resultados:**
- Proposta é salva
- O status do projeto resultante da proposta é "Planejamento"

**Regras de negócio:**  
Todos os dados são obrigatórios, exceto justificativa e orçamento.

---

## RF02 - Envio para Aprovação

**Descrição:**  
O usuário deve ser capaz de enviar uma proposta cadastrada para aprovação.

**Campos/Entradas:**
- Proposta previamente cadastrada

**Saídas/Resultados:**
- Projeto recebe o status "Aprovação"
- Aprovador é notificado

**Regras de negócio:**  
Somente propostas completas podem ser submetidas.

---

## RF03 - Fluxo de Aprovação

**Descrição:**  
O sistema deve permitir aprovação em etapas:
- PMO
- Equipe
- Gerente de Área

**Campos/Entradas:**
- Identificador da proposta
- Ação do aprovador (aprovar, rejeitar, devolver para ajustes)

**Saídas/Resultados:**
- Status do projeto é atualizado para "Iniciar" caso aprovado, ou "Reprovado" caso rejeitado
- Registro de quem aprovou/rejeitou

**Regras de negócio:**  
Nenhuma etapa pode ser pulada.

---

## RF04 - Notificações

**Descrição:**  
O sistema deve notificar os usuários relacionados a uma proposta sobre mudanças de status, via e-mail e notificação no sistema.

**Campos/Entradas:**
- Identificador
- Nome do projeto
- Novo status
- E-mail do destinatário

**Saídas/Resultados:**
- E-mail é enviado ao destinatário com o status atual
- Notificação é gerada no sistema para o usuário

**Regras de negócio:**  
Todos os dados de entrada devem estar presentes.

---

## RF05 - Consulta de Propostas e Projetos

**Descrição:**  
O usuário deve ser capaz de visualizar os projetos cadastrados.

**Campos/Entradas:**
- Identificador do usuário

**Saídas/Resultados:**
- São listados todos os projetos com os quais o usuário possui relação (como Equipe ou Responsável)
- O status atual de cada projeto é exibido

**Regras de negócio:**  
Aprovadores devem visualizar todos os registros, independentemente do vínculo.

---

## RF06 - Relatórios Dinâmicos

**Descrição:**  
O sistema deve ser capaz de gerar relatórios dinâmicos totalmente customizados e baseados em diversos projetos.

**Campos/Entradas:**
- Projetos a serem usados no relatório
- Campos do relatório
- Filtros do relatório
- Gráficos
- Exportação para Excel ou PDF

**Saídas/Resultados:**
- O relatório é gerado seguindo os dados inseridos.
- O relatório é exportável no formato de preferência (Excel ou PDF)

**Regras de negócio:**  
- Os relatórios devem poder ser montados usando somente projetos que o usuário tem acesso.  
- Os relatórios podem conter somente informações que o usuário possui acesso em cada projeto.

---

## RF07 - Cadastro de Novo Usuário

**Descrição:**  
Um administrador do sistema deve ser capaz de cadastrar novos usuários.

**Campos/Entradas:**
- Nome
- Cargo
- Email
- Usuário
- Licença de acesso

**Saídas/Resultados:**
- O usuário é cadastrado com uma senha temporária que é enviada ao email do mesmo.

**Regras de negócio:**
Ao fazer o primeiro login o usuário deverá criar uma nova senha que deve cumprir os requisitos:
- Ao menos 1 caractere maiúsculo
- Ao menos 1 caractere minúsculo
- Ao menos 1 número
- Ao menos 1 símbolo especial
- No mínimo 10 caracteres
- Não são permitidas sequências

---

## RF08 - Login

**Descrição:**  
O usuário deve ser capaz de fazer login no sistema desde que sejam cumpridas as devidas verificações.

**Campos/Entradas:**
- Email
- Senha
- Código de verificação

**Saídas/Resultados:**
- O usuário é logado no sistema e recebe uma sessão válida por 1 dia. Ao término da sessão é necessário efetuar o processo de login novamente.

**Regras de negócio:**
- Ao efetuar o login com o usuário e senha corretos, será solicitada uma autenticação multifatorial usando um código.  
- A sessão será válida por 1 dia, precisando efetuar novo login no próximo dia  
- Caso o usuário fique inativo do sistema por 5 minutos, o mesmo terá sua sessão invalidada.  

---

## RF09 - Troca de Senha

**Descrição:**  
O usuário deve trocar sua senha a cada 30 (trinta) dias.

**Campos/Entradas:**
- Email
- Senha atual
- Nova senha

**Saídas/Resultados:**
- Uma confirmação da troca é enviada por email. 

**Regras de negócio:**
- Caso seja confirmado, a senha é trocada.  
- Caso seja negado, a conta é bloqueada temporariamente.

---

## RF10 - Integração (SAP, Salesforce, ERPs Financeiros)

**Descrição:**  
O sistema deve ser capaz de atuar com integrações externas diversas provisionadas pelo sistema.

**Campos/Entradas:**
- Informações sobre o projeto (nome, custo, receita, estimativa)

**Saídas/Resultados:**
- Status da última sincronização
- Logs/Mensagens de erro

**Regras de negócio:**
- O sistema deve suportar modelos alternativos, sendo estes: batch, polling e arquivos intermediários.