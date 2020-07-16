# Integracao-Dados-com-Nuvem

Documentação do procedimento de integração dos dados apresentado no video: ---

1º Na IDE Studio5000 Instalar o EDS do PFC e configurar o tamanho das instâncias.

2º Alocar as variáveis a serem transmitidas na memória alocada para as instâncias do PFC.

3º Na IDE do E!COCKPIT, iniciar um programa novo e configurar a comunicação ETHERNET/IP Adapter através da biblioteca WagoAppEthernetIp_Adapter.library

4º Resgatar as váriaveis transmitidas através dos buffer's alocados para a comunicação ETHERNET/IP Adapter, utilizando a estrutura de Union.

5º Adicionar a biblioteca WagoAppCloud para transmitir as variáveis através do MQTT.

6º Configurar a conexão do PFC com alguma plataforma da Nuvem que tenha MQTT Broker - nesse exemplo utilizamos a plataforma da IBM Cloud - 

7º Validar comunicação MQTT e trabalhar com os dados já transmitidos ao cloud para realizar plotagens gráficas e outros tratamentos.

8º Algumas observações no quesito segurança cibernética: Possibilidade de separar as VLAN do CLP / Configuração de Firewall / VPN através do 3G.
