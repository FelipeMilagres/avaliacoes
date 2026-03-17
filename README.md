# **Discovery da Arquitetura de Dados para Apresentação das Informações no Looker**

**Projeto:** [Automation] Enriquecimento da Base de UAT 4
**Versão:** 1.0
**Status:** Em andamento
**Responsável:** Lucas Mendes de Souza (EXT)
**Data:** 16/03/2026

---

## **1. Objetivo do Mapeamento**

Validar a integração técnica dos arquivos enviados diariamente pela TSYS com o novo template do Looker Studio.

O objetivo é otimizar a identificação de cenários específicos de teste, permitindo que o time de Qualidade:

* Visualize o número correto do cartão por Unidade de Negócio (BU)
* Realize ações de regularização com base no status real da conta
* Utilize dados confiáveis extraídos diretamente dos sistemas da TSYS

---

## **2. Fontes de Dados e Integração (Arquivos TSYS)**

O cruzamento de dados permite isolar a massa necessária para cada cenário de teste, garantindo maior precisão na seleção dos dados.

### **2.1 Arquivos Utilizados**

| Arquivo           | Conteúdo Principal     | Regra de Negócio                                                                                             |
| ----------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------ |
| IssFeed_cardx     | Dados do Cartão        | Extrair o número do cartão específico do cenário, removendo registros irrelevantes (expirados ou adicionais) |
| IssFeed_caccounts | Dados da Conta         | Extrair o status real da conta para controle da saúde financeira                                             |
| Feed_products     | Dicionário de Produtos | Atuar como camada de tradução dos códigos de produtos, consolidando os dados dos demais arquivos             |

---

## **3. Melhorias na Visualização e Filtros Avançados**

O modelo proposto tem como foco a redução de ruído e o aumento da eficiência operacional na análise da massa de testes.

### **3.1 Filtro por Cenário (BU)**

A vinculação com o arquivo de produtos permite aplicar filtros que retornam exclusivamente o número do cartão correspondente ao cenário desejado.

**Problema resolvido:**

* O modelo anterior exibia múltiplos cartões por conta
* Existia mistura de cartões de diferentes BUs (ex: Atacadão, Sam’s Club)
* Havia dificuldade na identificação do cartão correto para o teste

**Benefício:**

* Precisão na seleção do cartão correto por cenário

---

### **3.2 Status de Manutenção de Pagamento**

O painel passa a exibir o status real da conta, permitindo rápida tomada de decisão pelo time de Qualidade.

**Status disponíveis:**

* **NORM**: Conta em estado normal (apta para uso)
* **DLNQ**: Conta com pagamento em atraso (necessita regularização)
* **LOST**: Conta com cartão perdido (necessita desbloqueio ou reemissão)

**Benefício:**

* Identificação rápida de contas que exigem ação antes da execução dos testes

---

## **4. Fluxo de Operação (Processo Manual)**

O processo mantém uma etapa de curadoria manual para garantir a integridade e confiabilidade das informações.

### **4.1 Etapas do Processo**

1. **Recebimento**
   O time responsável recebe diariamente os arquivos (.txt) provenientes da TSYS

2. **Carga**
   Upload manual dos arquivos no repositório que alimenta o Looker Studio

3. **Filtragem**
   Aplicação de filtros por BU e validação do status da conta (NORM/DLNQ/LOST), garantindo que a massa esteja apta para uso nos testes

---

## **5. Conclusão de Viabilidade**

A arquitetura proposta é tecnicamente viável.

A utilização do arquivo de produtos como camada de tradução possibilita a consolidação eficiente entre:

* Conta
* Número do cartão
* Contexto do produto

Ao expor os status (NORM, DLNQ, LOST) e organizar os dados por BU, o painel evolui de uma simples ferramenta de consulta para uma **ferramenta de gestão de prontidão de massa**.

Isso permite ao time de Qualidade:

* Identificar rapidamente cenários viáveis
* Reduzir esforço operacional
* Aumentar a assertividade na preparação dos testes

---

## **6. Riscos e Considerações**

* Dependência de processo manual para carga dos dados
* Possível defasagem entre geração e disponibilidade dos dados
* Risco de erro humano durante o processo de upload

---

## **7. Evoluções Futuras (Recomendado)**

* Automação do processo de ingestão de arquivos
* Integração direta com a TSYS via API ou pipeline de dados
* Implementação de alertas automáticos para inconsistências na massa
* Criação de indicadores de qualidade da massa (ex: % contas aptas, % contas com erro)

---

## **Sugestão de Nome do Arquivo**

**discovery-arquitetura-dados-looker-uat4.md**
