# Normalização dos Arquivos — Projeto Athena

## Projeto

Athena — Automação e Gestão de Massas UAT4

---

## Responsável

Felipe Milagres Guimarães

---

## Data

14/05/2026

---

# 1. Objetivo

Este documento faz parte da documentação funcional e técnica do projeto:

```text id="n9u1zx"
Athena
```

O projeto Athena tem como objetivo automatizar o processo de geração, organização, atualização e manutenção das massas utilizadas nos testes do ambiente UAT4.

A proposta da solução é centralizar e estruturar as informações necessárias para:

* automações E2E
* utilização pelos QAs
* preparação automática das massas
* atualização operacional das contas
* redução de atividades manuais de configuração
* organização das massas disponíveis no ambiente

A automação será construída com base nos arquivos disponibilizados pela Tsys referentes:

* carga inicial do ambiente
* atualização das movimentações
* sincronização das informações
* arquivos operacionais utilizados no UAT4

Este documento possui como principal objetivo:

# documentar e detalhar os arquivos consumidos pelo projeto Athena

incluindo:

* estrutura dos arquivos
* layouts
* descrição das colunas
* tipos de dados
* posicionamento das informações
* relacionamento entre arquivos
* regras de normalização
* regras operacionais
* comportamento dos dados enviados pela Tsys

A documentação deverá evoluir gradualmente conforme:

* novos arquivos forem analisados
* novas necessidades forem identificadas
* a arquitetura definida pelo time de dados evoluir
* o projeto Athena ampliar o consumo das informações disponibilizadas pela Tsys

Neste primeiro momento, devido aos alinhamentos ainda em andamento com o time de dados e definição da nova estrutura do ambiente UAT4, o detalhamento inicial será realizado apenas sobre o arquivo:

```text id="d2s8m7"
Response File
```

O Response File será utilizado como ponto inicial da documentação por conter as informações básicas necessárias para:

* identificação das contas
* identificação dos cartões
* identificação do cliente
* organização inicial das massas disponíveis no ambiente

Os demais arquivos disponibilizados pela Tsys serão incorporados gradualmente nesta documentação conforme evolução do projeto Athena e definição da estratégia final de consumo dos dados.

---

# 2. Contexto

A Tsys disponibiliza diversos arquivos relacionados ao processo de:

* migração
* atualização
* sincronização
* carga operacional do ambiente UAT4

Atualmente, a planilha técnica consolidada possui o detalhamento de:

```text id="2t9m3f"
113 arquivos
```

com periodicidades:

* diária
* semanal
* mensal
* sob demanda

Esses arquivos fazem parte da estrutura operacional utilizada para:

* carga do ambiente
* atualização de dados
* sincronização das informações
* movimentações operacionais
* manutenção do ambiente UAT4

O objetivo futuro do projeto Athena é consumir parte dessas informações para:

* automatização das massas
* atualização automática das contas
* preparação de cenários de teste
* organização e identificação das massas
* enriquecimento operacional das informações

Neste primeiro momento, o foco será exclusivamente na documentação e normalização do Response File, utilizado como ponto inicial da estrutura de dados do projeto.

---

# 3. Localização dos Arquivos

Todos os arquivos disponibilizados pela Tsys são publicados inicialmente no fileserver corporativo:

```text id="8y0v5f"
fileserverhom/migracao/TSYS
```

Após o recebimento, os arquivos são movimentados internamente por um serviço corporativo para o diretório utilizado pelo ambiente UAT4:

```text id="3m0n2v"
fileserverhom/migracao/TSYS/UAT4
```

Nesse diretório encontram-se:

* arquivos batch
* arquivos de migração
* arquivos de atualização
* arquivos operacionais
* arquivos utilizados na carga do ambiente
* arquivos complementares disponibilizados pela Tsys

---

# 4. Referência Técnica Complementar

Foi disponibilizada no drive do projeto uma planilha técnica contendo o detalhamento dos arquivos disponibilizados pela Tsys para o ambiente UAT4.

A planilha contém informações como:

* nome dos arquivos
* frequência
* origem e destino
* caminhos de transmissão
* nodes envolvidos
* descrição técnica
* informações operacionais relacionadas à carga e migração

Link da documentação técnica:

```text id="1z8m5p"
[ADICIONAR LINK DO DRIVE]
```

A estrutura atual da planilha possui os seguintes campos:

| Campo                                        |
| -------------------------------------------- |
| Interface Name File Description (Production) |
| Release/project                              |
| TSYS Technical contact                       |
| Frequency                                    |
| Transmission Final Destination               |
| Direction                                    |
| Transmission Path                            |
| Test / Production                            |
| Client node                                  |
| TSYS Node                                    |
| TSYS Internal PATH                           |
| TSYS File name                               |
| Client / Vendor receiving / sending Path     |
| Incoming TSYS mailbox route?                 |
| Client / Vendor File name                    |
| Comments or Tasks                            |

