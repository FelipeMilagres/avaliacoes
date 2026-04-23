O candidato utilizou Python com Pytest, estruturando o framework em camadas (services, models, helpers e tests), com uso de fixtures para gerenciamento de contexto, Faker para dados dinâmicos, jsonschema para validação de contrato e requests para consumo da API. A solução demonstra boa organização, reutilização e legibilidade, além de integração com GitHub Actions e geração de relatórios (HTML e Allure).

A cobertura funcional é ampla, incluindo cenários positivos, negativos, autenticação, contrato e fluxo E2E, com execução estável.

Como pontos de atenção, a solução não cobre completamente aspectos necessários para a cobertura esperada para a API, com ausência de testes para headers e cenários mais extremos de payload. Também há oportunidade de evolução no gerenciamento centralizado de dados de teste, visando maior previsibilidade e escalabilidade.

Status: Aprovado com ressalvas


O candidato desenvolveu a automação utilizando WebdriverIO com Appium, estruturando o projeto com Page Object, boa separação de responsabilidades e uso de helpers reutilizáveis, além de aplicar corretamente esperas explícitas e data-driven com CSV e JSON. A cobertura contempla os principais fluxos do aplicativo, incluindo login, cadastro, navegação, formulários e cenário end-to-end, com geração de evidências (Allure, screenshots) e integração com CI/CD via GitLab.

Como pontos de atenção, a execução não se mostrou totalmente estável, com falha em um dos cenários durante a execução apresentada , indicando fragilidade em validações após scroll. Além disso, a execução também está restrita ao Android em ambiente local, sem evidência de execução em iOS (possivelmente por limitação do ambiente) e não há integração com device farm, o que limita a escalabilidade e cobertura em diferentes dispositivos reais.

Status: Aprovado com ressalvas




Nos dois desafios, ele demonstrou uma base sólida em automação, com frameworks bem estruturados (API em Python/Pytest e Mobile em WebdriverIO/Appium), boa organização em camadas, uso de boas práticas como reutilização de código, dados dinâmicos/data-driven e integração com CI/CD. A cobertura contempla os principais fluxos de negócio, incluindo cenários positivos, negativos e E2E, além de geração de evidências e relatórios.

Os pontos de atenção estão mais relacionados à robustez e completude: no desafio de API, há lacunas na cobertura e no Mobile há fragilidade na estabilidade (um teste falhando) e menor profundidade em algumas validações funcionais. Também há limitação de execução apenas em Android local, sem evidência de iOS ou integração com device farm, o que impacta a escalabilidade.

Ainda assim, a base técnica é consistente, demonstra entendimento prático de automação e indica potencial claro de evolução com direcionamento.

Resultado final: Aprovado para entrevista técnica








Olá, pessoal, tudo bem?

Concluímos a avaliação técnica do candidato Jhonatan Gomes (API e Mobile).

O candidato apresentou boa estrutura de automação, com uso adequado de frameworks, organização em camadas e clara separação de responsabilidades. Demonstrou boas práticas como reutilização de código, uso de helpers, data-driven (CSV/JSON), validação de contrato no API e aplicação de Page Object Model no Mobile. Também se destacou pela integração com CI/CD, geração de relatórios (Allure) e evidências de execução, além de cobertura dos principais fluxos de negócio, incluindo cenários positivos, negativos e E2E.

Como pontos de atenção, no desafio de API há lacunas para cobertura completa (rate limit e headers). No Mobile, a execução não está totalmente estável (1 falha) e parte dos testes valida apenas estabilidade da tela. A automação mobile também está restrita ao Android local, sem evidência de iOS ou integração com device farm.

Resultado: aprovado para entrevista técnica.

Seguimos à disposição.
