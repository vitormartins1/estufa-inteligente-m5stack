# AWS Iot Core
Informações relacionadas a Things, Shadows, Regras e Tópicos usados no AWS IoT Core.
## Things

- env3
- m5photoperiod
- m5envcontrol
- m5core2

## Shadows

- m5photoperiod-shadow
- m5envcontrol-shadow

## Regras
Bird i if of that and the with repeating my fiend, i a broken into bird that the nothing, whom sought this the there what. I entreating seraphim sad thing mefilled betook core stillness midnight. And that the songs and the streaming be. Soon before stock we seraphim tis above more, as and token have nothing the on hath whispered, the i i grew spoken.

- DynamoDB Rule
- Environment Control Rule

## Tópicos
Como padronização os tópicos irão usar apenas lowercase, números e dashes e seguirão um padrão de nomenclatura do geral ao específico onde os níveis fluam da esquerda para a direita. Também deverão incluir qualquer informação de roteamento relevante em seus níveis.
Tópicos de leitura e feedback de estados possuem o prefixo *'dt/'* indicando que o tópico se refere a dados, enquanto tópicos de comando usam o prefixo *'cmd/'*.
### `cmd/growtron/env3`
Tópico que publica um comando para o dispositivo Env3 realizar uma leitura do sensor e publicar no tópico de dados correspondente.

Exemplo:
```json
{
  "newSensorRead": true
}
```
#### `publish`
- Core2
#### `subscribe`
- Env3
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
- Env3
#### `subscribe`
- Core2
- DynamoDB Rule
- Environment Control Rule
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
- Core2
#### `subscribe`
- M5Switch Fotoperíodo
- DynamoDB Rule
### `cmd/growtron/m5photoperiod/exaustor`
Tópico de comando que publica o estado do exaustor. O dispositivo *M5Photoperiod* se inscreve neste tópico para ligar ou desligar o exaustor de acordo com o comando recebido.

Exemplo:
```json
{
  "exaustor": true
}
```
#### `publish`
- Core2
#### `subscribe`
- M5Switch Fotoperíodo
### `cmd/growtron/m5envcontrol/umidificador`
Tópico de comando que publica o estado do umidificador. O dispositivo *M5EnvControl* se inscreve neste tópico para ligar ou desligar o umidificador de acordo com o comando recebido.

Exemplo:
```json
{
  "umidificador": false
}
```
#### `publish`
- Core2
- Environment Control Rule
#### `subscribe`
- M5Switch Enviroment
### `cmd/growtron/m5envcontrol/ventilador`
Tópico de comando que publica o estado do ventilador. O dispositivo *M5EnvControl* se inscreve neste tópico para ligar ou desligar o ventilador de acordo com o comando recebido.

Exemplo:
```json
{
  "ventilador": true
}
```
#### `publish`
- Core2
- Environment Control Rule
#### `subscribe`
- M5Switch Enviroment
### `dt/growtron/log`

# Documentação

<ol>
<li><a href="01-documentacao-de-contexto.md"> Documentação de Contexto</a></li>
<li><a href="02-especificacao-do-projeto.md"> Especificação do Projeto</a></li>
<li><a href="03-metodologia.md"> Metodologia</a></li>
<li><a href="07-funcionalidades.md"> Funcionalidades</a></li>
<li><a href="04-projeto-de-interface.md"> Projeto de Interface</a></li>
<li><a href="06-template-padrao-da-aplicacao.md"> Template Padrão da Aplicação</a></li>
<li><a href="05-arquitetura-da-solucao.md"> Arquitetura da Solução</a></li>
<li><a href="iot-core.md">AWS IoT Core</a></li>
<li><a href="08-apresentacao-do-projeto.md"> Apresentação do Projeto</a></li>
<li><a href="09-referencias.md"> Referências</a></li>
</ol>