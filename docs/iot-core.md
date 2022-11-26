# IoT Core

O serviço IoT Core exerce mais que a função  de um broker MQTT, ele possui lógicas de negócio,  regras de roteamento de tópicos, ações de gravação de registros na base de dados e registro de dispositivos e certificados. 

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
    WHEN humi > 70 THEN false
    WHEN humi < 60 THEN true
    ELSE null 
  END as umidificador, 
  CASE true
    WHEN temp >= 29 THEN true
    ELSE false
  END as ventilador
FROM 'dt/growtron/m5env3'
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
#### environmentControlConfigDynamoDBRule 
Grava no DynamoDB as configurações de controle de ambiente do usuário publicadas no tópico `cmd/growtron/m5envcontrol/config`.
```sql
SELECT
  -- todo
  timestamp() as timestamp 
FROM 'cmd/growtron/m5photoperiod/fotoperiodo'
```
#### environmentTimestreamRule
Envia o payload do tópico `dt/growtron/m5env3` para uma table no Timestream.
```sql
SELECT 
  humi AS humidity,
  temp AS temperature
FROM 'dt/growtron/m5env3'
```
#### relayTimestreamRule
Seleciona o quarto nível do tópico `dt/growtron/relay/+/status` como o tipo de rele, o estado do rele e envia para o Timestream.
```sql
SELECT
  CASE topic(4) WHEN 'ventilador' THEN relayStatus END as ventilador,
  CASE topic(4) WHEN 'umidificador' THEN relayStatus END as umidificador,
  CASE topic(4) WHEN 'led' THEN relayStatus END as led
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
|`publish`|`subscribe`|
|:-------:|:---------:|
|m5core2central|m5env3|
### `cmd/growtron/m5env3/limits`
Tópico que publica um comando para o dispositivo *m5env3* atualizar os parâmetros de limites de umidade e temperatura.

Exemplo:
```json
{
  "min_humi": 55,
  "max_humi": 75,
  "max_temp": 31,
}
```
|`publish`|`subscribe`|
|:-------:|:---------:|
|m5core2central|m5env3|
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
|`publish`|`subscribe`|
|:-------:|:---------:|
|m5env3|m5core2central|
||environmentTelemetryIotAnalyticsRule|
||environmentControlRepublishRule|
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
|`publish`|`subscribe`|
|:-------:|:---------:|
|m5core2central|m5photoperiod|
||photoperiodConfigDynamoDBRule|
### `cmd/growtron/m5photoperiod/exaustor`
Tópico de comando que publica o estado do exaustor. O dispositivo *m5photoperiod* se inscreve neste tópico para ligar ou desligar o exaustor de acordo com o comando recebido.

Exemplo:
```json
{
  "exaustor": true
}
```
|`publish`|`subscribe`|
|:-------:|:---------:|
|m5core2central|m5photoperiod|
### `cmd/growtron/m5envcontrol/relay`
Tópico de comando que publica o estado do umidificador e ventilador. O dispositivo *m5envcontrol* se inscreve neste tópico para ligar ou desligar o umidificador ou o ventilador de acordo com o comando recebido.

Exemplo:
```json
{
  "umidificador": false,
  "ventilador": true
}
```
|`publish`|`subscribe`|
|:-------:|:---------:|
|m5core2central|m5envcontrol|
|environmentControlRepublishRule||
### `dt/growtron/relay/+/status`
Tópico usado pelos relés para informar quando houver uma mudança de estado. O nível do tópico com o "+" será o tipo do relé. Os seguintes tipos serão usados:
- dt/growtron/relay/**led**/status
- dt/growtron/relay/**exaustor**/status
- dt/growtron/relay/**umidificador**/status
- dt/growtron/relay/**ventilador**/status
  
Exemplo:
```json
{
  "relayStatus": 1
}
```
|`publish`|`subscribe`|
|:-------:|:---------:|
|m5photoperiod|relayStatusDynamoDBRule|
|m5envcontrol|relayTelemetryIotAnalyticsRule|
# Documentação
<ol>
<li><a href="01-documentacao-de-contexto.md"> Documentação de Contexto</a></li>
<li><a href="02-especificacao-do-projeto.md"> Especificação do Projeto</a></li>
<li><a href="03-metodologia.md"> Metodologia</a></li>
<li><a href="04-projeto-de-interface.md"> Projeto de Interface</a></li>
<li><a href="05-arquitetura-da-solucao.md"> Arquitetura da Solução</a></li>
<li><a href="06-template-padrao-da-aplicacao.md"> Template Padrão da Aplicação</a></li>
<li><a href="07-programacao-de-funcionalidades.md"> Programação de Funcionalidades</a></li>
<li><a href="08-plano-de-testes-de-software.md"> Plano de Testes de Software</a></li>
<li><a href="09-registro-de-testes-de-software.md"> Registro de Testes de Software</a></li>
<li><a href="10-plano-de-testes-de-usabilidade.md"> Plano de Testes de Usabilidade</a></li>
<li><a href="11-registro-de-testes-de-usabilidade.md"> Registro de Testes de Usabilidade</a></li>
<li><a href="12-apresentacao-do-projeto.md"> Apresentação do Projeto</a></li>
<li><a href="13-referencias.md"> Referências</a></li>
<li><a href="iot-core.md">IoT Core</a></li>
</ol>