Plano de Transição de Ferramentas
Device Farm – BrowserStack → LambdaTest
Projeto: Tooling and Integration – Software Selection Device Farm
Contexto: Avaliação e possível substituição da solução atual de Device Farm
Ferramentas avaliadas: BrowserStack (atual) e LambdaTest (alternativa)
 
1. Introdução
Este documento apresenta o Plano de Transição de Ferramentas para a solução de Device Farm utilizada na execução de testes mobile pelos times de QA e desenvolvimento do Banco Carrefour.
Atualmente, a organização utiliza a plataforma BrowserStack para execução de testes em dispositivos móveis reais. No contexto do processo de Software Selection, está sendo conduzida uma avaliação comparativa entre o fornecedor atual e a plataforma LambdaTest.
Considerando que o contrato vigente com o BrowserStack possui término previsto para julho, torna-se necessário estabelecer um plano estruturado que permita:
•	garantir continuidade operacional das atividades de teste;
•	reduzir riscos técnicos durante uma possível mudança de fornecedor;
•	antecipar validações técnicas da nova solução;
•	preparar os times para adoção da nova plataforma.
Este plano define as atividades necessárias para viabilizar a transição entre ferramentas, caso seja tomada a decisão de migração.
 
2. Cenários Considerados
O plano contempla dois cenários possíveis resultantes do processo de Software Selection.
2.1 Continuidade com BrowserStack
Caso o resultado da avaliação indique a continuidade com o fornecedor atual:
•	não será necessária execução de atividades de migração;
•	o plano servirá apenas como documentação de contingência;
•	as atividades se limitarão à formalização da decisão e eventual renovação contratual.
2.2 Migração para LambdaTest
Caso a LambdaTest seja selecionada como nova solução de Device Farm:
•	será necessário executar as etapas descritas neste plano;
•	a transição será conduzida de forma gradual e controlada;
•	será adotado um período de validação paralela entre as ferramentas.
 
3. Análise de Impacto da Mudança
A possível substituição da ferramenta de Device Farm impacta diferentes dimensões da operação de testes mobile.
3.1 Impacto Técnico
A nova solução deverá integrar-se com os principais componentes da esteira de testes existente, incluindo:
•	execução de automação via Appium;
•	frameworks de automação utilizados pelos times, como WebdriverIO;
•	integração com pipelines GitLab CI/CD;
•	execução paralela de testes em dispositivos reais.
Também será necessário validar:
•	compatibilidade com os dispositivos utilizados nos cenários de testes;
•	estabilidade das sessões remotas;
•	suporte a testes de acessibilidade.
 
3.2 Impacto Operacional
A mudança de ferramenta pode exigir ajustes em processos operacionais atualmente estabelecidos, tais como:
•	processo de solicitação de acesso à plataforma;
•	fluxo de suporte e abertura de chamados;
•	procedimentos de execução de testes manuais e automatizados.
Esses processos deverão ser revisados e atualizados para refletir a nova solução.
 
3.3 Impacto nos Times
A adoção de uma nova ferramenta exigirá ações de adaptação e capacitação dos times de QA e desenvolvimento.
Entre os impactos esperados estão:
•	atualização dos guias de utilização da Device Farm;
•	adaptação de scripts e pipelines de automação;
•	treinamento dos times na nova plataforma.
 
4. Atividades de Liberação e Validação Interna
Considerando o contexto de um ambiente bancário, a adoção de uma nova ferramenta requer validações formais junto às áreas responsáveis por segurança e arquitetura.
As principais atividades incluem:
Avaliação de Segurança da Informação
•	submissão da solução para análise da área de Segurança da Informação (SI);
•	validação do tratamento de dados e logs;
•	análise de riscos relacionados ao uso da plataforma em ambiente corporativo.
Validação de Arquitetura
•	análise de aderência à arquitetura tecnológica do banco;
•	validação de integrações com a infraestrutura existente.
Conectividade com Ambientes Internos
Será necessário validar os mecanismos de acesso aos ambientes internos do banco, incluindo:
•	utilização de VPN ou túneis seguros;
•	comunicação com ambientes de testes (DEV, QA, HML);
•	conformidade com políticas de rede e segurança.
 
5. Plano de Integração Técnica
Após as validações iniciais, será necessário realizar a integração da ferramenta com a infraestrutura de testes existente.
As atividades incluem:
Integração com Automação de Testes
Validação da execução de testes automatizados utilizando:
•	Appium
•	WebdriverIO
Também deverá ser validada a execução de testes em:
•	dispositivos reais;
•	múltiplos dispositivos em paralelo.
 
Integração com CI/CD
A ferramenta deverá ser integrada aos pipelines existentes, possibilitando:
•	execução automática de testes mobile durante pipelines de build;
•	coleta de resultados e evidências de execução;
•	publicação de relatórios de testes.
 
Validação de Recursos de Debugging
Devem ser validados recursos que apoiem a análise de falhas, incluindo:
•	captura de screenshots;
•	gravação de sessões;
•	acesso a logs de execução;
•	monitoramento de rede.
 
6. Ajustes em Processos Operacionais
A adoção de uma nova ferramenta exigirá a adaptação de processos operacionais internos.
6.1 Processo de Solicitação de Acesso
Será necessário criar um fluxo de solicitação de acesso à nova plataforma por meio do ServiceNow, incluindo:
•	criação de fila de chamados específica para a ferramenta;
•	definição de fluxo de aprovação;
•	definição de perfis de acesso.
 
6.2 Administração da Ferramenta
Devem ser definidos responsáveis pela gestão da ferramenta, incluindo atividades como:
•	criação e gestão de usuários;
•	manutenção de projetos;
•	acompanhamento de utilização da plataforma.
 
