1)	Desafio

Me explica a arquitetura do framework que você montou.

2)	Gestão massa

Na primeira execução ocorreu falha relacionada à massa. Como você resolveria isso em um projeto real?

3)	Explorando os gaps do projeto

No desafio você implementou login válido, inválido e alguns CRUDs básicos. Em produção, que outros cenários você adicionaria?

4)	Contexto vaga

Um cliente possui informações vindas do banco, varejo, Serasa, comportamento de navegação, NPS, histórico de compras e produtos contratados. O sistema gera recomendações como Next Best Action (NBA) e Next Best Offer (NBO).

Como você estruturaria a estratégia de testes para esse produto?

•  O que seria crítico validar?
•  Onde estariam os maiores riscos?" 
•  Você faria somente testes de API?
•  Como dividiria entre unitário, integração e E2E?

5)	Integração entre múltiplos sistemas

O cliente altera renda no aplicativo. Esse dado passa por várias integrações até gerar uma oferta personalizada. Como você validaria esse fluxo?

•  Como validaria se o dado chegou em todos os sistemas? 
•  Como descobriria onde falhou?
•  Como faria rastreabilidade?

6)	Modelo baseado em dados

Como você validaria um modelo baseado em dados?

•  Como automatizaria isso?
•  Como saberia se o modelo piorou depois de uma atualização?

7)	Estatística aplicada ao QA

Quais métricas acompanharia?

8)	Qualidade de regras complexas
Uma regra diz:
Cliente com score >700 + renda >5000 + sem atraso + perfil investimento → oferecer produto X
•  Como você modelaria os testes?
•  Usaria tabela de decisão?
•  Como evitar explosão de cenários?

9)	Eventos

O cliente fez uma compra no varejo Carrefour e isso deveria influenciar uma nova oferta. Como você validaria?

•  Como garantir que o evento foi publicado?
•  Como garantir que foi consumido?
•  Como validaria payload?

10)	Dados inconsistentes

Chega do Serasa score 780, mas internamente o cliente está com score 450. O sistema usa ambos. Como testaria?

11)	Situação critica

O negócio reporta que clientes começaram a receber ofertas erradas após um deploy, mas todos os testes passaram.

•  Qual seria sua investigação? 
•  Quais evidências buscaria?
•  Como descobriria se é dado, regra ou integração?

12)	Na sua visão, qual seria a maior dificuldade de testar um motor de relacionamento como esse?"
