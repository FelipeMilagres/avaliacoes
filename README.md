Cenário 1: Estrutura da base de dados

Dado que a plataforma Atena necessite armazenar as massas de teste do ambiente UAT4;

Quando a solução for implementada;

Então deverá existir uma base de dados capaz de armazenar as informações necessárias para gerenciamento das massas.

Cenário 2: Modelo de dados

Dado que a base de dados será utilizada por diferentes componentes da plataforma;

Quando o modelo de dados for definido;

Então ele deverá suportar a evolução da solução e o armazenamento das informações necessárias para gerenciamento das massas.

Cenário 3: Persistência das informações

Dado que novas informações de massas sejam disponibilizadas para a plataforma;

Quando forem processadas;

Então deverão ser persistidas na base de dados de forma íntegra e consistente.

Cenário 4: Atualização das informações

Dado que uma massa já exista na base de dados;

Quando novas informações forem disponibilizadas para essa mesma massa;

Então a plataforma deverá permitir sua atualização preservando a consistência dos dados.

Cenário 5: Disponibilidade para consumo

Dado que existam massas armazenadas;

Quando os componentes da plataforma necessitarem utilizá-las;

Então as informações deverão estar disponíveis para consumo por meio da camada de serviços da solução.

Cenário 6: Evolução da estrutura

Dado que novos atributos ou tipos de massas sejam incorporados à plataforma;

Quando houver necessidade de evolução do modelo de dados;

Então a estrutura deverá permitir sua expansão sem comprometer as informações existentes.

Cenário 7: Identificação única das massas

Dado que uma massa seja armazenada na plataforma;

Quando for persistida na base de dados;

Então ela deverá possuir informações que permitam sua identificação e gerenciamento ao longo do seu ciclo de vida.

Cenário 8: Sincronização das informações

Dado que novas informações sejam disponibilizadas pelo fornecedor;

Quando forem incorporadas à plataforma;

Então a base de dados deverá refletir o estado mais recente das massas disponibilizadas.

Cenário 9: Rastreabilidade dos dados

Dado que informações sejam inseridas ou atualizadas na base de dados;

Quando essas operações forem executadas;

Então deverá ser possível identificar a origem e o histórico das alterações realizadas.