Essa planilha será utilizada como principal referência técnica para:

* identificação dos arquivos
* entendimento da origem dos dados
* evolução do processo de normalização
* detalhamento futuro das estruturas consumidas

Conforme evolução da arquitetura definida pelo time de dados, este documento será atualizado gradualmente com:

* novos arquivos
* regras de normalização
* estrutura dos layouts
* identificação dos campos
* posição e composição dos dados
* relacionamento entre arquivos
* regras operacionais necessárias para automação das massas

O objetivo é centralizar neste documento toda a visão funcional e técnica dos arquivos consumidos no processo de automação e manutenção das massas do ambiente UAT4.

---

# 5. Arquivo Utilizado na Primeira Fase

O arquivo utilizado inicialmente será o:

```text id="m2u7z0"
Response File
```

Esse arquivo contém:

* contas carregadas no ambiente
* cartões vinculados
* validade dos cartões
* CPF do cliente
* status da conta

Exemplo:

```csv id="8j0t6s"
Account_Number,Card_Number,Expiration_Date,CPF_NUMBER,Account_Status
70000182264,5448242539438264,31-DEC-27,22284160883,NORM
70000471485,5448242224331303,29-FEB-28,48541102602,NORM
```

O Response File será utilizado inicialmente como base para:

* identificação das massas disponíveis
* relacionamento cliente/cartão
* organização inicial das contas
* entendimento da estrutura de dados enviada pela Tsys

---

# 6. Estrutura do Arquivo

| Campo           | Descrição Técnica                                | Tipo de Dado     |
| --------------- | ------------------------------------------------ | ---------------- |
| Account_Number  | Número da conta vinculada ao cliente             | Alfanumérico     |
| Card_Number     | Número do cartão retornado pela carga            | Numérico         |
| Expiration_Date | Data de validade do cartão                       | Data (DD-MMM-YY) |
| CPF_NUMBER      | Documento do cliente                             | Numérico         |
| Account_Status  | Status da conta no momento da geração do arquivo | Alfanumérico     |

---

# 7. Regras Identificadas

Durante a análise inicial foram identificadas as seguintes regras:

* um cliente pode possuir múltiplos cartões
* uma conta pode possuir múltiplos cartões
* o arquivo pode retornar cartões antigos e atuais simultaneamente
* o mesmo CPF pode aparecer múltiplas vezes no arquivo

Por esse motivo, a estratégia inicial considera:

* separação entre cliente e cartão
* relacionamento 1:N entre cliente e cartões
* normalização estrutural dos dados

---

# 8. Regras Iniciais de Normalização

O processo inicial deverá considerar:

* remoção de espaços excedentes
* validação de tipos
* padronização dos nomes das colunas
* tratamento básico de caracteres inválidos
* validação de registros inconsistentes

O campo:

```text id="0w8r5u"
Expiration_Date
```

deverá manter o padrão:

```text id="5s7v2n"
DD-MMM-YY
```

Exemplo:

```text id="9a4d8x"
31-DEC-27
```

---

# 9. Status da Conta

O campo:

```text id="2m7k9f"
Account_Status
```

representa o status da conta no momento da geração do arquivo pela Tsys.

Exemplos identificados:

* NORM
* BLCK
* AFRD
* CLSD

Os valores deverão ser mantidos conforme retorno original do arquivo.

---

# 10. Estratégia Inicial

Neste primeiro momento:

* não será desenvolvido o ETL completo
* não será construída a estrutura final do banco
* não será realizada integração com todos os arquivos da Tsys

O foco inicial será:

* entendimento do Response File
* normalização estrutural
* documentação do arquivo
* definição do De-Para inicial
* preparação para evolução futura

---

# 11. Evolução Futura

Após alinhamento com o time de dados e definição da nova estrutura do ambiente UAT4:

* os demais arquivos serão avaliados
* novas regras de normalização serão definidas
* novos arquivos poderão complementar a estrutura de automação de massas
* será definida a estratégia final de ingestão e consumo dos arquivos

Conforme evolução do projeto Athena, este documento será atualizado gradualmente com:

* novos layouts
* estrutura dos arquivos
* posição dos campos
* detalhamento técnico das colunas
* relacionamento entre arquivos
* regras de negócio
* regras de validação
* requisitos operacionais

O objetivo é transformar esta documentação em:

# referência central dos arquivos consumidos pelo projeto Athena

permitindo:

* rastreabilidade
* entendimento dos dados
* padronização da estrutura
* evolução controlada da automação de massas

---

# 12. Resultado Esperado

Ao final desta primeira etapa teremos:

* documentação técnica inicial do Response File
* entendimento padronizado da estrutura do arquivo
* regras iniciais de normalização definidas
* base documental para evolução futura
* estrutura preparada para detalhamento dos próximos arquivos disponibilizados pela Tsys
* ponto inicial da documentação evolutiva do projeto Athena
