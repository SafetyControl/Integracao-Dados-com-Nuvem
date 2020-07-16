# Integracao-Dados-com-Nuvem

Documentação do procedimento de integração dos dados apresentado no video: ---

# 1º Na IDE Studio5000 Instalar o EDS e configurar o tamanho das instâncias.
  
  - O arquivo para a instalação é o WagoAppEthrenetIp_Adapter.eds.
  
  - Após EDS ser instalado, configuramos um novo módulo na rede Ethernet, ele estará descrito como: WAGO 2759-101 EN/IP:
  ![ScreenShot](https://i.postimg.cc/Xq8nfZWj/PFC-adicionado.jpg)
      - Damos um nome para o módulo.
      - Indicamos o seu endereço de IP.
      - E em module Definition falamos os tamanhos das memórias de entradas e saídas que serão alocadas para o módulo:
  ![ScreenShot](https://i.postimg.cc/zvh3hwD9/Configurando-tamaho-de-mem-rias.jpg)

# 2º Alocar as variáveis a serem transmitidas na memória alocada para as instâncias do PFC.

  - Como a maioria das variáveis são do tipo REAL, declaramos as memórias já como reais.
  - Para as primeiras memórias serão passadas as variáveis do tipo REAL, e por último as variáveis INT e BOOLEAN:
  ![ScreenShot](https://i.postimg.cc/gkq8Bdd1/Transimitindo-vari-veis.jpg)
  
  -Para a transmissão das váriaveis booleanas uma váriavel auxiliar #sinaisdigitais: SINT[4] # foi criada para receber os bit e poder ser transmitida utilizando a última memória que sobrou do alocamento feito:
  ![ScreenShot](https://i.postimg.cc/CLmdqKwM/VarAux.jpg)
  
# 3º Na IDE do E!COCKPIT, iniciar um programa novo para configurar a comunicação ETHERNET/IP Adapter através da biblioteca WagoAppEthernetIp_Adapter.library
  - Para adicionar a biblioteca basta ir em Library Manager e selecionar Add Library:
  ![ScreenShot](https://i.postimg.cc/52X9QqPp/Adicionando-Library.jpg)
  
  
# 4º Resgatar as váriaveis transmitidas através dos buffer's alocados para a comunicação ETHERNET/IP Adapter, utilizando a estrutura de Union.
  
  - A estrutura de Unions permite utilizarmos um mesmo espaço de memória para representar os valores em diferentes tipos de variáveis (REAL / INT / BYTE):
  ![ScreenShot](https://i.postimg.cc/gj1SSpWx/Estrutura-Union.jpg)
  
  - Recebendo variáveis do bloco Adapter e enviando para variáveis globais nomeadas:
  ![ScreenShot](https://i.postimg.cc/vmyjwG69/Recebendo-Variaveis.jpg)

# 5º Adicionar a biblioteca WagoAppCloud para transmitir as variáveis através do MQTT.

  - Aqui é o mesmo procedimento que realizamos com a biblioteca EthernetIP_Adapter:
  ![Screenshot](https://i.postimg.cc/52X9QqPp/Adicionando-Library.jpg)
  
  - Criar uma nova rotina para transmitir as variáveis globais através do MQTT:
  ![ScreenShot](https://i.postimg.cc/QdbWHNVh/Routine.jpg)

# 6º Configurar a conexão do PFC com alguma plataforma da Nuvem que tenha MQTT Broker - nesse exemplo utilizamos a plataforma da IBM Cloud - 

[![Criando-Recurso-Plataforma-IBM.jpg](https://i.postimg.cc/VN8Dckpw/Criando-Recurso-Plataforma-IBM.jpg)](https://postimg.cc/9DLGdCcg)
- Os procedimentos para criar a conexão com o Cloud da IBM estarão no arquivo # e!C_ApplicationNote_Cloud Connectivity.pdf #

- Após configurar um dispositivo na IBM Cloud, configure os parâmetros gerados pela plataforma na página Web do PFC:

7º Validar comunicação MQTT e trabalhar com os dados já transmitidos ao cloud para realizar plotagens gráficas e outros tratamentos.

8º Algumas observações no quesito segurança cibernética: Possibilidade de separar as VLAN do CLP / Configuração de Firewall / VPN através do 3G.
