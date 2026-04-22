O candidato desenvolveu a automação utilizando Maven, RestAssured e Cucumber, com uma estrutura bem organizada em camadas (config, factory, services, steps e runner), demonstrando boa prática de separação de responsabilidades e legibilidade de código. A solução cobre o CRUD completo de usuários, incluindo cenários positivos e negativos relevantes, além de utilizar geração de dados dinâmicos, o que contribui para a execução dos testes sem conflitos diretos. Também há integração com GitHub Actions e documentação clara no README, permitindo fácil entendimento e execução do projeto.

Por outro lado, a solução não atende completamente aos requisitos do desafio, principalmente por não contemplar autenticação via JWT, validações de contrato (schema), testes de headers e cenários mais robustos de erro. As validações estão concentradas em status code e mensagens, sem aprofundamento na estrutura das respostas. Além disso, o gerenciamento de dados não garante total isolamento entre execuções e a pipeline apresenta falha no comando mvn clean verify, comprometendo a geração de relatórios e a confiabilidade da automação em um fluxo contínuo.






O candidato desenvolveu a automação utilizando WebdriverIO com Appium, estruturando o projeto com Page Object Model e uma BasePage reutilizável, o que traz uma organização clara, boa reutilização e facilidade de manutenção. A solução cobre os principais fluxos do aplicativo, como login, cadastro, navegação e formulários, com cenários positivos e negativos bem definidos, além de uso de massa de dados externa e tratamento adequado para diferenças entre Android e iOS.

A execução ocorreu com sucesso nas duas plataformas via BrowserStack, com todos os cenários passando, o que demonstra estabilidade e confiabilidade da automação. O projeto também está integrado a uma pipeline no GitLab, com execução por plataforma e geração de relatórios Allure com evidências, incluindo captura de screenshots em caso de falha.

Como ponto de atenção, não há evidência de execução local em emuladores, conforme sugerido no enunciado. Ainda assim, como a execução em dispositivos reais via BrowserStack foi bem implementada e funcional, esse ponto acaba tendo um impacto menor na avaliação.

De forma geral, o candidato demonstra boa maturidade técnica em automação mobile, domínio das ferramentas propostas e capacidade de entregar uma solução consistente e próxima de um cenário real de uso.




Com base na análise técnica dos desafios de API e Mobile, o candidato demonstra boa base em automação de testes, com domínio das principais ferramentas e capacidade de estruturar soluções organizadas e funcionais.

No desafio de API, apresentou uma solução bem estruturada e com boa cobertura dos fluxos principais, porém com lacunas relevantes em critérios mais avançados como autenticação, validação de contrato e confiabilidade da pipeline. Já no desafio mobile, entregou uma solução mais madura, com boa organização, execução estável em múltiplas plataformas, integração com CI/CD e geração de evidências, atendendo de forma consistente aos requisitos.

Considerando o conjunto das entregas, o candidato demonstra capacidade técnica compatível com o esperado, mesmo com alguns pontos de evolução.

Status final: Aprovado para entrevista técnica
