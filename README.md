# Estufa Inteligente M5stack
 Estufa inteligente com soluções automatizadas de IoT

Um sistema de monitoramento de estufa inteligente que coleta dados de ambiente internos, controla o tempo que as luzes ficam acesas, controla a itensidade da luz de acordo com a temperatura externa e interna usando IoT Analytics, e permite controlar e visualizar todas essas funcionalidades pelo dispositivo M5Stack Core2. Os dados de ambiente interno serão captados com M5Atom e Env3. O Led de cultivo será controla pelos relé do M5Switch. Todos os dispositivos estarão se comunicando via MQTT com a AWS IoT usando tópicos, regras e shadows.

A smart greenhouse monitoring system that collects indoor environment data, controls how long the lights are on, controls the light intensity according to outdoor and indoor temperature using IoT Analytics, and allows you to control and visualize all these functionality from the device M5Stack Core2. Indoor data will be captured with M5Atom and Env3. The grow LED will be controlled by the M5Switch relay. All devices will be communicating via MQTT with AWS IoT using topics, rules and shadows.

# Documentação

<ol>
<li><a href="docs/01-documentacao-de-contexto.md"> Documentação de Contexto</a></li>
<li><a href="docs/02-especificacao-do-projeto.md"> Especificação do Projeto</a></li>
<li><a href="docs/03-metodologia.md"> Metodologia</a></li>
<li><a href="docs/04-projeto-de-interface.md"> Projeto de Interface</a></li>
<li><a href="docs/05-arquitetura-da-solucao.md"> Arquitetura da Solução</a></li>
<li><a href="docs/06-template-padrao-da-aplicacao.md"> Template Padrão da Aplicação</a></li>
<li><a href="docs/07-apresentacao-do-projeto.md"> Apresentação do Projeto</a></li>
<li><a href="docs/08-referencias.md"> Referências</a></li>
</ol>

## Roadmap

- Criar um MVP focado nas funcionadades básicas;
- Focar no aprendizado da AWS durante o processo para expandir o projeto numa próxima etapa;
- Estudar o AWS IoT SDK e avaliar a migração do UIFLOW para o Micropython puro no VSCode;
- Criar um produto final com interface gráfica profissional e funcionalidades de automação condizentes com a necessidade;
- Integrar o produto com os recursos avançados de Analytics da AWS;
- Criar um frontend e um site para hospedar o serviço;
- Documentar o processo e metodologias;

## MVP

### Dispositivos
- Device conectado a um sensor de umidade e temperatura publicando os dados de leitura num tópico periodicamente.
- Dispositivo com RTC e relés para controlar o fotoperíodo e o exaustor.
- Dispositivo com relés para controlar o umidificador e o ventilador.
- Dispositivo com tela e input para monitoramento e gerenciamento. 

### Funcionalidades
- Dispositivo RTC com alarme de inicio e fim do fotoperíodo diariamente.
- Dispositivo RTC com fotoperíodo configurável via tópico.
- Dispositivo de monitoramento deve exibir os dados do sensor de umidade e temperatura em tempo real.
- Dispositivo de monitoramento deve poder selecionar horários de fotoperíodo e enviar a um tópico para configuração do dispositivo com RTC.
- Dispositivo de monitoramento deve controlar o exaustor, ventilador e umidificador.
- Regras para ligar o ventilador e umidificador automaticamente de acordo com os dados do tópico de temperatura e umidade.
- Armazenar os dados de telemetria ambiente no DynamoDB com o timestamp como chave primária.
- Produzir logs de análise e debug com AWS CloudWatch.
- Tratar reconexão de internet em caso de queda e reconexão com a AWS IoT.

## Metodologia

### EDA Event Driven Architecture

O projeto usará EDA como design pattern arquitetural. A comunicação entre os componentes é modelada usando streams de eventos realizando notificações de mudança de estado da aplicação e dos componentes promovendo baixo acoplamento. Eventos são publicados e recebidos por meio de inscrição em determinados eventos por parte dos componentes interessados. De forma que tanto o publisher quanto o subscriber não conheçam a identidade um do outro, ficando está tarefa por contra do broker.

A assincronicidade promovida pelo padrão Event Driven referesse a otimização de tempo, onde não temos bloqueios de recurso para o atendimento das requisições como tradicionalmente ocorre em componentes como comunicação síncrona.

### Cloud-Based Deployment Model

Num modelo de deploy Cloud-based, você pode migrar aplicações existentes para a nuvem, ou você pode projetar e construir novas aplicações na nuvem. Essas aplicações podem ser construídas numa infraestrutura de baixo nível e custo e que requeira que o time de TI a gerencie. Alternativamente você pode construir usando serviços de alto nível quer reduzem o gerenciamento, arquitetamento e escalonamento da infraestrutura central.