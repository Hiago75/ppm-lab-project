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

## RF05 - Consulta de Propostas e projetos

**Descrição:**  
O usuário deve ser capaz de visualizar os projetos cadastrados.

**Campos/Entradas:**
- Identificador do usuário

**Saídas/Resultados:**
- São listados todos os projetos com os quais o usuário possui relação (como Equipe ou Responsável)
- O status atual de cada projeto é exibido

**Regras de negócio:**  
Aprovadores devem visualizar todos os registros, independentemente do vínculo.