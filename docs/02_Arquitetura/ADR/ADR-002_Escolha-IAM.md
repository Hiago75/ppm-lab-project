# ADR-002: Escolha da Solução de Identidade e Acesso (IAM)

## Status
Aceito

## Contexto
O sistema necessita de um mecanismo de autenticação e autorização robusto com funcionalidades específicas como MFA, senhas temporárias, políticas de expiração de senha e gerenciamento de sessão. A discussão central foi decidir entre construir uma solução própria ou utilizar um serviço de mercado, considerando os requisitos funcionais detalhados.

Também foram considerados os seguintes fatores:
- A solução precisa ser implantável tanto em nuvem (Azure) quanto em ambiente on-premise, um requisito crítico para atender clientes do setor público.
- O prazo do projeto é curto, exigindo uma solução que acelere o desenvolvimento e minimize a complexidade de implementação.
- A equipe possui familiaridade prévia com a tecnologia Keycloak, reduzindo a curva de aprendizado.
- O Custo Total de Propriedade (TCO), incluindo custos de infraestrutura e operacionais, foi um fator importante na decisão.

Alternativas consideradas:
- **Desenvolvimento Interno**: Oferece controle total, mas foi desconsiderado pela alta complexidade, riscos de segurança inerentes, tempo de desenvolvimento elevado e a carga de manutenção contínua.
- **Azure AD B2C**: Solução PaaS robusta e nativa do Azure. Foi desconsiderada por ser exclusivamente um serviço de nuvem, não atendendo ao requisito fundamental de implantação on-premise.
- **Keycloak**: Solução open-source que atende ao requisito de implantação híbrida (nuvem e on-premise), oferece alta capacidade de personalização e a equipe já possui conhecimento prévio sobre a ferramenta.

## Decisão
Adotaremos o **Keycloak** como nossa plataforma de IAM. A implantação no ambiente de nuvem será realizada em **Máquinas Virtuais no Azure**. Esta abordagem foi escolhida por ser a mais pragmática, atendendo ao requisito de implantação híbrida com uma solução única e equilibrando custo e complexidade para a carga de usuários esperada.

## Consequências
A equipe assume a responsabilidade operacional pela infraestrutura do Keycloak (instalação, atualizações, segurança, backup). A escalabilidade futura exigirá intervenção manual. Em contrapartida, teremos uma base de código única para autenticação em ambos os ambientes (nuvem e on-premise), o que acelera o desenvolvimento e garante consistência funcional em todas as implantações.