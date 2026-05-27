# =========================================
# ARQUIVO:
# docs/normalizacao/index.md
# =========================================

# Normalização de Dados 🔄

## Visão Geral

A documentação de normalização do projeto Athena possui como objetivo centralizar o entendimento técnico e funcional dos arquivos disponibilizados pela TSYS utilizados no ambiente UAT4.

A iniciativa busca estruturar uma base evolutiva para automação das massas de testes utilizadas pelos times de Qualidade, garantindo rastreabilidade, padronização e governança das informações consumidas.

---

## Objetivos da Normalização

- Padronizar estruturas consumidas pela automação;
- Organizar entendimento dos arquivos TSYS;
- Estruturar relacionamento entre cliente, conta e cartão;
- Reduzir atividades manuais;
- Garantir rastreabilidade operacional;
- Preparar evolução futura do ETL;
- Permitir escalabilidade da solução Athena.

---

## Escopo Inicial

Neste primeiro momento o foco será:

- Documentação do Response File;
- Entendimento estrutural do arquivo;
- Definição inicial das regras de normalização;
- Organização das massas disponíveis;
- Estruturação documental para evolução futura.

---

## Estrutura Atual

A documentação está organizada em:

| Documento | Objetivo |
|--|--|
| Contexto TSYS | Contextualização operacional |
| Localização dos Arquivos | Estrutura de diretórios |
| Referência Técnica | Planilhas e materiais auxiliares |
| Response File | Estrutura inicial analisada |
| Regras de Normalização | Padronizações iniciais |
| Estratégia Inicial | Escopo da primeira etapa |
| Evolução Futura | Próximos passos |

---

## Status Atual

| Item | Status |
|--|--|
| Response File | Em andamento |
| Regras de normalização | Em andamento |
| ETL completo | Futuro |
| Integração total TSYS | Futuro |

---

## Observações

A documentação será evoluída gradualmente conforme:

- Novos arquivos forem analisados;
- Regras forem identificadas;
- A arquitetura de dados evoluir;
- Novas necessidades operacionais forem definidas.







# =========================================
# ARQUIVO:
# docs/normalizacao/contexto.md
# =========================================

# Contexto TSYS

## Visão Geral

A TSYS disponibiliza diversos arquivos utilizados na operação do ambiente UAT4.

Esses arquivos possuem informações relacionadas a:

- Migração;
- Atualização de contas;
- Sincronização operacional;
- Movimentações;
- Estrutura de cartões;
- Dados operacionais do ambiente.

---

## Estrutura Atual

Atualmente existe uma planilha consolidada contendo aproximadamente:

# 113 arquivos

distribuídos entre:

- Processos diários;
- Processos semanais;
- Processos mensais;
- Processos sob demanda.

---

## Objetivo do Athena

O projeto Athena possui como objetivo consumir parte dessas informações para:

- Automatização das massas;
- Atualização automática de contas;
- Organização das massas disponíveis;
- Preparação de cenários E2E;
- Estruturação futura do ETL.

---

## Problemas Identificados

Antes da iniciativa Athena existiam dificuldades relacionadas a:

- Falta de padronização;
- Estruturas desconhecidas;
- Dependência operacional manual;
- Dificuldade de rastreabilidade;
- Ausência de documentação consolidada;
- Falta de relacionamento entre arquivos.

---

## Benefícios Esperados

Com a evolução da documentação e normalização espera-se:

- Maior governança;
- Redução operacional;
- Melhor rastreabilidade;
- Estrutura evolutiva;
- Base consistente para automações futuras.







# =========================================
# ARQUIVO:
# docs/normalizacao/localizacao.md
# =========================================

# Localização dos Arquivos

## Estrutura Inicial

Os arquivos disponibilizados pela TSYS são publicados inicialmente no fileserver corporativo.

Exemplo:

```txt
fileserverhom/migracao/TSYS
```

---

## Estrutura Utilizada pelo UAT4

Após processamento inicial os arquivos são movimentados internamente para:

```txt
fileserverhom/migracao/TSYS/UAT4
```

---

## Estruturas Encontradas

