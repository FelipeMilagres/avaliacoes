Desafio de Automação de Testes Web

Utilizando uma aplicação web pública (ex: e-commerce ou sistema de autenticação), desenvolva uma automação de testes que atenda os seguintes requisitos:

1. Cenários e Cobertura de Testes

Criar 10 cenários de teste cobrindo as principais jornadas da aplicação:
Autenticação (Login com fluxos de sucesso e falha)
Navegação entre páginas
Preenchimento de formulários e interação com elementos web (inputs, selects, checkboxes)
Validação de mensagens de erro e estados de validação
Padrão de Projeto: Implementar Page Object Model (POM) ou Screenplay Pattern.
Data-Driven (Bônus): Parametrizar testes dinâmicos utilizando arquivos JSON ou CSV.

2. Ambientes de Execução

Execução local em navegador (Chrome obrigatório)
Execução em outros navegadores (Firefox ou Edge) – bônus
Execução em nuvem (BrowserStack ou LambdaTest) – bônus

3. Evidências e Relatórios

Captura automática de screenshots em caso de falhas
Geração de relatório interativo (Allure Report) contendo:
Status de execução (Pass/Fail/Skipped)
Logs de execução
Screenshots anexados ao passo de falha
Metadados do ambiente (browser, versão, sistema operacional)

4. Integração Contínua (CI/CD)

Pipeline configurado no GitHub Actions ou GitLab CI/CD
Execução automática disparada por push ou pull_request no branch principal
Publicação dos artifacts do relatório de testes gerado no pipeline

Stack Tecnológica Recomendada
Linguagem: JavaScript ou TypeScript (Node.js)
Framework: WebdriverIO (v8 ou superior)
Test Runner: Mocha
Reporter: Allure Report
CI/CD: GitHub Actions ou GitLab CI/CD
Linter: ESLint + Prettier
Critérios de Avaliação
Organização e limpeza do código (estrutura, padronização, ausência de código duplicado)
Estratégia de seletores (priorização de id ou data-testid em vez de XPath)
Resiliência dos testes (uso de waits explícitos, evitando pausas fixas)
Documentação (README com instruções de execução)
Segurança (uso de variáveis de ambiente para dados sensíveis)

Entrega
Código fonte completo em repositório Git (GitHub ou GitLab)
README com instruções de configuração e execução dos testes