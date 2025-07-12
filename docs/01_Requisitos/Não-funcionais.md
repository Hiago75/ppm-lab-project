# Requisitos Não-Funcionais

## RNF01 - Disponibilidade
O sistema deve possuir um uptime de 99% exceto em períodos programados de manutenção.

---

## RNF02 - Segurança
Somente usuários autenticados podem acessar o sistema. O acesso deve ocorrer por login e senha, podendo evoluir para autenticação multifator futuramente.

---

## RNF03 - Auditoria
Todas as ações relevantes devem ser registradas, contendo:
- Usuário responsável
- Data e hora
- Ação executada

---

## RNF04 - Performance
O sistema deve responder às operações de cadastro, consulta em até 3 segundos e 5 segundos para atualização, considerando até 50 usuários simultâneos.

---

## RNF05 - Escalabilidade
A arquitetura deve suportar crescimento futuro para até 500 usuários simultâneos sem degradação de performance.

---

## RNF06 - Integração
Deve permitir integração futura com sistemas ERP ou ferramentas de BI, através de APIs REST ou SOAP.

---

## RNF07 - Usabilidade
A interface deve ser intuitiva, permitindo o uso sem necessidade de treinamento extenso, baseada em padrões de design responsivo para dispositivos desktop e móveis.

---

## RNF08 - Conformidade Legal
O sistema deve estar em conformidade com a LGPD (Lei Geral de Proteção de Dados), garantindo privacidade e segurança dos dados pessoais.
