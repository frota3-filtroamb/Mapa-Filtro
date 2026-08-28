MAPA DA FILTROAMB

1. Funcionalidades para a Gestão de Frota da Filtroamb
Esse mapa funciona como uma central de comando e socorro rápido para a frota:

Socorro Mecânico Imediato: Se um caminhão quebrar na estrada, a equipe não perde tempo procurando no Google. O mapa mostra as Oficinas Parceiras mais próximas por categoria (Mecânica, Elétrica, Guincho, Borracharia, Tacógrafo, Lavação e Autopeça).

Rastreamento da Frota (via Sascar): O botão "Importar KML Sascar" permite carregar a posição exata dos veículos (no painel vemos que há dados de 246 veículos).

Telemetria dos Veículos: Ao clicar em um caminhão, o mapa exibe dados em tempo real: placa, cidade atual, se a ignição está ligada/desligada, velocidade e até a voltagem da bateria.

Localização das Unidades: Mapeia todas as filiais da Filtroamb (Matriz Araquari, Canoas, Chapecó, Duque de Caxias, etc.) para facilitar a rota entre as bases da empresa.

2. Como o Código Funciona?
O fluxo do sistema funciona em 4 passos simples:

Leitura dos Dados: O código lê a lista de oficinas/unidades e faz o upload dos arquivos da Sascar (arquivo KML com a posição dos caminhões).

Conversão de Coordenadas: Ele pega esses endereços e converte em pontos no mapa (latitude e longitude).

Desenho na Tela (Leaflet): O JavaScript cria os marcadores coloridos na tela de acordo com o tipo de serviço (ex: vermelho para Elétrica, azul para Mecânica).

Filtros e Busca: Quando você digita uma placa na barra de pesquisa ou clica em uma categoria na legenda (ex: "Borracharia"), o código oculta os outros ícones e foca apenas no que você precisa.

3. Como ele foi Construído?
O sistema foi feito usando tecnologias web padrões com o auxílio de bibliotecas prontas:

Estrutura (HTML): Cria a barra lateral de controle (#sidebar), o campo de busca, os botões de importação e o espaço onde o mapa é desenhado (#map).

Estilização (CSS): Define o layout com menu lateral fixo (340px) e o mapa ocupando o restante da tela, além do visual moderno e das cores dos marcadores.

Mapa Interativo (Leaflet.js): Foi utilizada a biblioteca gratuita Leaflet (leaflet.js e leaflet.css), responsável por desenhar o mapa base (OpenStreetMap/Satélite), permitir o zoom e renderizar os pinos.

Ícones (Font-Awesome): Biblioteca de ícones usada para desenhar os símbolos de ferramentas, caminhões, lupas e pastas.

Lógica (JavaScript): Controla a busca de placas, lê o arquivo KML da Sascar, filtra a exibição das oficinas e atualiza os painéis informativos de cada caminhão.
