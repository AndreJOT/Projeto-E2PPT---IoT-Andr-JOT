# Projeto-E2PPT---IoT-Andre-JOT
Sistema IoT com ESP32 e Node-RED para controle de potência (0–100%) via potenciômetro, com monitoramento em VM Linux (Oracle Cloud) usando MQTT.

Materiais utilizados:
•	ESP32 WROOM;
•	Protoboard;
•	Cabos;
•	Display OLED;
•	Potenciômetro;
•	2 Push button;

<img width="916" height="497" alt="image" src="https://github.com/user-attachments/assets/0bbce868-ff55-4c5a-8a29-72b89eb01028" />
<img width="459" height="456" alt="image" src="https://github.com/user-attachments/assets/d8784ddb-9109-4775-b33e-c4229a3f421b" />

# Sistema Operacional e Softwares Utilizados
- Servidor Linux 24.04 hospedado no Oracle Cloud.
- ArduinoIDE para codificar o ESP32 (bibliotecas instaladas: PubSubClient, Adafruit GFX Library, Adafruit SSD1306).
- No arquivo XXXX contém instrução de instalação / configuração / scripts: 
•	Banco de Dados MySQL;
•	Servidor Mosquitto (MQTT);
•	NodeRED;

# Acesso ao Node-RED Dashboard:
http://129.153.95.201:1880/ui

# Como funciona o projeto:
O programa desenvolvido tem como objetivo realizar a leitura de um valor analógico por meio de um potenciômetro conectado ao ESP32, onde esse potenciômetro é utilizado para controlar a potência de um motor em porcentagem (0 a 100%). Inicialmente, o sistema estabelece conexão com a rede Wi-Fi e com um servidor MQTT, permitindo a comunicação com aplicações externas, como o Node-RED. A leitura do potenciômetro é feita continuamente, e o valor obtido é tratado para representar a potência aplicada ao motor.
Além disso, o sistema conta com dois botões físicos e um botão virtual via MQTT, que permitem a interação com o usuário. O primeiro botão físico é responsável por ativar ou desativar o modo de “congelamento” do valor, ou seja, ao ser acionado, a potência atual definida pelo potenciômetro é mantida fixa, mesmo que haja variação na posição do componente. Essa mesma função também pode ser controlada remotamente por meio de um comando recebido via MQTT, no qual o envio de 0 pausa o sistema (mantendo o valor congelado) e o envio de 1 retoma o funcionamento normal. Já o segundo botão físico altera o modo de operação entre duas escalas de cálculo (1x ou 2x), influenciando diretamente a sensibilidade do controle da potência do motor. Essa lógica integrada entre controle local e remoto permite maior flexibilidade no ajuste e simula diferentes condições de operação.
Por fim, o valor calculado da potência do motor é exibido em tempo real no display OLED, juntamente com o modo de operação selecionado, proporcionando uma interface visual simples e eficiente. Quando o sistema se encontra em estado de pausa ou com o valor congelado, é exibida a indicação “HOLD” no display, informando claramente ao usuário que não há atualização da leitura. Simultaneamente, esse valor é publicado via protocolo MQTT em um tópico específico, possibilitando que plataformas como o Node-RED recebam os dados e os apresentem em um dashboard. Dessa forma, o sistema integra controle de potência, aquisição de dados, interação com o usuário e comunicação em nuvem, caracterizando uma aplicação completa de Internet das Coisas (IoT).