Nesse diretório encontram-se arquivos relacionados a:

- Carga inicial;
- Migração;
- Atualização;
- Sincronização;
- Operações do ambiente;
- Arquivos batch;
- Arquivos complementares.

---

## Objetivo da Estrutura

A organização atual permite:

- Separação operacional;
- Organização das cargas;
- Controle dos arquivos consumidos;
- Estruturação futura do Athena.

---

## Observações

A estrutura atual poderá sofrer alterações conforme:

- Evolução da arquitetura;
- Definições do time de dados;
- Estratégia futura de ingestão;
- Novas necessidades operacionais.







# =========================================
# ARQUIVO:
# docs/normalizacao/referencia-tecnica.md
# =========================================

# Referência Técnica

## Objetivo

Foi disponibilizada uma planilha técnica contendo informações operacionais relacionadas aos arquivos TSYS utilizados no ambiente UAT4.

Essa planilha será utilizada como principal referência técnica do projeto Athena.

---

## Informações Disponíveis

A estrutura atual possui informações como:

- Nome dos arquivos;
- Frequência;
- Origem e destino;
- Caminhos de transmissão;
- Nodes envolvidos;
- Estrutura operacional;
- Descrição técnica;
- Fluxo de carga e migração.

---

## Campos Identificados

| Campo |
|--|
| Interface Name File Description |
| Release/project |
| TSYS Technical contact |
| Frequency |
| Transmission Final Destination |
| Direction |
| Transmission Path |
| Test / Production |
| Client node |
| TSYS Node |
| TSYS Internal PATH |
| TSYS File name |
| Client / Vendor receiving / sending Path |
| Incoming TSYS mailbox route |

---

## Objetivo Futuro

Essa referência será utilizada para:

- Identificação dos arquivos;
- Governança operacional;
- Mapeamento técnico;
- Evolução do ETL;
- Relacionamento entre arquivos;
- Estratégia de ingestão.

---

## Status

> 🚧 Em construção

Novos detalhes serão incorporados gradualmente conforme evolução da análise técnica.







# =========================================
# ARQUIVO:
# docs/normalizacao/response-file.md
# =========================================

# Response File

## Objetivo

O Response File foi definido como ponto inicial da estratégia de normalização do projeto Athena.

O arquivo contém informações essenciais para:

- Identificação das contas;
- Relacionamento cliente/cartão;
- Organização inicial das massas;
- Estruturação operacional do ambiente.

---

## Estrutura Inicial Identificada

Exemplo:

```txt
Account_Number,Card_Number,Expiration_Date,CPF_NUMBER,Account_Status
70000182264,5448242539438264,31-DEC-27,22284160883,NORM
70000471485,5448242224331303,29-FEB-28,48541102602,NORM
```

---

## Campos Identificados

| Campo | Descrição Técnica | Tipo |
|--|--|--|
| Account_Number | Número da conta vinculada ao cliente | Alfanumérico |
| Card_Number | Número do cartão retornado pela carga | Numérico |
| Expiration_Date | Data de validade do cartão | Data |
| CPF_NUMBER | Documento do cliente | Numérico |
| Account_Status | Status operacional da conta | Alfanumérico |

---

## Objetivos do Arquivo

O Response File será utilizado inicialmente para:

- Organização das massas disponíveis;
- Relacionamento cliente/cartão;
- Entendimento estrutural dos dados;
- Estruturação da automação inicial.

---

## Regras Identificadas

Durante análise inicial foram identificadas as seguintes regras:

- Um cliente pode possuir múltiplos cartões;
- Uma conta pode possuir múltiplos cartões;
- O mesmo CPF pode aparecer diversas vezes;
- Cartões antigos e atuais podem coexistir.

---

## Estratégia Inicial

A estratégia inicial considera:

- Separação entre cliente e cartão;
- Relacionamento 1:N;
- Normalização estrutural;
- Tratamento básico dos dados;
- Padronização das colunas.







# =========================================
# ARQUIVO:
# docs/normalizacao/regras.md
# =========================================

# Regras de Normalização

## Objetivo

