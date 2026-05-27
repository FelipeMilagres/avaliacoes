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

