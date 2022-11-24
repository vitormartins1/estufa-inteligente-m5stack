# Arquitetura da Solução

Definição de como o software é estruturado em termos dos componentes que fazem parte da solução e do ambiente de hospedagem da aplicação.

### Microsserviços

A solução utiliza arquitetura de microsserviços para ajudar a manter a disponibilidade da aplicação quando um único componente falha. Numa arquitetura de microsserviços, os componentes da aplicação tem fraco acoplamento. Nesse caso, se um componente falhar, os outros componentes continuam o trabalho pois estão se comunicando uns com os outros. 

O acoplamento fraco ajuda a isolar o comportamento de um componente de outros componentes que dependem dele, aumentando a resiliência e a agilidade. Uma alteração ou uma falha em um dos componentes não deve afetar os outros componentes.

### EDA Event Driven Architecture

O projeto usará EDA como design pattern arquitetural. A comunicação entre os componentes é modelada usando streams de eventos realizando notificações de mudança de estado da aplicação e dos componentes promovendo baixo acoplamento. Eventos são publicados e recebidos por meio de inscrição em determinados eventos por parte dos componentes interessados. De forma que tanto o publisher quanto o subscriber não conheçam a identidade um do outro, ficando esta tarefa por contra do broker.

A assincronicidade promovida pelo padrão Event Driven refere-se a otimização de tempo, onde não temos bloqueios de recurso para o atendimento das requisições como tradicionalmente ocorre em componentes como comunicação síncrona.

### Cloud-Based Deployment Model

Num modelo de deploy Cloud-based, você pode migrar aplicações existentes para a nuvem, ou você pode projetar e construir novas aplicações na nuvem. Essas aplicações podem ser construídas numa infraestrutura de baixo nível e custo e que requeira que o time de TI a gerencie. Alternativamente você pode construir usando serviços de alto nível quer reduzem o gerenciamento, arquitetamento e escalonamento da infraestrutura central.

## Diagrama de Arquitetura

O *C4Model* é usado para visualizar a arquitetura de software do sistema. Ele consiste numa técnica de notação gráfica enxuta para modelar a arquitetura de sistemas de software. Bons diagramas de arquitetura de software ajudam na comunicação das equipes de desenvolvimento, integração eficiente de novos colaboradores, análises e avaliações de arquitetura, identificação de riscos e melhorias.

O modelo é uma abordagem de abstrações que reflete como arquitetos e desenvolvedores pensam e constroem o software. Ele possui 4 níveis de abstração dos diagramas: Contexto, Contêiner, Componente e Código. Só é necessário criar os diagramas que gerem valor ao desenvolvimento do software. Nesse projeto usaremos apenas o diagrama de contexto e contêineres que serão suficientes para visualizar com detalhes a arquitetura de software projetada e a comunicação dos componentes entre si. 

### Diagrama de Contexto do Sistema

O diagrama de contexto exibe um quadro geral com pessoas e sistemas de software, em vez de tecnologias, protocolos e outros detalhes de baixo nível.

![Diagrama de Contexto](../out/docs/arquitetura/context/diagrama_arquitetural_contexto.png) 

### Diagrama de Container

O Diagrama de container mostra como as responsabilidades são distribuídas pela arquitetura, as principais opções de tecnologia e como os containers se comunicam entre si. Um container é uma unidade executável ou implantável separadamente que executa código ou armazena dados. 

![Diagrama de Container](../out/docs/arquitetura/container/diagrama_arquitetural_container.png) 

## Projeto da Base de Dados

Descrição das tabelas utilizadas no DynamoDB para armazenar dados de telemetria, configuração e mudanças de status.
### DynamoDB
#### `photoperiod_configuration`
|timestamp|fim|inicio|
|:-------:|:-:|:----:|
|1668368150734|19:0|7:0|
|1668373591323|23:0|5:0|
#### `environment_control_configuration`
|timestamp|max_humi|min_humi|max_temp|
|:-------:|:------:|:------:|:------:|
|1668381579314|70|60|29|
|1668381578564|75|60|29|
|1668381577914|70|55|28|

