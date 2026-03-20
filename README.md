# **Documento de Levantamento de Requisitos e Arquitetura – Plataforma de Gestão de Massas (TDM)**

---

## **1. Visão Geral**

Este documento apresenta a versão inicial consolidada dos requisitos técnicos, funcionais e arquiteturais para a implementação de uma **Plataforma de Gestão de Dados de Teste (Test Data Management - TDM)**.

A solução tem como objetivo estruturar e padronizar o ciclo completo de dados de teste, incluindo ingestão, criação, maturação e consumo, garantindo maior confiabilidade, rastreabilidade e eficiência operacional para o Time de Qualidade.

---

## **2. Objetivo da Solução**

Estabelecer uma arquitetura centralizada que permita:

* Ingestão e normalização de dados provenientes de arquivos batch da TSYS
* Criação de massas de teste por meio das APIs transacionais oficiais da TSYS (POST/VR – Apache)
* Armazenamento estruturado e versionado das massas
* Execução de processos automatizados de maturação e gestão contínua
* Disponibilização dos dados via API para consumo padronizado
* Redução de dependência manual na preparação de cenários de teste

---

## **3. Definições e Conceitos**

| Termo          | Definição                                                   |
| -------------- | ----------------------------------------------------------- |
| TDM            | Plataforma de gestão de dados de teste                      |
| Massa de Teste | Conjunto de dados preparados para execução de cenários      |
| Maturação      | Processo automatizado de manutenção e preparação das massas |
| ETL            | Processo de extração, transformação e carga                 |
| TSYS APIs      | APIs transacionais utilizadas para criação de dados reais   |
| LDSG           | Processo necessário para ativação ou ajuste de massas       |

---

## **3.1 Conceito de Massa Pronta (Ready-to-Use)**

Uma massa de teste será considerada pronta quando:

* Estiver com dados consistentes e íntegros
* Estiver com status adequado para execução de testes
* Não exigir ajustes manuais adicionais
* Estiver validada pelas regras de maturação

---

## **4. Escopo da Solução**

### **4.1 Dentro do Escopo**

* Ingestão de arquivos TSYS
* Normalização e tratamento de dados
* Armazenamento em base central
* Criação de massas via APIs TSYS
* Execução de regras de maturação e gestão contínua
* API de gerenciamento de massas
* Suporte ao consumo por automação

---

### **4.2 Fora do Escopo**

* Alterações em sistemas core da TSYS
* Desenvolvimento de novas APIs TSYS
* Interface gráfica (UI) nesta fase inicial
* Gestão de dados produtivos

---

## **5. Visão Arquitetural**

A solução será composta por cinco camadas principais:

### **5.1 Fonte de Dados**

* Arquivos batch TSYS (.txt)
* APIs transacionais TSYS (POST/VR – Apache)

---

### **5.2 Ingestão e Processamento**

* Serviço ETL em Python
* Parsing, normalização e tratamento de dados

---

### **5.3 Armazenamento (Data Store)**

* Base central de massas
* Persistência de estado e histórico
* Fonte única da verdade

---

### **5.4 Maturação e Gestão de Massas**

* Execução de serviços automatizados (workers/jobs)
* Manutenção contínua das massas
* Atualização de consistência estrutural e integridade
* Regularização de status financeiros (pagamento, atraso, bloqueio)
* Aplicação de regras de negócio (incluindo LDSG)
* Garantia de prontidão para uso em testes
* Eliminação de necessidade de intervenção manual

---

### **5.5 Consumo**

* API de gerenciamento de massas
* Integração com automações e testes QA

---

## **6. Fluxos da Solução**

### **6.1 Fluxo de Ingestão (Batch)**

* Recebimento de arquivos TSYS
* Processamento via ETL
* Normalização e persistência na base

---

### **6.2 Fluxo de Criação de Massas (Online)**

* Solicitação via API interna
* Consumo das APIs transacionais TSYS (POST/VR)
* Criação de entidades reais
* Persistência automática na base

---

### **6.3 Fluxo de Maturação e Gestão Contínua**

* Execução de serviços automatizados de forma contínua ou agendada
* Aplicação de regras de negócio
* Atualização de:

  * Status de pagamento
  * Situação da conta/cartão
  * Consistência estrutural
* Correção automática de inconsistências
* Garantia de massa pronta para uso

---

### **6.4 Fluxo de Consumo**

* Consulta via API
* Seleção de massa por cenário
* Uso em automações de teste

---

## **7. Requisitos Funcionais**

### **RF01 – Ingestão de Arquivos**

* Receber arquivos TSYS automaticamente
* Validar formato e estrutura
* Executar parsing e tratamento

---

### **RF02 – Normalização de Dados**

* Padronizar estrutura
* Realizar junções entre dados
* Eliminar inconsistências

---

### **RF03 – Armazenamento de Massas**

