# ADR-004: Estratégia de Banco de Dados e Multitenancy

## Status
Aprovado

## Contexto
A aplicação precisa de uma estratégia de banco de dados que suporte um modelo de serviço híbrido (on-premise e nuvem), garantindo alta disponibilidade sem um ponto único de falha (SPOF). A estratégia deve atender aos requisitos de multitenancy (RNF03), segurança da informação (RNF09) e escalabilidade para 500 usuários simultâneos (RNF10).

Também foram considerados os seguintes fatores:
- **Tecnologia do Banco de Dados:** A escolha do PostgreSQL se deu por sua robustez, suporte nativo a schemas, e excelente compatibilidade com ambientes on-premise e ofertas gerenciadas na Azure (Azure Database for PostgreSQL), alinhado ao RNF14.
- **Isolamento de Dados vs. Custo:** A necessidade de isolar os dados dos clientes (RNF09, RNF13) foi um fator crítico. A discussão ponderou o nível de isolamento contra o custo e a complexidade operacional.
- **Prevenção de "Vizinho Barulhento":** Foi identificado o risco de um tenant com uso intenso de recursos (especialmente relatórios, RNF06) degradar a performance para outros tenants (RNF05).
- **Reutilização de Componentes:** A solução deveria, sempre que possível, reutilizar componentes já existentes na arquitetura para reduzir a complexidade e o custo.

**Alternativas consideradas:**
- **Banco de Dados por Tenant:** Oferece isolamento máximo, mas foi descartado devido ao alto custo, complexidade de gerenciamento e provisionamento lento, o que dificultaria a escalabilidade.
- **Schema Compartilhado com Discriminador:** A alternativa de menor custo, mas foi descartada por apresentar um risco de segurança inaceitável (falha de programação poderia expor dados de todos os tenants) e por agravar o problema do "vizinho barulhento".
- **Governança com PgBouncer:** Foi sugerido para limitar recursos por tenant no nível do banco, mas considerado "over-architecture" para a carga esperada de um sistema PPM, adicionando complexidade desnecessária.

## Decisão
Foi decidido adotar uma abordagem de **Schema por Tenant** sobre um **cluster de alta disponibilidade do PostgreSQL, gerenciado pelo Patroni**.

Para mitigar o risco de performance ("vizinho barulhento"), as operações de geração de relatórios complexos serão desacopladas da aplicação principal, sendo processadas de forma **assíncrona através de filas no RabbitMQ**, um componente já utilizado para a funcionalidade offline (ADR-003).

## Consequências
- A aplicação terá um forte isolamento de dados entre os tenants a um custo operacional gerenciável.
- A infraestrutura de banco de dados será altamente disponível, sem um ponto único de falha.
- A performance geral do sistema fica protegida contra picos de uso de relatórios.
- A equipe de desenvolvimento precisará criar e manter scripts para aplicar migrações de schema em todos os schemas dos tenants de forma automatizada.
- A experiência do usuário para a geração de relatórios complexos muda de síncrona para assíncrona. A interface precisará de um mecanismo para notificar o usuário quando o relatório estiver pronto.
