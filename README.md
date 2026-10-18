# Dashboard de Vendas Porsche

Projeto final da DIO: transformar uma planilha de vendas em um dashboard interativo com HTML, CSS e JavaScript, reunidos em um único arquivo.

**Autora:** Ana Virginia Gadelha Coelho Ellery

[Acessar o dashboard](https://anagade-del.github.io/dashboard-vendas-porsche/)

## Perguntas de negócio

| Pergunta | Visualização | Por que foi escolhida |
| --- | --- | --- |
| Como o valor de vendas evolui por mês e ano? | Gráfico Vendas por Período, somando SalesPriceSanitized e excluindo Cancelled | Permite comparar períodos e identificar oscilações nas vendas registradas. |
| Qual vendedor possui o maior valor de vendas? | Card com o nome do líder, valor e quantidade de vendas | Destaca o desempenho comercial por valor vendido. |
| Como as vendas estão distribuídas por status de entrega? | Gráfico de barras com a contagem de DeliveryStatusSanitized | Ajuda a acompanhar entregas e situações pendentes. |
| Quais métodos de pagamento são mais utilizados? | Gráfico de pizza com a contagem de PayMethodSanitized | Mostra a participação de cada modalidade de pagamento. |

Todos os indicadores respondem aos filtros combinados de data inicial, data final, modelo e cidade. O botão **Limpar filtros** restaura a visão geral.

## Indicadores e regras de cálculo

- **Valor total de vendas:** soma de SalesPriceSanitized no recorte selecionado.
- **Vendas registradas:** quantidade de linhas no recorte.
- **Ticket médio:** valor total dividido pela quantidade de vendas.
- **Vendedor em destaque:** maior soma de SalesPriceSanitized por salesperson. Em empate, todos os líderes são apresentados.
- **Vendas por Período:** soma mensal por data da venda; os registros com DeliveryStatusSanitized igual a Cancelled são excluídos somente deste gráfico.
- **Entregas e pagamentos:** quantidade de registros por categoria, e não soma dos valores.

Os cards e os gráficos de entregas e pagamentos incluem todos os status. Por isso, o total do gráfico por período pode ser diferente do card de valor total. Os valores representam vendas registradas, não recebimentos confirmados.

A moeda definida para apresentação é o dólar americano (USD / US$), sem conversão cambial.

## Preparação da base

A fonte é a planilha sanitizada disponibilizada no desafio, com 100 registros de vendas.

1. Na primeira versão recebida, 24 registros apresentavam SaleDateSanitized como INVALID. A autora revisou a base e enviou uma nova versão, utilizada no dashboard final, com as 100 datas válidas. O critério de correção de cada data não foi documentado nesta conversa.
2. As datas armazenadas como números seriais do Excel foram convertidas para o formato ISO (AAAA-MM-DD), permitindo filtros e agrupamentos por mês e ano.
3. SalesPriceSanitized foi convertido para número para permitir somas e médias.
4. Os cálculos utilizam os campos sanitizados correspondentes e o campo salesperson. ModelYearSanitized não é utilizado como data da venda.
5. O campo customer_name foi removido dos dados embutidos no HTML. Os nomes dos vendedores foram mantidos conforme a base do exercício; nomes parecidos não foram unificados sem confirmação.
6. Os dados foram embutidos como valores no HTML, sem dependência das fórmulas do Excel.

## Uso de IA e ferramentas

Foi utilizado um agente de IA no ChatGPT Work (Codex), com skills de análise de planilhas, leitura de PDF e criação de sites. O agente leu o enunciado e a base, gerou o HTML e verificou cálculos e a lógica dos filtros. **O recurso Canvas não foi utilizado nesta implementação.**

A autora definiu as perguntas de negócio, revisou a base, avaliou o dashboard, pediu refinamentos e realizou a publicação pelo GitHub Pages.

## Prompt de criação

A solicitação foi construída em mensagens sucessivas. Abaixo está a consolidação do pedido inicial, preservando seus requisitos:

> Crie um dashboard em HTML, em arquivo único, com filtros de data, modelo e cidade e opção de total geral. Utilize a planilha sanitizada Porsche como fonte e um visual elegante inspirado no site da Porsche. Responda às seguintes perguntas: total de vendas por ano pela soma de SalesPriceSanitized; salesperson com maior valor de vendas em um card; distribuição de DeliveryStatusSanitized em um gráfico; e métodos de pagamento mais utilizados em um gráfico de pizza com PayMethodSanitized. Todos os indicadores devem responder aos filtros.

### Refinamentos até a versão final

Os pedidos seguintes ajustaram o resultado:

1. **Substituir a base:** utilizar a nova versão enviada após a revisão das datas.
2. **Moeda:** “pode colocar a moeda em dólares”.
3. **Visual:** fundo cinza-chumbo, textos em branco e amarelo e valores dos cards em vermelho.
4. **Detalhamento temporal:** trocar a agregação anual por mês e ano e mudar o título para “Vendas por Período”.
5. **Cancelamentos:** excluir os registros cancelados somente do gráfico Vendas por Período.

## Como usar

Abra o [dashboard publicado](https://anagade-del.github.io/dashboard-vendas-porsche/), selecione os filtros e acompanhe as mudanças nos indicadores. O gráfico mensal possui rolagem horizontal para consultar períodos extensos.

Para executar localmente, baixe o arquivo index.html e abra-o em um navegador. Não é necessário instalar dependências nem acessar a internet para executar o arquivo baixado.

## Arquivos do repositório

- **index.html:** dashboard completo, estilos, lógica e dados embutidos.
- **README.md:** documentação das perguntas, preparação dos dados e processo de criação.

## Verificações realizadas

A lógica foi conferida para a quantidade de 100 registros, soma dos valores, datas válidas, filtros combinados, limites inclusivos de data, recortes sem resultados e reconciliação dos totais mensais. Também foi verificada a exclusão dos 7 registros Cancelled somente do gráfico por período.

A autora revisou o visual durante a construção. A conferência final dos filtros no endereço publicado deve ser realizada no navegador antes da submissão.

## Publicação

O código está em um repositório público e a publicação utiliza GitHub Pages a partir da branch principal, na pasta raiz.

- **Dashboard:** https://anagade-del.github.io/dashboard-vendas-porsche/
- **Repositório para entrega na DIO:** https://github.com/anagade-del/dashboard-vendas-porsche

Projeto educacional independente, sem vínculo oficial com a Porsche.
