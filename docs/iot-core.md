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
##### `dt/growtron/m5env3`
##### `cmd/growtron/m5envcontrol/relay`
```sql
SELECT 
  CASE true
    WHEN humi > 70 THEN false
    WHEN humi < 55 THEN true
    ELSE null 
  END as umidificador, 
  CASE true
    WHEN temp >= 29 THEN true
    ELSE false
  END as ventilador
FROM 'dt/growtron/m5env3'
```
#### environmentTelemetryDynamoDBRule
##### `dt/growtron/m5env3`
```sql
SELECT 
  *, 
  timestamp() as timestamp 
FROM 'dt/growtron/m5env3'
```
#### photoperiodConfigDynamoDBRule 
##### `cmd/growtron/m5photoperiod/fotoperiodo`
```sql
SELECT
  concat(inicio.hora, ":", inicio.minuto) AS inicio, 
  concat(fim.hora, ":", fim.minuto) AS fim, 
  timestamp() as timestamp 
FROM 'cmd/growtron/m5photoperiod/fotoperiodo'
```
#### relayStatusDynamoDBRule
##### `dt/growtron/relay/#/status`
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
Tópico de dados que são publicados as leituras do sensor de umidade, temperatura e pressão através do dispositivo *m5env3*.

Exemplo:
```json
{
  "humi": "66.7",
  "pres": "101137",
  "temp": "27.37"
}
```
#### `publish`
- m5env3
#### `subscribe`
- m5core2central
- environmentTelemetryDynamoDBRule
- environmentControlRepublishRule
### `cmd/growtron/m5photoperiod/fotoperiodo`
Tópico de comando que publica a configuração de início e fim do fotoperíodo. O dispositivo *m5photoperiod* que controla o fotoperíodo e o exaustor se inscreve neste tópico para receber e configurar a nova configuração de fotoperíodo.

Exemplo:
```json
{
  "inicio": { "hora":14, "minuto":28},
  "fim": { "hora":14, "minuto":29}
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
- `dt/growtron/relay/led/status`
- `dt/growtron/relay/exaustor/status`
- `dt/growtron/relay/umidificador/status`
- `dt/growtron/relay/ventilador/status`
  
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