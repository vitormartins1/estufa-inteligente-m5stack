# Estrutura de Tópicos MQTT

### `cmd/growtron/env3`
Tópico que publica um comando para o dispositivo Env3 realizar uma leitura do sensor e publicar no tópico de dados correspondente.

Exemplo:
```json
{
  "newSensorRead": true
}
```
#### `publish`
MQTT Test Client
Core2
#### `subscribe`
Env3
### `dt/growtron/env3`
Tópico de dados que são publicados as leituras do sensor de umidade, temperatura e pressão através do dispositivo *Env3*.

Exemplo:
```json
{
  "humi": "66.7",
  "pres": "101137",
  "temp": "27.37"
}
```
#### `publish`
Env3
#### `subscribe`
Core2
DynamoDB Rule
Environment Control Rule
### `cmd/growtron/m5photoperiod/fotoperiodo`
Tópico de comando que publica a configuração de início e fim do fotoperíodo. O dispositivo *M5Switch* que controla o fotoperíodo e o exaustor se inscreve neste tópico para receber e configurar a nova configuração de fotoperíodo.

Exemplo:
```json
{
  "inicio": { "hora":14, "minuto":28},
  "fim": { "hora":14, "minuto":29}
}
```
#### `publish`
MQTT Test Client
#### `subscribe`
M5Switch Fotoperíodo
DynamoDB Rule
### `cmd/growtron/m5photoperiod/exaustor`
Tópico de comando que publica o estado do exaustor. O dispositivo *M5Photoperiod* se inscreve neste tópico para ligar ou desligar o exaustor de acordo com o comando recebido.

Exemplo:
```json
{
  "exaustor": true
}
```
#### `publish`
MQTT Test Client
Core2
#### `subscribe`
M5Switch Fotoperíodo
### `cmd/growtron/m5envcontrol/umidificador`
Tópico de comando que publica o estado do umidificador. O dispositivo *M5EnvControl* se inscreve neste tópico para ligar ou desligar o umidificador de acordo com o comando recebido.

Exemplo:
```json
{
  "umidificador": false
}
```
#### `publish`
MQTT Test Client
Core2
Environment Control Rule
#### `subscribe`
M5Switch Enviroment
### `cmd/growtron/m5envcontrol/ventilador`
Tópico de comando que publica o estado do ventilador. O dispositivo *M5EnvControl* se inscreve neste tópico para ligar ou desligar o ventilador de acordo com o comando recebido.

Exemplo:
```json
{
  "ventilador": true
}
```
#### `publish`
MQTT Test Client
Core2
Environment Control Rule
#### `subscribe`
M5Switch Enviroment
### `dt/growtron/log`

# Documentação

<ol>
<li><a href="01-documentacao-de-contexto.md"> Documentação de Contexto</a></li>
<li><a href="02-especificacao-do-projeto.md"> Especificação do Projeto</a></li>
<li><a href="03-metodologia.md"> Metodologia</a></li>
<li><a href="04-projeto-de-interface.md"> Projeto de Interface</a></li>
<li><a href="05-arquitetura-da-solucao.md"> Arquitetura da Solução</a></li>
<li><a href="06-template-padrao-da-aplicacao.md"> Template Padrão da Aplicação</a></li>
<li><a href="07-funcionalidades.md"> Funcionalidades</a></li>
<li><a href="estrutura-de-topicos.md"> Estrutura de Tópicos MQTT</a></li>
<li><a href="08-apresentacao-do-projeto.md"> Apresentação do Projeto</a></li>
<li><a href="09-referencias.md"> Referências</a></li>
</ol>