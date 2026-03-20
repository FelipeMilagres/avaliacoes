Realizar o planejamento técnico e a definição da arquitetura da solução de automação de massas de teste, com base nos insumos levantados na etapa de discovery.

A atividade contempla a consolidação do modelo arquitetural da plataforma de gestão de dados de teste (TDM), incluindo a definição dos principais componentes, fluxos de dados e integrações necessárias para suportar o ciclo completo de geração, maturação e consumo de massas.

Deverá ser considerada a ingestão de dados provenientes de arquivos batch da TSYS, o processamento e normalização via serviço de ETL, o armazenamento em base central de massas e a implementação de uma camada de maturação responsável pela manutenção contínua dos dados, garantindo que estejam sempre consistentes e prontos para uso em testes.

A arquitetura também deve contemplar a criação ativa de massas por meio do consumo das APIs transacionais da TSYS (POST/VR), assegurando aderência ao fluxo produtivo e maior confiabilidade dos dados gerados.

Além disso, deve ser definida uma API de gerenciamento de massas, responsável por disponibilizar acesso padronizado para consulta, criação e manipulação dos dados pelo time de QA e automação.

Como resultado esperado, a solução deve eliminar dependências operacionais manuais, aumentar a eficiência na preparação de cenários de teste e garantir a disponibilidade de massas prontas para uso.