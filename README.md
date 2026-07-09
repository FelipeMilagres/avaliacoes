[Automation] Criação da API de Massas de Teste

ou

[Automation] Criação da API de Gerenciamento de Massas

Objetivo

Como consumidor da plataforma Atena (testes automatizados, testes manuais ou aplicações integradas),

Quero consumir as massas de teste por meio de uma API padronizada,

Para que seja possível localizar, reservar, criar e utilizar massas de teste sem necessidade de acesso direto à base de dados.

Contexto

Com a disponibilização da base de dados e do Maturation Engine, torna-se necessário disponibilizar uma camada de serviços responsável por expor as funcionalidades da plataforma aos consumidores.

A API será o ponto único de interação com as massas de teste, abstraindo a estrutura interna da solução e permitindo que diferentes consumidores utilizem os dados de forma padronizada, segura e escalável.

Além dos testes automatizados, a solução deverá permitir futuras integrações com aplicações internas, ferramentas de apoio, bots e agentes de IA, sem necessidade de acesso direto à base de dados.

Critérios de Aceite
Cenário 1: Consulta de massas
Dado que existam massas cadastradas na plataforma;
Quando um consumidor solicitar uma consulta;
Então a API deverá retornar as massas conforme os filtros informados.
Cenário 2: Disponibilização de massa
Dado que exista uma massa apta para utilização;
Quando um consumidor solicitar uma massa;
Então a API deverá disponibilizar as informações necessárias para utilização nos testes.
Cenário 3: Gerenciamento das massas
Dado que uma operação de criação, atualização ou gerenciamento seja solicitada;
Quando a requisição for recebida;
Então a API deverá encaminhar o processamento conforme as regras da plataforma.
Cenário 4: Abstração da base de dados
Dado que a plataforma possua uma base de dados interna;
Quando os consumidores utilizarem a solução;
Então nenhuma interação deverá ocorrer diretamente com o banco de dados, sendo toda comunicação realizada por meio da API.
Cenário 5: Integração com múltiplos consumidores
Dado que diferentes aplicações consumam as massas de teste;
Quando integrarem com a plataforma;
Então a API deverá disponibilizar interfaces padronizadas para utilização pelos diferentes consumidores.
Cenário 6: Evolução dos serviços
Dado que novas funcionalidades sejam incorporadas à plataforma Atena;
Quando houver necessidade de disponibilizá-las aos consumidores;
Então a API deverá permitir evolução incremental sem impacto nas integrações existentes.
Cenário 7: Rastreabilidade
Dado que uma operação seja executada pela API;
Quando a solicitação for processada;
Então deverão ser registrados eventos suficientes para rastrear as operações realizadas.
Resultado Esperado
Disponibilizar um ponto único de acesso às massas de teste.
Eliminar a necessidade de consultas diretas ao banco de dados.
Padronizar o consumo das massas pela plataforma Atena.
Permitir integração com testes automatizados, testes manuais, aplicações internas, bots e agentes de IA.
Facilitar a evolução da solução por meio de uma camada de serviços desacoplada da persistência dos dados.