### Timestream
#### `environment_telemetry`
|estufa|measure_name|time|measure_value::double|measure_value::bigint|
|:----:|:----------:|:--:|:-------------------:|:-------------------:|
|estufa_producao|temperature|2022-11-21 01:38:43.969000000|28.34|-|
|estufa_producao|humidity|2022-11-21 01:38:43.969000000|62.2|-|
|estufa_producao|ventilador|2022-11-21 01:38:43.969000000|-|1|
|estufa_producao|umidificador|2022-11-21 01:38:43.969000000|-|1|
|estufa_producao|luz|2022-11-21 01:38:43.969000000|-|1|

## Tecnologias Utilizadas

Descreva aqui qual(is) tecnologias você vai usar para resolver o seu problema, ou seja, implementar a sua solução. Liste todas as tecnologias envolvidas, linguagens a serem utilizadas, serviços web, frameworks, bibliotecas, IDEs de desenvolvimento, e ferramentas.

Apresente também uma figura explicando como as tecnologias estão relacionadas ou como uma interação do usuário com o sistema vai ser conduzida, por onde ela passa até retornar uma resposta ao usuário.

Nesta seção são apresentados os detalhes técnicos da solução criada pela equipe, tratando dos componentes que fazem parte da solução e do ambiente de hospedagem da solução.

- Descrever serviços AWS utilizados.
- Tecnologias e componentes IoT.
- Tecnologias de segurança.
- Tecnologias de banco de dados.
- Tecnologias de analytics.
- Tecnologias de serviços.

## Componentes
Os componentes que fazem parte da solução apresentados no diagrama de arquitetura são exibidos aqui com mais detalhes e informações referentes a suas funcionalidades.

### Tópicos MQTT

Explicar o principio de funcionamento dos topicos MQTT e como eles se integram aos servicos aws. Linkar referencia a documentacao do iot-core.

### Rule Engine

Explicar o que sao regras e como elas funcionam no contexto do aws iotcore. Linkar referencia a documentacao do iot-core.

### DynamoDB
To but himnot ah and her that deemed and yes a, loved tis might hall in perchance had fondly, aisle who thee been for, his land uncouth superstition rake, in mine flatterers through heartless to paphian. Say known harold for labyrinth it not yet name. Not dome when was not, feere and soon vile this plain girls he companie. Start tis that almost sullen had save. Go dear only or for to land, hight his none knew near he to left for within, weary his but would and amiss.

### Timestream
Raven volume crest i meant metell, thing my have your door lenore door had gloated midnight. Suddenly much nodded the sought stepped heart not a, little pondered and this ominous my a word, more lenore kind eyes whom. And the sitting there fancy tossed throws my tis. But word ever and was, yore days within nevermore i, more before clasp its bosoms thy hath. 

### Dispositivos

#### m5env3
#### m5photoperiod
#### m5envcontrol
#### m5core2central

Dispositivos, módulos e sensores usados no sistema:

| Imagem | Dispositivo | Aplicação | Quantidade |
|--------|-------------|-----------|------------|
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_8078b53c-8d2e-4445-84aa-1ed1d4898874_1200x1200.jpg?v=1654830268"> | M5 Stack Core 2 | Será usado como uma central de controle e monitoramento conectado ao sistema que exibirá dados coletados e poderá definir configurações do sistema | 1 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_2e4a5d8d-c739-405a-9494-431e2edec8ae_1200x1200.jpg?v=1655692121">  | M5 Stack Atom Lite | Leitura do sensor de ambiente e controle dos relés do ventilador e umidificador. | 2 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_879fd0f2-cbe5-45b3-9056-6f3185e7530f_1200x1200.jpg?v=1655692021"> | M5 Stack Atom Matrix | Controle dos relés de fotoperíodo e exaustão. Os leds da matriz são úteis para feedback de status de conexão e alarmes. | 1 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_cf4d6f58-dddd-4a70-8bd5-9628775151ab_1200x1200.jpg?v=1607929895"> | Atom HUB Switch D | Módulos relé para automatizar o fotoperíodo, temperatura e umidade ambiente. | 2 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/4_a60a5e8c-7e5d-4706-9f6e-4c808a6c60e0_1200x1200.jpg?v=1627863922"> | Env3 Unit | Sensor ambiente que faz leituras de temperatura, umidade e pressão atmosférica. | 1 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/4_b690441a-fb9a-455a-b481-ca85aaee8517_1200x1200.jpg?v=1627863925"> | RTC Unit | Relógio de tempo real com um alarme configurável. | 1 |

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