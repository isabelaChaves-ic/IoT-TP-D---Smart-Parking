# IoT TP D - Smart Parking

## Descrição

Este projeto implementa um sistema de estacionamento inteligente baseado em IoT (Internet das Coisas), usando o sensor ultrassônico HC-SR04 e o microcontrolador ESP32 para monitorar a ocupação das vagas de estacionamento. O sistema é implementado em Node-RED e utiliza o InfluxDB para persistir dados de motoristas, ocupação de vagas e pagamentos.

### Funcionalidades

1. **Monitoramento em tempo real:** O sistema permite verificar a disponibilidade das vagas no estacionamento, com atualizações instantâneas via dashboard.
2. **Cadastro de motoristas:** O motorista preenche um formulário com seus dados (nome, modelo do veículo, idade, sexo, setor, vaga e valor pago), e os dados são registrados no InfluxDB.
3. **Integração com sensores:** Através do sensor HC-SR04, a ocupação das vagas é detectada automaticamente. O sistema reconhece quando a vaga está ocupada ou livre, atualizando o estado da vaga em tempo real.
4. **Alerta de lotação máxima:** Se todas as vagas de um setor estiverem ocupadas, o sistema emite um alerta.
5. **Histórico de eventos:** Todos os eventos relacionados à ocupação das vagas são registrados no histórico, que pode ser visualizado no dashboard.

### Arquitetura

O projeto é composto pelos seguintes componentes:

- **ESP32** com sensor HC-SR04: Detecta a ocupação das vagas.
- **Node-RED**: Gerencia o fluxo de dados entre o ESP32 e o banco de dados.
- **InfluxDB**: Armazena dados de motoristas e ocupação de vagas.
- **MQTT**: Protocolo de comunicação entre o ESP32 e o Node-RED.
- **Dashboard**: Exibe as informações sobre as vagas e o histórico em tempo real.

### Tecnologias

- **Node-RED**: Plataforma para automação de fluxos de dados e integração de sistemas.
- **InfluxDB**: Banco de dados time-series para armazenar dados de sensores.
- **MQTT**: Protocolo de mensagens para comunicação entre o ESP32 e o servidor.
- **HC-SR04**: Sensor ultrassônico para detectar a presença de veículos nas vagas.
- **ESP32**: Microcontrolador usado para simular os sensores de presença.

### Fluxo de Dados

1. **Entrada do motorista**: Quando um motorista chega, ele preenche um formulário no dashboard. O sistema verifica se a vaga está ocupada, e se estiver livre, registra os dados do motorista no InfluxDB.
2. **Atualização automática**: O ESP32 publica no MQTT quando uma vaga é liberada, e o Node-RED atualiza automaticamente o estado da vaga no dashboard.
3. **Histórico de eventos**: Cada evento de ocupação ou liberação de vaga é registrado no histórico e exibido no dashboard.

### Sensor HC-SR04 e Critérios de Ocupação

- O sensor HC-SR04 utiliza ondas ultrassônicas para medir a distância entre o sensor e o veículo.
- **Critério de ocupação**: A vaga é considerada ocupada se a distância for menor que 15 cm, e livre caso contrário.

### Estrutura do InfluxDB

- **Measurement**: motoristas
- **Tags**: nome, sexo, modelo, setor, vaga
- **Fields**: idade, valorPago
- **Timestamp**: horário da entrada

### Como Usar

1. **Configuração do ESP32**:
    - Conecte o ESP32 à sua rede Wi-Fi.
    - Faça a comunicação MQTT com o broker (broker.emqx.io).
    - Implemente o código para coletar dados do sensor HC-SR04 e enviar para o Node-RED via MQTT.

2. **Configuração do Node-RED**:
    - Importe o fluxo de Node-RED do projeto.
    - Conecte o Node-RED ao seu banco InfluxDB.
    - Crie as visualizações no dashboard para monitorar o estado das vagas.

3. **Dashboard**:
    - Use o painel para preencher os dados do motorista e acompanhar a disponibilidade das vagas.


## Equipe

- **Membros da Equipe:**
  - Nome: Isabela Chaves Pedroso | Número do Aluno: m321970
  - Nome: Ruth da Silva Mendonça | Número do Aluno: m321979


