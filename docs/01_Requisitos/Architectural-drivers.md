## AD-01 - Availability
| Field           | Value                                          |
|-----------------|------------------------------------------------|
| Driver Name     | Uptime 99%                                     |
| Driver ID       | AD.01.Availability                             |
| Status          | Open                                           |
| Priority        | High                                           |
| Author          | Hiago                                          |
| Supporter       | System Architect                               |
| Sponsor         | Business Stakeholder                           |
| Inspector       | QA Lead                                        |
| Description     | The system must guarantee at least 99% availability, excluding planned maintenance windows, to ensure users can reliably access the application when needed. |
| Environment     | The application runs in a cloud environment.   |
| Stimulus        | A user attempts to log in, view data, or perform operations in the application. |
| Response        | The system is available and operational at least 99% of the time within a monthly measurement period. |
| Quantification  | 99% uptime per month. This equates to a maximum of approximately 7 hours and 18 minutes of downtime per month. |


## AD-02 - Segurança
| Campo                   | Valor                                  |
|-------------------------|----------------------------------------|
| Nome do driver          | Autenticação por login e senha         |
| Identificador do driver | AD-02 - Segurança                      |
| Status                  | Aberto                                 |
| Prioridade              | Alta                                   |
| Autor                   | Hiago                                  |
| Apoiador                | Arquiteto de software                  |
| Patrocinador            | Stakeholder                            |
| Inspetor                | QA Lead                                |
| Descrição               | O sistema deve garantir que somente usuários autenticados via login e senha tenham acesso a aplicação para garantir a segurança e experiencia personalidade de cada usuário |
| Ambiente                | O sistema esta corretamente operacional. |
| Estimulo                | Um novo usuário tenta acessar uma página do sistema |
| Resposta                | O sistema valida a sessão do usuário. Caso não seja existente o mesmo é redirecionado para a tela de log in para fazer a autenticação |
| Quantificação           | Suporte para bloqueio após 5 tentativas falhas. 100% das tentativas de acesso devem passar por autenticação. |

## AD-03 - Auditoria
| Campo                   | Valor                                              |
|-------------------------|---------------------------------------------------|
| Nome do driver          | Monitoramento de ações relevantes                  |
| Identificador do driver | AD-03 - Auditoria                                  |
| Status                  | Aberto                                            |
| Prioridade              | Média                                             |
| Autor                   | Hiago                                             |
| Apoiador                | Arquiteto de software                             |
| Patrocinador            | Stakeholder                                       |
| Inspetor                | QA Lead                                           |
| Descrição               | Garantir o registro de todas as ações relevantes no sistema, armazenando dados do usuário responsável, data, hora e a ação executada, assegurando rastreabilidade e suporte à auditoria. |
| Ambiente                | O sistema está corretamente operacional            |
| Estimulo                | Um usuário realiza uma ação relevante no sistema.  |
| Resposta                | O sistema deve registrar a ação, incluindo o usuário responsável, a data, a hora e a descrição da ação executada. |
| Quantificação           | 100% das ações relevantes devem ser auditáveis e consultáveis via logs assim que a ação for executada. |

## AD-04 - Performance
| Campo                   | Valor                                                                                     |
|-------------------------|-------------------------------------------------------------------------------------------|
| Nome do driver          | Performance do sistema                                                                    |
| Identificador do driver | AD-04 - Performance                                                                       |
| Status                  | Aberto                                                                                    |
| Prioridade              | Alta                                                                                      |
| Autor                   | Hiago                                                                                     |
| Apoiador                | Arquiteto de software                                                                     |
| Patrocinador            | Stakeholder                                                                               |
| Inspetor                | QA Lead                                                                                   |
| Descrição               | Garantir que o sistema responda às operações de cadastro e consulta em até 3 segundos e às operações de atualização em até 5 segundos, mesmo com até 50 usuários simultâneos, assegurando boa experiência ao usuário e desempenho adequado. |
| Ambiente                | O sistema está corretamente operacional e com alta carga de usuários                      |
| Estimulo                | O usuário executa operações de cadastro, consulta ou atualização no sistema, com até 50 usuários conectados simultaneamente. |
| Resposta                | O sistema deve processar e retornar os resultados das operações dentro dos tempos estabelecidos. |
| Quantificação           | Cadastro e consulta devem ser concluídos em até 3 segundos, e atualização em até 5 segundos, considerando até 50 usuários simultâneos. |


## AD-05 - Escalabilidade
| Campo                   | Valor                                                                                                               |
|-------------------------|---------------------------------------------------------------------------------------------------------------------|
| Nome do driver          | Escalabilidade do sistema                                                                                           |
| Identificador do driver | AD-05 - Escalabilidade                                                                                              |
| Status                  | Aberto                                                                                                              |
| Prioridade              | Alta                                                                                                                |
| Autor                   | Hiago                                                                                                               |
| Apoiador                | Arquiteto de software                                                                                               |
| Patrocinador            | Stakeholder                                                                                                         |
| Inspetor                | QA Lead                                                                                                             |
| Descrição               | Garantir que a arquitetura do sistema seja capaz de suportar crescimento futuro para até 500 usuários simultâneos, sem causar degradação perceptível na performance ou na experiência do usuário. |
| Ambiente                | O sistema está operacional, suportando até 50 usuários simultâneos, mas deve ser capaz de escalar para 500 sem perda de performance             |
| Estimulo                | O número de usuários simultâneos aumenta progressivamente até chegar a 500.                                         |
| Resposta                | O sistema deve manter tempos de resposta e performance estáveis, sem quedas de desempenho perceptíveis, mesmo com até 500 usuários simultâneos. |
| Quantificação           | Suportar até 500 usuários simultâneos sem ultrapassar os limites definidos para performance (resposta de operações críticas em até 5 segundos). |


