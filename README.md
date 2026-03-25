9. Requisitos de Acessibilidade (RA)

Os requisitos de acessibilidade definem os critérios necessários para garantir que a plataforma seja plenamente utilizável por pessoas com deficiência (PcD), em conformidade com as diretrizes internacionais de acessibilidade digital (WCAG 2.1 ou superior).

RA01: Navegação por Teclado

A plataforma deve permitir navegação completa utilizando apenas o teclado, sem dependência de mouse, incluindo:

criação e edição de cenários de teste
navegação entre páginas e dashboards
execução de testes
interação com modais, menus e tabelas

Critério de aceite:
Não deve haver bloqueios ou perda de funcionalidade ao utilizar apenas teclado.

RA02: Ordem de Foco e Navegação

A navegação via teclado deve seguir uma ordem lógica e previsível.

evitar “armadilhas de foco”
garantir foco visível em todos os elementos interativos
respeitar fluxo visual da interface
RA03: Compatibilidade com Leitores de Tela

A plataforma deve ser compatível com leitores de tela, como:

NVDA
VoiceOver

Deve permitir:

leitura correta de labels, botões e campos
anúncio de mudanças de estado
navegação por estrutura semântica (títulos, listas, regiões)
RA04: Estrutura Semântica (HTML/ARIA)

A interface deve utilizar corretamente:

hierarquia de títulos (H1 a H6)
landmarks (nav, main, etc.)
atributos ARIA quando necessário

Objetivo: garantir interpretação correta por tecnologias assistivas.

RA05: Rótulos e Identificação de Campos

Todos os campos de entrada devem possuir:

<label> associado
descrição clara e contextual
mensagens de erro acessíveis
RA06: Feedback e Notificações Acessíveis

Eventos como:

sucesso de ações
erros de validação
atualizações de status

devem ser comunicados via:

ARIA-live regions
mensagens interpretáveis por leitores de tela
RA07: Uso de Cores e Contraste

A interface deve garantir:

contraste mínimo de 4.5:1 (WCAG)
não depender exclusivamente de cores para transmitir informação

Deve haver suporte a:

ícones com rótulos
indicadores visuais alternativos
RA08: Componentes Dinâmicos Acessíveis

Componentes como:

drag-and-drop
modais
tabelas dinâmicas
dashboards

devem possuir:

alternativa via teclado
descrição acessível
controle de foco adequado
RA09: Acessibilidade em Gráficos e Dashboards

Os dashboards devem oferecer:

descrição textual dos dados
tabelas equivalentes aos gráficos
leitura interpretável por leitor de tela
RA10: Editor de Cenários Acessível

O editor de texto deve permitir que leitores de tela anunciem:

posição do cursor
conteúdo digitado
mudanças de contexto
RA11: Atalhos de Teclado Compatíveis

Atalhos da ferramenta não devem conflitar com:

atalhos de leitores de tela
atalhos do sistema operacional
RA12: Tratamento de Itens Impeditivos

Problemas que impeçam uso por PcD devem ser tratados como bloqueadores críticos, como:

campos sem identificação
ações indisponíveis via teclado
ausência de leitura por screen reader