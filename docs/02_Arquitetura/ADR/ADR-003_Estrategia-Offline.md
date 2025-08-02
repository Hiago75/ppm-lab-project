# ADR-003: Estratégia de Sincronização e Disponibilidade Offline

## Status
Aprovado

## Contexto
A necessidade de suportar operações em locais com conectividade de internet limitada ou inexistente é um requisito crítico para os usuários que trabalham em campo. Esta decisão é guiada pelo requisito **RNF02 - Disponibilidade offline** e deve garantir a funcionalidade dos requisitos **RF01 a RF05** em modo offline.

Também foram considerados os seguintes fatores:
- **Experiência do Usuário:** A interface deve permanecer rápida e responsiva, independentemente da qualidade da conexão.
- **Integridade dos Dados:** A sincronização deve garantir a consistência dos dados, com uma estratégia clara para a resolução de conflitos.
- **Segurança:** Os dados armazenados localmente no dispositivo do cliente devem ser protegidos.
- **Volume de Dados:** Cada projeto pode conter de 300 a 400 atividades, com um tamanho estimado de 1MB em formato JSON.

Alternativas consideradas:
- **Sincronização sob demanda**: Descartada por não oferecer uma experiência de usuário transparente, exigindo que o usuário baixe os projetos proativamente para trabalhar offline.
- **CRDTs (Conflict-free Replicated Data Types)**: Descartada por ser incompatível com o requisito de negócio de resolução de conflitos baseada na hierarquia do usuário.

## Decisão
Será implementada uma arquitetura **Offline-First**. As operações essenciais (RF01-RF05) serão executadas contra um banco de dados local no cliente (ex: SQLite, PouchDB). As alterações serão enfileiradas e sincronizadas com o servidor assim que uma conexão for estabelecida.

O servidor ficará responsável pela lógica de resolução de conflitos, aplicando a regra de negócio definida no **RNF02**, onde a alteração do usuário de maior hierarquia prevalece em caso de conflito.

## Consequências
- **Complexidade do Backend:** Haverá um aumento na complexidade do backend para gerenciar a lógica de sincronização e resolução de conflitos.
- **Atraso em Ações Dependentes do Servidor:** Notificações (RF04) e fluxos de aprovação (RF03) só serão disparados após o usuário estar online e os dados serem sincronizados, o que pode introduzir latência no processo.
- **Segurança Local:** É mandatório criptografar o banco de dados local no dispositivo do cliente para proteger as informações contra acesso não autorizado.
- **Feedback ao Usuário:** A interface do usuário deve fornecer feedback claro sobre o status da conectividade e da sincronização de dados.