## AD-06 - Integração
| Campo                   | Valor                                                                                                            |
|-------------------------|------------------------------------------------------------------------------------------------------------------|
| Nome do driver          | Integração com sistemas externos                                                                                 |
| Identificador do driver | AD-06 - Integração                                                                                               |
| Status                  | Aberto                                                                                                           |
| Prioridade              | Média                                                                                                            |
| Autor                   | Hiago                                                                                                            |
| Apoiador                | Arquiteto de software                                                                                            |
| Patrocinador            | Stakeholder                                                                                                      |
| Inspetor                | QA Lead                                                                                                          |
| Descrição               | O sistema permite integração com sistemas ERP e ferramentas de BI, utilizando APIs REST ou SOAP para comunicação eficiente e padronizada. |
| Ambiente                | Sistema em ambiente de desenvolvimento e produção, preparado para integrações via APIs REST e SOAP.              |
| Estimulo                | Necessidade de integração com sistemas externos ERP ou BI via APIs REST ou SOAP.                                 |
| Resposta                | O sistema expõe e consome APIs REST e SOAP que garantem compatibilidade e segurança na integração.               |
| Quantificação           | Suportar integração com pelo menos dois sistemas externos diferentes via APIs REST ou SOAP, com comunicação segura e documentação disponível. |

## AD-07 - Conformidade Legal
| Campo                   | Valor                                                                                                 |
|-------------------------|-----------------------------------------------------------------------------------------------------|
| Nome do driver          | Conformidade com LGPD                                                                                 |
| Identificador do driver | AD-08 - Conformidade Legal                                                                           |
| Status                  | Aberto                                                                                              |
| Prioridade              | Alta                                                                                                |
| Autor                   | Hiago                                                                                              |
| Apoiador                | Arquiteto de software                                                                               |
| Patrocinador            | Stakeholder                                                                                        |
| Inspetor                | QA Lead                                                                                            |
| Descrição               | Assegurar que o sistema esteja em conformidade com a Lei Geral de Proteção de Dados (LGPD), garantindo a privacidade e segurança dos dados pessoais dos usuários. |
| Ambiente                | Ambiente de produção e desenvolvimento com controle rigoroso de acesso e proteção de dados.         |
| Estimulo                | A coleta, armazenamento e processamento de dados pessoais no sistema.                               |
| Resposta                | O sistema deve implementar medidas técnicas e administrativas para proteger os dados pessoais, respeitando os direitos dos titulares conforme a LGPD. |
| Quantificação           | 100% dos dados pessoais devem ser tratados conforme os requisitos da LGPD, com auditoria e relatórios regulares de conformidade. |

## AD-08 - Fluxo de Aprovação
| Campo                   | Valor                                                                                                       |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| Nome do driver          | Fluxo de aprovação em etapas                                                                                 |
| Identificador do driver | AD-07 - Fluxo de Aprovação                                                                                   |
| Status                  | Aberto                                                                                                      |
| Prioridade              | Alta                                                                                                        |
| Autor                   | Hiago                                                                                                      |
| Apoiador                | Arquiteto de software                                                                                        |
| Patrocinador            | Stakeholder                                                                                                |
| Inspetor                | QA Lead                                                                                                    |
| Descrição               | O sistema deve suportar um fluxo de aprovação sequencial pelas etapas PMO, Equipe e Gerente de Área, garantindo que nenhuma etapa seja pulada. As ações possíveis são aprovar, rejeitar ou devolver para ajustes, e o status do projeto deve ser atualizado conforme as decisões. |
| Ambiente                | Ambiente de produção e desenvolvimento com controle de processos de aprovação.                              |
| Estimulo                | Submissão de propostas para aprovação nas etapas definidas.                                                |
| Resposta                | O sistema deve controlar o fluxo sequencial, registrar ações dos aprovadores e atualizar o status do projeto de acordo com as decisões tomadas. |
| Quantificação           | 100% dos fluxos de aprovação devem seguir a sequência correta, sem pular etapas, e registros devem ser auditáveis. |

## AD-09 - Notificações
| Campo                   | Valor                                                                                                    |
|-------------------------|----------------------------------------------------------------------------------------------------------|
| Nome do driver          | Notificações de status de propostas                                                                      |
| Identificador do driver | AD-08 - Notificações                                                                                      |
| Status                  | Aberto                                                                                                   |
| Prioridade              | Média                                                                                                    |
| Autor                   | Hiago                                                                                                   |
| Apoiador                | Arquiteto de software                                                                                     |
| Patrocinador            | Stakeholder                                                                                              |
| Inspetor                | QA Lead                                                                                                  |
| Descrição               | O sistema deve enviar notificações por e-mail e no sistema para usuários relacionados a uma proposta, informando mudanças de status e garantindo que todos os dados necessários estejam presentes. |
| Ambiente                | Ambiente de produção e desenvolvimento com sistemas de notificação integrados.                           |
| Estimulo                | Mudança de status em uma proposta relacionada a um usuário.                                              |
| Resposta                | O sistema envia e-mails e gera notificações internas para os usuários afetados, com informações atualizadas sobre o status da proposta. |
| Quantificação           | 100% das notificações devem ser enviadas com sucesso e no tempo máximo de 1 minuto após a mudança de status. |
