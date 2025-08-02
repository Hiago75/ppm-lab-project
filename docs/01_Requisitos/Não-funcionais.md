# Requisitos Não-Funcionais

## RNF01 - Disponibilidade online  
O sistema deve possuir um uptime de 99.99%. Manutenções serão consideradas nessa conta e devem acontecer de forma previsível e fora do horário de pico para cada região.  
O sistema deve trabalhar com falhas localizadas apenas. Ele não pode cair completamente.

---

## RNF02 - Disponibilidade offline  
O sistema deve ser capaz de operar sem acesso a rede ainda que com recursos limitados e a sincronização deve ser feita logo que uma conexão for estabelecida.  
Quando sem conexão o usuário deve ser capaz de usar os recursos:
- Criação de projetos e tarefas
- Preenchimento de formulários
- Apontamento de horas
- Upload de anexos  

Tendo como restrições:  
Ações críticas bloqueadas (exclusão de projetos, alterações estruturais)  
IA, relatórios e integrações desabilitados offline  

Os conflitos devem ser resolvidos por hierarquia de usuário

---

## RNF03 - Multitenancy  
O sistema deve ser homogêneo, stateless e reimplementável. Deve ser capaz de trabalhar em nuvem em várias diferentes instâncias de forma individual.

---

## RNF04 - Auditoria  
Todas as ações relevantes devem ser registradas, contendo:
- Usuário responsável  
- Data e hora  
- Ação executada

---

## RNF05 - Performance geral  
O sistema deve ser capaz de apresentar as telas no geral em 500ms para 90% das requisições.

---

## RNF06 - Performance dos relatórios  
O sistema deve ser capaz de gerar relatórios com dados individuais dos projetos em até 500ms e preencher os cruzamentos totais e agregados em até 5 segundos ao trabalhar com relatórios complexos.

---

## RNF07 - Performance do login  
O login irá acontecer em 1 segundo ou menos para ao menos 95% das requisições.

---

## RNF08 - Segurança do usuário  
O sistema só pode ser acessado por usuários cadastrados que já tenham feito a alteração obrigatória de senha.  
O usuário deve fornecer usuário, senha e código de autenticação (MFA) para fazer o login.

---

## RNF09 - Segurança das informações  
Somente usuários que possuem acesso direto a um projeto ou informação devem ser capazes de visualizar.  
Um usuário precisa de um acesso a mais para poder editar uma informação que ele tenha acesso à visualização.

---

## RNF10 - Escalabilidade  
A arquitetura deve suportar crescimento futuro para até 500 usuários simultâneos sem degradação de performance.

---

## RNF11 - Integração  
Deve permitir integração futura com sistemas ERP ou ferramentas de BI, através de APIs REST ou SOAP.

---

## RNF12 - Usabilidade  
A interface deve ser intuitiva, permitindo o uso sem necessidade de treinamento extenso, baseada em padrões de design responsivo para dispositivos desktop e móveis.

---

## RNF13 - Conformidade Legal  
O sistema deve estar em conformidade com a LGPD (Lei Geral de Proteção de Dados), garantindo privacidade e segurança dos dados pessoais.

---

## RNF14 - Provedor de nuvem  
O sistema deve usar a nuvem da Azure

---

## RNF15 - Conformidade UE  
Dados de clientes europeus devem ficar armazenados na UE, por exigência do GDPRwwwwwwww