Definir as regras iniciais de padronização utilizadas pelo projeto Athena para tratamento das estruturas consumidas pela automação de massas.

---

## Regras Iniciais

O processo inicial deverá considerar:

- Remoção de espaços excedentes;
- Validação de tipos;
- Padronização das colunas;
- Tratamento de caracteres inválidos;
- Validação de registros inconsistentes.

---

## Padrão de Colunas

As colunas deverão seguir padrão:

```txt
UPPER_SNAKE_CASE
```

Exemplo:

```txt
ACCOUNT_NUMBER
CARD_NUMBER
EXPIRATION_DATE
CPF_NUMBER
ACCOUNT_STATUS
```

---

## Padrão de Datas

O campo:

```txt
EXPIRATION_DATE
```

deverá manter padrão:

```txt
DD-MMM-YY
```

Exemplo:

```txt
31-DEC-27
```

---

## Status da Conta

O campo:

```txt
ACCOUNT_STATUS
```

deverá manter os valores originais retornados pela TSYS.

Exemplos identificados:

- NORM;
- BLCK;
- AFRD;
- CLSD.

---

## Relacionamentos

A estrutura inicial considera:

| Relacionamento | Tipo |
|--|--|
| Cliente → Conta | 1:N |
| Conta → Cartão | 1:N |
| Cliente → Cartão | 1:N |

---

## Objetivos Futuros

As próximas evoluções deverão considerar:

- De/Para operacional;
- Regras de validação avançadas;
- Tratamento de inconsistências;
- Regras de negócio;
- Governança dos dados.







# =========================================
# ARQUIVO:
# docs/normalizacao/estrategia.md
# =========================================

# Estratégia Inicial

## Escopo da Primeira Etapa

Neste primeiro momento:

- Não será desenvolvido o ETL completo;
- Não será construída a estrutura final do banco;
- Não haverá integração com todos os arquivos TSYS;
- O foco permanecerá no Response File.

---

## Objetivos da Primeira Fase

A primeira etapa possui como objetivo:

- Entendimento do Response File;
- Estruturação documental;
- Definição inicial do De/Para;
- Organização das massas;
- Estruturação evolutiva do Athena.

---

## Estratégia Técnica

A estratégia inicial considera:

1. Documentação do arquivo;
2. Entendimento dos campos;
3. Identificação dos relacionamentos;
4. Normalização estrutural;
5. Estruturação futura do ETL.

---

## Resultado Esperado

Ao final da primeira etapa espera-se:

- Estrutura documental consolidada;
- Entendimento operacional do arquivo;
- Base inicial de normalização;
- Organização das massas disponíveis;
- Base para evolução futura.

---

## Status

> 🚧 Em construção

A estratégia será refinada conforme evolução do projeto.







# =========================================
# ARQUIVO:
# docs/normalizacao/evolucao.md
# =========================================

# Evolução Futura

## Próximos Passos

Após alinhamento com o time de dados e evolução da arquitetura UAT4 serão avaliados:

- Novos arquivos TSYS;
- Novas regras de normalização;
- Estrutura futura do ETL;
- Estratégia de ingestão;
- Relacionamento entre arquivos.

---

## Evoluções Previstas

A evolução da solução deverá considerar:

- Estrutura completa de dados;
- Processamento automatizado;
- Integração operacional;
- Consolidação das massas;
- Governança dos dados;
- Dashboards operacionais.

---

## Expansão da Estrutura

Futuramente a documentação deverá incorporar:

- Novos layouts;
- Estruturas operacionais;
- Regras de negócio;
- Regras de validação;
- Relacionamentos avançados;
- Estratégias de sincronização.

---

## Objetivo Final

O objetivo futuro do Athena é transformar a documentação em referência central dos arquivos consumidos pela automação de massas.

Permitindo:

- Rastreabilidade;
- Padronização;
- Governança;
- Escalabilidade;
- Evolução controlada.

---

## Status Atual

| Item | Status |
|--|--|
| Response File | Em evolução |
| Regras estruturais | Em evolução |
| ETL | Futuro |
| Integração total TSYS | Futuro |
| Governança avançada | Futuro |

```