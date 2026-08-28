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

4. Programa utilizado:
Esse código foi desenvolvido direto na plataforma web do OneCompiler, usando o ambiente de testes de HTML, CSS e JavaScript que ele oferece de forma gratuita e online.




DADOS QUE UTILIZEI PARA FAZER O MAPA
------------------------------------------
PDF DE EXPLICAÇÃO DE COMO FUNCIONA A API

[README.pdf](https://github.com/user-attachments/files/31551915/README.pdf)

-----------------------------------------------------------------------------------------------------------------------------------------

📌 Instruções para Conexão da Telemetria no Power BI Desktop
Olá! Para conectar o seu relatório no Power BI aos dados de telemetria da frota em tempo real, siga o passo a passo abaixo:

🛠️ Passo a Passo no Power BI Desktop:
No Power BI Desktop, clique em Obter Dados (Get Data).
Clique na aba Outro no menu da esquerda (ou pesquise por Web na barra do topo).
Selecione a opção Web e clique em Conectar.
No campo URL, cole exatamente o link abaixo:
text

https://sasintegra-filtroamb.onrender.com/api/download?limite=100000&api_key=FiltroAmb_2026_Secreta

Clique em OK.
Na janela de credenciais que abrir, selecione a aba Anônimo (Anonymous) no menu à esquerda e clique em Conectar.
Na janela de visualização:
Clique em Carregar para importar os dados diretamente para o relatório, ou
Clique em Transformar Dados para abrir o Power Query e realizar tratamentos adicionais.
💡 Nota: A chave api_key na URL já realiza a autenticação automática sem a necessidade de digitar usuário e senha.

-----------------------------------------------------------------------------------------------------------------------------------------

POR QUE NÃO DEU CERTO: (UTILIZADO ELICollege)

Pense nisso como a entrada de um clube exclusivo (o site ou API que você quer acessar) e o navegador como o segurança da porta.

O Cenário
Você está no seu computador desenvolvendo um site em http://localhost:3000 (Sua Casa).

Você usa o comando fetch para pedir informações a um servidor em [http://api.exemplo.com](http://api.exemplo.com) (O Clube).

A Regra do Segurança (Política de Mesma Origem)
O navegador tem uma regra rígida de segurança: por padrão, ele não deixa um site pegar dados de outro site a menos que o outro site autorize explicitamente.

Para o navegador, duas origens só são iguais se tiverem exatamente o mesmo Protocolo (http), Domínio (exemplo.com) e Porta (3000). Se mudar qualquer um deles, são considerados "estranhos".

O Diálogo que Causou o Erro
Seu site (Você): Envia uma mensagem para o servidor: "Ei, sou o site localhost:3000, me manda esses dados!"

Navegador (Segurança): O segurança intercepta e diz ao servidor: "Ele está pedindo dados, mas veio de localhost:3000. Você conhece ele?"

Servidor (O Clube): Responde enviando os dados, mas esquece de colocar o crachá de autorização (Access-Control-Allow-Origin).

Navegador (Segurança): Olhou a resposta, não viu o crachá e disse: "Opa! Esse servidor não disse no cabeçalho que localhost:3000 tem permissão de entrar. Bloqueado!"

E aí o navegador lança essa mensagem no seu console:

"Access to fetch has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource."

Como Resolve?
Se a API é sua: Você precisa ir no código do seu servidor e adicionar a permissão (o tal cabeçalho Access-Control-Allow-Origin: * ou liberando o endereço do seu front-end).

Se a API não é sua: Como essa trava é somente do navegador, você não consegue fazer a chamada direto pelo navegador. Você precisará criar um servidor intermediário (proxy) no seu próprio back-end para buscar os dados por você, já que chamadas de servidor para servidor não passam pelo controle do navegador.
