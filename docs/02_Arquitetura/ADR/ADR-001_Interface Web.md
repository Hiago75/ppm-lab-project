# ADR-001: Escolha do Framework Frontend

## Status
Aceito

## Contexto
O projeto requer uma interface web interativa e moderna, com foco em boa usabilidade, responsividade e integração futura com bibliotecas de visualização como cronogramas (Gantt), dashboards e formulários dinâmicos.  

Também foram considerados os seguintes fatores:
- A equipe atual possui experiência prévia com desenvolvimento em React.
- O sistema será desenvolvido com abordagem modular e desacoplada (clean architecture).
- A base de usuários pode evoluir para múltiplos dispositivos (desktop, tablet).

Alternativas consideradas:
- **Vue.js**: sintaxe elegante, curva de aprendizado baixa, mas menos utilizado pela equipe.
- **Angular**: solução completa, porém mais opinativa e pesada para o tipo de solução proposta.
- **Svelte**: moderno, mas com menor maturidade e ecossistema de bibliotecas.

## Decisão
Adotar **React** como framework principal de frontend, utilizando **TypeScript** como linguagem base.

## Consequências
- Aproveitamento da experiência prévia da equipe, reduzindo curva de adoção.
- TypeScript permite maior robustez na definição de contratos de dados entre frontend e backend.
- React tem um ecossistema rico, com diversas bibliotecas de Gantt e UI que atendem os requisitos do sistema.
- A escolha favorece manutenibilidade e testes, além de se alinhar à estratégia de micro frontends caso necessário.
- Evita o acoplamento de soluções mais monolíticas como Angular, favorecendo flexibilidade arquitetural.