6.3 Atualização de Procedimentos Operacionais
Os seguintes materiais deverão ser atualizados:
•	guias de utilização da Device Farm;
•	documentação de automação;
•	orientações para execução de testes manuais.
 
7. Plano de Comunicação e Capacitação
Para garantir uma transição eficiente, será necessário preparar os times para utilização da nova ferramenta.
As ações previstas incluem:
Comunicação
•	comunicação formal da possível mudança de ferramenta;
•	divulgação do cronograma de transição.
Capacitação
•	realização de sessões de treinamento para os times;
•	demonstração de execução de testes manuais e automatizados;
•	disponibilização de material de apoio.
 
8. Estratégia de Transição
Para reduzir riscos operacionais, recomenda-se a adoção de um período de transição controlada.
Durante esse período:
•	as duas ferramentas poderão ser utilizadas em paralelo;
•	será realizada validação da estabilidade da nova solução;
•	eventuais ajustes técnicos poderão ser realizados antes da descontinuação da ferramenta atual.
 
9. Cronograma Sugerido de Transição
Considerando o término do contrato atual em julho, sugere-se o seguinte cronograma indicativo:
Fase 1 – Validações iniciais
•	avaliação técnica da ferramenta
•	validação de segurança e arquitetura
Fase 2 – Integração técnica
•	integração com pipelines
•	validação de automação
Fase 3 – Preparação operacional
•	criação de processos de acesso
•	atualização de documentação
Fase 4 – Capacitação
•	treinamento dos times
•	comunicação da mudança
Fase 5 – Transição controlada
•	execução paralela entre ferramentas
•	validação final da nova solução
Fase 6 – Encerramento da ferramenta anterior
•	descontinuação gradual do BrowserStack
•	consolidação da nova plataforma.
 
10. Resultado Esperado
Ao final do processo de transição espera-se:
•	adoção segura da solução selecionada;
•	continuidade das atividades de testes mobile;
•	integração completa com a infraestrutura do banco;
•	capacitação dos times para utilização da nova ferramenta.





































9. Cronograma Sugerido de Transição
Considerando que o contrato atual com o fornecedor BrowserStack possui término previsto para 18 de julho de 2026, recomenda-se que as atividades de validação e preparação para uma eventual transição sejam conduzidas de forma antecipada, reduzindo o risco de descontinuidade nas atividades de testes mobile.
O cronograma abaixo apresenta uma sugestão de sequência das atividades necessárias para viabilizar a migração para a nova ferramenta, caso a decisão do processo de Software Selection indique a adoção da LambdaTest.
 
Fase 1 – Validações iniciais e decisão da ferramenta
Objetivo: Concluir o processo de Software Selection e validar tecnicamente a ferramenta candidata.
Atividades:
•	conclusão do benchmarking entre BrowserStack e LambdaTest;
•	validação técnica da execução de testes manuais e automatizados;
•	avaliação preliminar de performance e estabilidade da plataforma;
•	consolidação da recomendação técnica.
Resultado esperado:
•	definição da ferramenta que será adotada como solução oficial de Device Farm.
 
Fase 2 – Validações de segurança e arquitetura
Objetivo: Garantir que a nova solução esteja aderente aos requisitos de segurança e infraestrutura do banco.
Atividades:
•	submissão da ferramenta à avaliação da área de Segurança da Informação;
•	validação de conformidade com políticas internas de segurança;
•	validação de conectividade com ambientes internos via VPN ou túnel seguro;
•	aprovação de arquitetura da solução.
Resultado esperado:
•	ferramenta aprovada para integração com ambientes internos.
 
Fase 3 – Integração técnica e preparação do ambiente
Objetivo: Garantir que a nova ferramenta esteja integrada à esteira de testes existente.
Atividades:
•	integração com GitLab CI/CD;
•	validação de execução de automações via Appium e WebdriverIO;
•	configuração de catálogo de dispositivos;
•	validação de captura de logs e evidências.
Resultado esperado:
•	ambiente técnico preparado para utilização pelos times.
 
Fase 4 – Preparação operacional e capacitação
Objetivo: Preparar os times e os processos operacionais para utilização da nova ferramenta.
Atividades:
•	criação da fila de chamados no ServiceNow para solicitação de acesso;
•	definição de fluxo de aprovação de usuários;
•	atualização dos guias de utilização da Device Farm;
•	realização de sessões de treinamento para os times de QA e desenvolvimento.
Resultado esperado:
•	times capacitados e processos operacionais definidos.
 
Fase 5 – Período de execução paralela
Objetivo: Validar a estabilidade da nova solução antes da descontinuação da ferramenta atual.
Atividades:
•	execução de testes em paralelo nas duas plataformas;
•	validação da estabilidade das sessões de teste;
•	identificação e correção de possíveis problemas operacionais.
Resultado esperado:
•	validação da nova solução em cenário real de uso.
 
Fase 6 – Descontinuação da ferramenta atual
Objetivo: Concluir a transição para a nova solução de Device Farm.
Atividades:
•	encerramento gradual do uso do BrowserStack;
•	atualização final da documentação técnica;
•	comunicação oficial da transição para os times.
Resultado esperado:
•	consolidação da nova ferramenta como solução oficial de Device Farm.
 
Marco contratual
Considerando o término do contrato atual com o BrowserStack em 18 de julho de 2026, recomenda-se que as etapas de validação e preparação da nova ferramenta sejam conduzidas antes dessa data, garantindo que a organização tenha tempo suficiente para concluir a transição sem impacto na continuidade das atividades de testes mobile.
Sempre que possível, recomenda-se antecipar as atividades de validação técnica e integração da ferramenta candidata, permitindo que o período de execução paralela ocorra com antecedência ao encerramento do contrato vigente.




