Pontos de avaliação do desafio:
🧪 Automação e Cobertura:

☐ O conjunto de testes automatizados cobre as principais jornadas da aplicação?
☐ A solução demonstra bom entendimento de aplicações web (fluxos, navegação, estados)?
☐ Existem testes para cenários de falha (ex: validações de formulário, erros de autenticação)?
☐ Os fluxos de autenticação (login/logout) estão corretamente implementados e validados?
☐ O código de automação é legível, modular e segue boas práticas?
☐ Há reutilização adequada de código (ex: Page Objects, métodos utilitários)?
☐ Existe gerenciamento de dados de teste (ex: massa externa via JSON/CSV)?

🧱 Arquitetura e Boas Práticas:

☐ Foi implementado Page Object Model (POM) ou Screenplay Pattern corretamente?
☐ Há separação clara entre testes, páginas e utilitários?
☐ Os seletores utilizados são estáveis (id, data-testid, evitando XPath frágil)?
☐ O uso de waits está adequado (sem uso de pause/sleep fixo)?

🔁 Integração e Relatórios:

☐ Os testes estão integrados a uma pipeline de CI (GitHub Actions, GitLab, etc)?
☐ A execução é disparada automaticamente (push/pull request)?
☐ Relatórios de execução são gerados (ex: Allure)?
☐ Os relatórios incluem evidências (screenshots, logs)?

📚 Documentação e Entrega:

☐ O código-fonte completo foi disponibilizado em repositório (GitHub/GitLab)?
☐ A documentação descreve os testes implementados e os cenários cobertos?
☐ O README contém instruções claras para setup e execução do projeto?
☐ Foram utilizadas variáveis de ambiente para dados sensíveis (.env)?