* Persistir dados em base central
* Manter histórico e estado
* Garantir rastreabilidade

---

### **RF04 – Maturação e Gestão Automatizada de Massas**

* Executar processos automatizados contínuos
* Manter dados atualizados e consistentes
* Aplicar regras de negócio (pagamento, status, estrutura)
* Corrigir inconsistências automaticamente
* Garantir prontidão sem intervenção manual
* Permitir reprocessamento

---

### **RF05 – Criação de Massas via APIs TSYS**

* Consumir APIs transacionais (POST/VR – Apache)
* Criar entidades reais (cartão, conta, cliente)
* Seguir fluxo produtivo
* Persistir automaticamente os dados

---

### **RF06 – API de Gerenciamento**

* Disponibilizar operações de consulta, criação, atualização e exclusão
* Permitir filtros por cenário, status e BU
* Garantir controle e padronização de acesso

---

### **RF07 – Consumo pelo QA**

* Permitir integração com automação
* Garantir uso de massas prontas
* Facilitar seleção e utilização dos dados

---

## **8. Requisitos Técnicos**

### **RT01 – ETL**

* Implementação em Python
* Execução automatizada
* Suporte a arquivos batch

---

### **RT02 – Banco de Dados**

* Banco relacional ou analítico
* Alta performance e escalabilidade
* Estrutura preparada para volume elevado

---

### **RT03 – Maturação e Processamento Assíncrono**

* Workers ou jobs assíncronos
* Execução contínua ou agendada
* Aplicação de regras de manutenção
* Suporte a reprocessamento

---

### **RT04 – API**

* Arquitetura REST
* Autenticação e autorização
* Logging estruturado

---

### **RT05 – Integração TSYS**

* Consumo de APIs POST/VR via Apache
* Tratamento de falhas e retentativas
* Controle de chamadas

---

### **RT06 – Observabilidade**

* Logs centralizados
* Monitoramento de jobs
* Alertas de falha

---

## **9. Requisitos Não Funcionais**

### **Performance**

* Resposta rápida para consultas e operações

### **Escalabilidade**

* Suporte ao crescimento de dados e uso

### **Confiabilidade**

* Integridade e consistência garantidas

### **Segurança**

* Controle de acesso e auditoria

### **Manutenibilidade**

* Código modular e de fácil evolução

---

## **10. Riscos e Mitigações**

| Risco                | Mitigação                    |
| -------------------- | ---------------------------- |
| Dependência da TSYS  | Monitoramento e fallback     |
| Falhas em APIs       | Retry e tratamento de erro   |
| Dados inconsistentes | Validação automática         |
| Alto volume de dados | Estratégia de escalabilidade |

---

## **11. Premissas**

* APIs TSYS disponíveis e estáveis
* Arquivos com layout consistente
* Infraestrutura adequada
* Uso via API pelo time de QA

---

## **12. Restrições**

* Dependência de integrações externas
* Limitações de acesso a APIs TSYS
* Possível necessidade de etapas manuais iniciais

---

## **13. Critérios de Sucesso**

* Redução do tempo de preparação de massa
* Aumento da confiabilidade dos testes
* Redução de erros operacionais
* Adoção pelo time de QA

---

## **14. Diferencial da Solução**

A solução implementa um modelo de **gestão ativa de massas**, onde dados são continuamente mantidos e preparados por processos automatizados.

Além disso, utiliza APIs transacionais reais da TSYS, garantindo aderência ao fluxo produtivo e alta fidelidade dos dados.

---

## **15. Roadmap de Evolução (Sugestão)**

* Automação completa da ingestão
* Implementação de mensageria (fila)
* Data Quality automatizado
* Dashboard de monitoramento
* Evolução para plataforma TDM corporativa

---

## **16. Próximos Passos**

* Validar com stakeholders
* Refinar regras de maturação
* Definir stack tecnológica
* Planejar implementação

---

## **17. Observações Finais**

Este documento representa a base inicial da solução e deverá evoluir conforme novos insumos, validações e decisões técnicas forem incorporados.

---

## **Sugestão de Nome do Documento**

**tdm-arquitetura-requisitos-v1.md**


Elaborar e consolidar os requisitos técnicos e funcionais para a construção de uma solução de gestão e maturação de dados de teste (Test Data Management - TDM).

A solução deverá contemplar a ingestão de arquivos batch provenientes da TSYS, o processamento e normalização desses dados por meio de um serviço de ETL em Python, o armazenamento em uma base central de massas e a execução de processos de maturação responsáveis pela atualização e preparação dos dados para uso em testes.

Adicionalmente, a solução deverá permitir a criação ativa de massas de teste por meio da integração com APIs da própria TSYS, possibilitando a geração de dados sob demanda.

O acesso e a manipulação das massas deverão ser realizados via uma API de gerenciamento, garantindo controle, rastreabilidade e padronização no consumo pelo time de QA e automação.