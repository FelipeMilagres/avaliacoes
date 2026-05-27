# Documento de Arquitetura da Solução (DAS) 📘 - Athena

| Versão documento | 1.0.0 |
|--|--|
| Quadrimestre criação | 2026-q1 |
| Quadrimestre atualização | 2026-q1 |
| Owner | CoE Qualidade |

---

# Objetivo do DAS

- Centralizar documentação técnica do Athena;
- Estruturar entendimento dos arquivos TSYS;
- Definir estratégia inicial de normalização;
- Padronizar consumo das massas de testes;
- Apoiar evolução futura da automação.

---

# Iniciativa

## Título

Athena - Plataforma de Gestão e Automação de Massas

---

## Descrição

O projeto Athena possui como objetivo automatizar o processo de geração, organização, atualização e manutenção das massas utilizadas nos testes E2E do ambiente UAT4.

A solução busca centralizar informações técnicas relacionadas aos arquivos disponibilizados pela TSYS, permitindo evolução estruturada da automação de massas utilizada pelas squads.

---

## Origem

Projeto interno CoE Qualidade

---

# Stakeholders

## CoE Qualidade

- QA Lead Automação: Felipe Milagres
- Engenharia Qualidade
- Times consumidores UAT4

---

# Athena | Plataforma de Gestão de Massas

## Definição Arquitetural da Solução

A solução Athena visa centralizar a gestão das massas utilizadas em cenários automatizados E2E, organizando informações provenientes da TSYS e preparando uma base evolutiva para automação operacional das contas utilizadas no ambiente UAT4.

Inicialmente o foco será estruturar:

- Response File;
- Regras de normalização;
- Relacionamento cliente/cartão;
- Organização das massas;
- Base documental evolutiva.

---

# Alinhamento Estratégico

## Objetivos Estratégicos

### Padronização Operacional

Estabelecer estrutura única de documentação e organização dos arquivos consumidos pelo processo de automação.

### Eficiência Operacional

Reduzir atividades manuais relacionadas à preparação de massas.

### Rastreabilidade

Garantir entendimento dos arquivos consumidos e regras aplicadas.

### Escalabilidade

Permitir expansão gradual para novos arquivos TSYS.

### Evolução da Qualidade

Preparar ambiente para futuras automações de dados e integrações ETL.

---

# Matriz de Responsabilidade

| Atividade | CoE Qualidade | Engenharia Dados | Infra | Segurança |
|--|--|--|--|--|
| Documentação DAS | R | C | I | I |
| Normalização | R | C | I | I |
| Estratégia Arquivos | R | R | I | I |
| Evolução Arquitetura | C | R | C | I |
| Governança | R | C | I | C |

Legenda:

- R → Responsável
- A → Aprovador
- C → Consultado
- I → Informado

---

# Arquitetura 💻

Para mais detalhes relacionados à arquitetura acesse o link:

[Arquitetura](arquitetura.md)

---

# Infraestrutura 🛠️

Para mais detalhes relacionados à infraestrutura acesse o link:

[Infraestrutura](infra.md)

---

# ADR's 📚

Para mais detalhes sobre decisões arquiteturais:

[ADR's](adrs/index.md)

---

# Referências 📎

- Planilha técnica TSYS
- Response File
- Estrutura UAT4
- Documentação Athena
- Estratégia de automação de massas

---

# Status Atual

| Item | Status |
|--|--|
| Response File | Em andamento |
| Regras normalização | Em andamento |
| ETL completo | Futuro |
| Integração arquivos TSYS | Futuro |




Bruno, entendo seu ponto e concordo que a intenção não deve ser buscar um “candidato perfeito”. Nosso objetivo também não é tornar o processo mais burocrático ou criar barreiras desnecessárias.

O contexto dessa validação adicional aconteceu por conta da própria mudança que fizemos no fluxo do processo seletivo. Antes, analisávamos os desafios técnicos primeiro e, com base no que era entregue, conduzíamos a entrevista técnica já aprofundando em cima das implementações realizadas. Como recebemos feedback de que o processo estava ficando muito demorado, invertimos a ordem para agilizar: primeiro a entrevista teórica e depois os desafios.

O efeito colateral dessa mudança é justamente perder os insumos técnicos durante a entrevista inicial. Por isso, em alguns casos, precisamos fazer uma validação complementar após a entrega, principalmente para garantir que o candidato realmente domina o que foi desenvolvido e consegue sustentar tecnicamente as decisões tomadas no desafio. Hoje temos cenários onde candidatos utilizam apoio externo, IA ou até terceiros para entrega, e a intenção dessa conversa adicional é apenas validar autoria, contexto e maturidade técnica sobre o que foi apresentado.

No caso da Izabela especificamente, o objetivo do papo seria exatamente esse: entender melhor algumas decisões da entrega, esclarecer dúvidas técnicas e validar o domínio dela sobre API e automação mobile conforme o material apresentado. Não era reprovar ou buscar perfeição. Inclusive, temos consciência de que sempre existirão pontos de evolução em qualquer profissional, seja pleno ou sênior.

O que buscamos no processo é garantir aderência ao nível esperado para evitar problemas futuros tanto para o time quanto para a própria consultoria. Quando um candidato entra muito desalinhado do que foi apresentado, acabamos gerando desgaste para todos os lados e até situações de substituição, o que também impacta a percepção da consultoria internamente.

De toda forma, como entendemos que essa etapa adicional acabou gerando desconforto, conversei com o Flávio e decidimos seguir de outra forma. Inclusive, já desmarquei o papo de amanhã.

Precisamos apenas que vocês formalizem por e-mail que a candidata ofertada para a posição pleno atende tecnicamente os pontos relacionados à automação mobile e API conforme apresentado nos desafios entregues, e que vocês validam essa aderência ao nível esperado da vaga. A partir dessa formalização, seguimos com a aprovação.

O Flávio provavelmente deve alinhar esse ponto com você também, mas da nossa parte a ideia é seguir de forma prática e transparente.
