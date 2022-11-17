# IoT Core
Informações relacionadas a Things, Shadows, Regras e Tópicos usados no AWS IoT Core.
## Things

- m5env3
- m5photoperiod
- m5envcontrol
- m5core2central

## Shadows

- m5photoperiod-shadow
- m5envcontrol-shadow

## Regras
#### environmentControlRepublishRule
Faz verificações na temperatura e umidade recebida pelo tópico `dt/growtron/m5env3` e republica uma mensagem no tópico `cmd/growtron/m5envcontrol/relay` com o comando de ligar ou desligar o ventilador ou o umidificador.
```sql
SELECT 
  CASE true
    WHEN humi > 75 THEN false
    WHEN humi < 55 THEN true
    ELSE null 
  END as umidificador, 
  CASE true
    WHEN temp >= 29 THEN true
    ELSE false
  END as ventilador
FROM 'dt/growtron/m5env3'
```
#### environmentTelemetryIotAnalyticsRule
Insere o timestamp e envia o payload do tópico `dt/growtron/m5env3` para um channel do IoT Analytics.
```sql
SELECT 
  *, 
  timestamp() as timestamp 
FROM 'dt/growtron/m5env3'
```
#### relayTelemetryIotAnalyticsRule
Seleciona o quarto nível do tópico `dt/growtron/relay/#/status` como o alias do estado do rele e o envia junto com o timestamp para um channel do IoT Analytics.
```sql
SELECT
  CASE topic(4)
    WHEN 'ventilador' THEN relayStatus
  END as ventilador,
  CASE topic(4)
    WHEN 'umidificador' THEN relayStatus
  END as umidificador,
  CASE topic(4)
    WHEN 'led' THEN relayStatus
  END as led,
  CASE topic(4)
    WHEN 'exaustor' THEN relayStatus
  END as exaustor,
  timestamp() as timestamp 
FROM 'dt/growtron/relay/+/status'
```
#### photoperiodConfigDynamoDBRule 
Grava no DynamoDB todas as configurações de fotoperíodo publicadas no tópico `cmd/growtron/m5photoperiod/fotoperiodo` usando o timestamp como chave primária.
```sql
SELECT
  concat(inicio.hora, ":", inicio.minuto) AS inicio, 
  concat(fim.hora, ":", fim.minuto) AS fim, 
  timestamp() as timestamp 
FROM 'cmd/growtron/m5photoperiod/fotoperiodo'
```
#### relayStatusDynamoDBRule
Seleciona o quarto nível do tópico `dt/growtron/relay/#/status` como o tipo de rele, o estado do rele e o timestamp e grava no DynamoDB.
```sql
SELECT
  topic(4) as relay_type,
  relayStatus as relay_status, 
  timestamp() as timestamp 
FROM 'dt/growtron/relay/+/status'
```
## Tópicos
Como padronização os tópicos irão usar apenas lowercase, números e dashes e seguirão um padrão de nomenclatura do geral ao específico onde os níveis fluam da esquerda para a direita. Também deverão incluir qualquer informação de roteamento relevante em seus níveis.
Tópicos de leitura e feedback de estados possuem o prefixo *'dt/'* indicando que o tópico se refere a dados, enquanto tópicos de comando usam o prefixo *'cmd/'*.
### `cmd/growtron/m5env3/read`
Tópico que publica um comando para o dispositivo *m5env3* realizar uma leitura do sensor e publicar no tópico de dados correspondente.

Exemplo:
```json
{
  "newSensorRead": true
}
```
#### `publish`
- m5core2central
#### `subscribe`
- m5env3
### `dt/growtron/m5env3`
Tópico de dados que são publicadas as leituras do sensor de umidade, temperatura e pressão através do dispositivo *m5env3*.

Exemplo:
```json
{
  "humi": 66.7,
  "pres": 101137,
  "temp": 27.37
}
```
#### `publish`
- m5env3
#### `subscribe`
- m5core2central
- environmentTelemetryIotAnalyticsRule
- environmentControlRepublishRule
### `cmd/growtron/m5photoperiod/fotoperiodo`
Tópico de comando que publica a configuração de início e fim do fotoperíodo. O dispositivo *m5photoperiod* se inscreve neste tópico para receber e configurar o novo fotoperíodo. A regra *photoperiodConfigDynamoDBRule* se inscreve para registrar a nova configuração numa tabela.

Exemplo:
```json
{
  "inicio": { 
    "hora":6, 
    "minuto":0
  },
  "fim": { 
    "hora":22, 
    "minuto":0
  }
}
```
#### `publish`
- m5core2central
#### `subscribe`
- m5photoperiod
- photoperiodConfigDynamoDBRule
### `cmd/growtron/m5photoperiod/exaustor`
Tópico de comando que publica o estado do exaustor. O dispositivo *m5photoperiod* se inscreve neste tópico para ligar ou desligar o exaustor de acordo com o comando recebido.

Exemplo:
```json
{
  "exaustor": true
}
```
#### `publish`
- m5core2central
#### `subscribe`
- m5photoperiod
### `cmd/growtron/m5envcontrol/relay`
Tópico de comando que publica o estado do umidificador e ventilador. O dispositivo *m5envcontrol* se inscreve neste tópico para ligar ou desligar o umidificador ou o ventilador de acordo com o comando recebido.

Exemplo:
```json
{
  "umidificador": false,
  "ventilador": true
}
```
#### `publish`
- m5core2central
- environmentControlRepublishRule
#### `subscribe`
- m5envcontrol
### `dt/growtron/relay/+/status`
Tópico usado pelos relés para informar quando houver uma mudança de estado. O nível do tópico com o "+" será o tipo do relé. Os seguintes tipos serão usados:
- dt/growtron/relay/**led**/status
- dt/growtron/relay/**exaustor**/status`
- dt/growtron/relay/**umidificador**/status
- dt/growtron/relay/**ventilador**/status
  
Exemplo:
```json
{
  "relayStatus": 1
}
```
#### `publish`
- m5photoperiod
- m5envcontrol
#### `subscribe`
- relayStatusDynamoDBRule
- relayTelemetryIotAnalyticsRule

# Documentação

<ol>
<li><a href="documentacao-de-contexto.md"> Documentação de Contexto</a></li>
<li><a href="especificacao-do-projeto.md"> Especificação do Projeto</a></li>
<li><a href="funcionalidades.md"> Funcionalidades</a></li>
<li><a href="metodologia.md"> Metodologia</a></li>
<li><a href="projeto-de-interface.md"> Projeto de Interface</a></li>
<li><a href="template-padrao-da-aplicacao.md"> Template Padrão da Aplicação</a></li>
<li><a href="arquitetura-da-solucao.md"> Arquitetura da Solução</a></li>
<li><a href="iot-core.md">IoT Core</a></li>
<li><a href="apresentacao-do-projeto.md"> Apresentação do Projeto</a></li>
<li><a href="referencias.md"> Referências</a></li>
</ol>