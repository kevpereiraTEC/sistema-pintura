Projeto: Monitoramento de Processo de Pintura (IoT)
Este projeto monitora um processo de pintura em chão de fábrica usando dois ESP32 (comunicação via ESPNOW) e visualiza os dados em um dashboard (Grafana).

1. Como Montar o Projeto (Hardware)
O projeto usa dois ESP32:

Unidade 1: ESP32 "Chão de Fábrica" (Transmissor)
Este ESP32 lê os sensores do ambiente e envia os dados.

Componentes:
- Sensor Ultrassônico (para nível da tinta).
- Sensor DHT (Temperatura e Umidade).
- Fotorresistor (Luz).
- Sensor PIR (Presença).
- LEDs Verde/Vermelho (para status local).

Unidade 2: ESP32 "Monitoramento" (Receptor/Gateway)
Este ESP32 recebe os dados, exibe localmente e envia para a nuvem.

Componentes:
- Matriz de LEDs (para exibir dados recebidos).
- LEDs Verde/Vermelho (para status da conexão ESPNOW).

2. Como Rodar o Backend (InfluxDB)
Para armazenar os dados, este projeto usa o InfluxDB.

Configure o InfluxDB:
- Crie uma conta (local ou na nuvem).
- Crie um Bucket (ex: fabrica_pintura_db).
- Gere um Token de API e anote-o, juntamente com sua Org ID e URL.
- Configure o Gateway (ESP32 de Monitoramento)

3. Como Consultar os Dados Salvos (Grafana)
Usamos o Grafana para criar os dashboards e visualizar os dados do InfluxDB em tempo real .

Configure o Grafana:
- Acesse sua conta do Grafana (local ou na nuvem).
- Conecte a Fonte de Dados:
- Vá em "Data Sources" (Fontes de Dados) e adicione "InfluxDB".
- Preencha as credenciais do InfluxDB (URL, Bucket, Token) que você anotou anteriormente.
Crie os Dashboards:
- Crie um novo "Dashboard".
- Adicione "Panels" (Gráficos, Medidores, etc.).
- Em cada painel, use o editor de consultas (Query) para buscar os dados do InfluxDB (ex: Nível do Tanque, Temperatura).
- Configure o dashboard para atualizar automaticamente (ex: a cada 5 segundos).
