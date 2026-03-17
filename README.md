# **Discovery da Arquitetura de Dados para Apresentação das Informações no Looker**

**Projeto:** [Automation] Enriquecimento da Base de UAT 4
**Versão:** 1.0
**Status:** Em andamento
**Responsável:** Lucas Mendes de Souza (EXT)
**Data:** 16/03/2026

---

## **1. Objetivo do Mapeamento**

Validar a integração técnica dos arquivos enviados diariamente pela TSYS com o novo template do Looker Studio.

O objetivo é otimizar a identificação de cenários específicos de teste, permitindo que o Time de Qualidade:

* Visualize o número correto do cartão por Unidade de Negócio (BU)
* Realize ações de regularização com base no status real da conta
* Utilize dados confiáveis extraídos diretamente dos sistemas da TSYS

---

## **2. Fontes de Dados e Integração (Arquivos TSYS)**

O cruzamento de dados permite isolar a massa necessária para cada cenário de teste, garantindo maior precisão na seleção das informações.

### **2.1 Arquivos Utilizados**

| Arquivo           | Conteúdo Principal     | Regra de Negócio                                                                                                         |
| ----------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| IssFeed_cardx     | Dados do Cartão        | Extrair o número do cartão específico do cenário, removendo registros irrelevantes, como cartões expirados ou adicionais |
| IssFeed_caccounts | Dados da Conta         | Extrair o status da conta para controle da saúde financeira                                                              |
| Feed_products     | Dicionário de Produtos | Atuar como camada de tradução dos códigos de produtos, consolidando os dados dos demais arquivos                         |

---

## **3. Melhorias na Visualização e Filtros Avançados**

O modelo proposto tem como objetivo reduzir ruído e aumentar a eficiência operacional na análise da massa de testes.

### **3.1 Filtro por Cenário (BU)**

A vinculação com o arquivo de produtos permite aplicar filtros que retornam exclusivamente o número do cartão correspondente ao cenário desejado.

**Problemas resolvidos:**

* Exibição de múltiplos cartões por conta
* Mistura de cartões de diferentes BUs, como Atacadão e Sam’s Club
* Dificuldade na identificação do cartão correto para execução do teste

**Benefício:**

* Precisão na seleção do cartão correto por cenário

---

### **3.2 Status de Manutenção de Pagamento**

O painel passa a exibir o status da conta, permitindo rápida tomada de decisão pelo Time de Qualidade.

**Status disponíveis:**

* **NORM**: Conta em estado normal, apta para uso
* **DLNQ**: Conta com pagamento em atraso, necessita regularização
* **LOST**: Conta com cartão perdido, necessita desbloqueio ou reemissão

**Benefício:**

* Identificação rápida de contas que exigem ação antes da execução dos testes

---

## **4. Fluxo de Operação (Processo Manual)**

O processo mantém uma etapa de curadoria manual para garantir a integridade e confiabilidade das informações.

### **4.1 Etapas do Processo**

1. **Recebimento**
   Recebimento diário dos arquivos no formato .txt provenientes da TSYS

2. **Carga**
   Upload manual dos arquivos no repositório que alimenta o Looker Studio

3. **Filtragem**
   Aplicação de filtros por BU e validação do status da conta, garantindo que a massa esteja apta para uso nos testes

---

## **5. Conclusão de Viabilidade**

A arquitetura proposta é tecnicamente viável.

A utilização do arquivo de produtos como camada de tradução possibilita a consolidação eficiente entre conta, número do cartão e contexto do produto.

Ao expor os status e organizar os dados por BU, o painel evolui de uma ferramenta de consulta para uma ferramenta de gestão de prontidão de massa.

Isso permite ao Time de Qualidade:

* Identificar rapidamente cenários viáveis
* Reduzir esforço operacional
* Aumentar a assertividade na preparação dos testes

---

## **6. Riscos e Considerações**

A arquitetura proposta melhora a organização e o consumo dos dados para testes, porém ainda apresenta pontos de atenção relacionados à operação, qualidade e governança dos dados. Esses fatores devem ser considerados para garantir a confiabilidade das informações e a eficiência do processo.

A análise dos riscos permite antecipar impactos, reduzir retrabalho e orientar a evolução da solução de forma estruturada.

### **6.1 Riscos Operacionais**

* Dependência de processo manual para carga dos dados
* Possibilidade de erro humano durante upload ou substituição de arquivos
* Ausência de controle de versionamento dos arquivos carregados

---

### **6.2 Riscos de Qualidade de Dados**

* Inconsistência entre arquivos, como cartões sem correspondência de conta
* Dados desatualizados em relação ao sistema de origem
* Registros duplicados ou incompletos impactando filtros
* Ausência de validação automática de integridade dos dados

---

### **6.3 Riscos de Arquitetura**

* Forte dependência do formato dos arquivos da TSYS
* Ausência de camada estruturada de processamento de dados
* Baixa escalabilidade para aumento de volume

---

### **6.4 Riscos de Governança**

* Ausência de rastreabilidade dos dados
* Falta de auditoria sobre alterações nos arquivos
* Não definição clara de responsabilidade sobre os dados

---

### **6.5 Impactos Potenciais**

* Execução de testes com massa inválida
* Aumento de retrabalho do Time de Qualidade
* Redução da confiabilidade do painel
* Decisões baseadas em dados inconsistentes

---

## **7. Evoluções Futuras (Roadmap Recomendado)**

A solução atual atende ao objetivo de disponibilização e organização da massa de testes, porém existem oportunidades relevantes de evolução para aumentar a eficiência operacional, a escalabilidade e a governança dos dados.

As iniciativas propostas visam reduzir dependências manuais, melhorar a qualidade das informações e estruturar a arquitetura para um modelo mais automatizado e sustentável.

### **7.1 Automação da Ingestão de Dados**

* Implementação de pipeline automatizado para ingestão dos arquivos
* Eliminação da etapa manual de upload
* Agendamento automático de cargas

---

### **7.2 Camada de Processamento de Dados**

* Criação de camada intermediária para tratamento e padronização
* Aplicação de regras de negócio e enriquecimento de dados

---

### **7.3 Validação e Qualidade de Dados**

* Implementação de validações automáticas de integridade
* Deduplicação e validação de consistência entre arquivos
* Geração de logs e controle de erros

---

### **7.4 Monitoramento e Observabilidade**

* Criação de indicadores de qualidade da massa
* Alertas para falhas de ingestão ou inconsistências
* Monitoramento de volume e disponibilidade dos dados

---

### **7.5 Governança de Dados**

* Definição de responsáveis pelos dados
* Implementação de rastreabilidade e histórico
* Estruturação de documentação e catálogo de dados

---

### **7.6 Evolução do Painel**

* Criação de indicadores estratégicos
* Segmentação por BU, produto e tipo de teste
* Melhoria na usabilidade e filtros dinâmicos

---

### **7.7 Integração com Fluxo de Testes**

* Integração com ferramentas de gestão de testes
* Possibilidade de seleção e exportação de massa diretamente do painel
* Evolução para modelo de gestão de dados de teste

---

## **8. Arquitetura da Solução**

A arquitetura atual segue um fluxo simplificado:

* **Origem dos Dados:** Arquivos TSYS
* **Ingestão:** Upload manual
* **Processamento:** Aplicação de regras e cruzamento de dados
* **Consumo:** Visualização no Looker Studio

Essa arquitetura atende ao cenário atual, porém possui oportunidades claras de evolução para maior automação e escalabilidade.

---

## **Sugestão de Nome do Arquivo**

**discovery-arquitetura-dados-looker-uat4.md**
