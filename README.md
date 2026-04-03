O candidato apresentou um projeto de automação mobile bem estruturado, utilizando WebDriverIO com Appium e TypeScript, demonstrando bom entendimento de arquitetura de testes e boas práticas de automação. A solução está organizada em camadas (screen objects, helpers, configs e data), com aplicação consistente do padrão Page Object e uso de data-driven através de arquivos JSON.

A cobertura de testes contempla os principais fluxos do aplicativo, incluindo login, cadastro, navegação, formulários, validações e cenário end-to-end, além de integração com Allure para geração de relatórios e evidências. A pipeline em GitLab CI/CD está bem estruturada, com separação de estágios e execução automatizada, incluindo suporte a emuladores e integração com BrowserStack.

Como pontos de atenção, a suíte apresentou falhas na execução, principalmente nos testes de Swipe (problemas de sincronização e scroll) e WebView (incompatibilidade de Chromedriver), além do uso recorrente de driver.pause, indicando dependência de tempo fixo e risco de instabilidade. Esses pontos mostram necessidade de evolução em confiabilidade dos testes e configuração de ambiente.

Status do desafio: Aprovado com ressalvas




Com base na avaliação dos desafios de API e Mobile, o candidato demonstrou bom domínio técnico e capacidade de estruturar frameworks de automação bem organizados, utilizando boas práticas como separação por camadas, uso de data-driven e integração com relatórios e CI/CD.

No desafio de API, apresentou boa cobertura de cenários, validações consistentes (incluindo contrato) e organização do código, com alguns pontos de atenção relacionados à estabilidade e controle de dados de teste. Já no desafio mobile, entregou uma solução robusta com Page Object, integração com Allure, execução em pipeline e suporte a múltiplos ambientes, porém com falhas na execução (Swipe e WebView) e dependência de pause, indicando necessidade de evolução em confiabilidade e troubleshooting.

De forma geral, o desempenho é compatível com o nível esperado, com gaps pontuais não bloqueadores.

Status: Aprovado para entrevista técnica