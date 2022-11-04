# estufa-inteligente-m5stack
 Estufa inteligente com soluções automatizadas de IoT

Um sistema de monitoramento de estufa inteligente que coleta dados de ambiente internos, controla o tempo que as luzes ficam acesas, controla a itensidade da luz de acordo com a temperatura externa e interna usando IoT Analytics, e permite controlar e visualizar todas essas funcionalidades pelo dispositivo M5Stack Core2. Os dados de ambiente interno serão captados com M5Atom e Env3. O Led de cultivo será controla pelos relé do M5Switch. Todos os dispositivos estarão se comunicando via MQTT com a AWS IoT usando tópicos, regras e shadows.

A smart greenhouse monitoring system that collects indoor environment data, controls how long the lights are on, controls the light intensity according to outdoor and indoor temperature using IoT Analytics, and allows you to control and visualize all these functionality from the device M5Stack Core2. Indoor data will be captured with M5Atom and Env3. The grow LED will be controlled by the M5Switch relay. All devices will be communicating via MQTT with AWS IoT using topics, rules and shadows.

## Roadmap

- Criar um MVP focado nas funcionadades básicas;
- Focar no aprendizado da AWS durante o processo para expandir o projeto numa próxima etapa;
- Estudar o AWS IoT SDK e avaliar a migração do UIFLOW para o Micropython puro no VSCode;
- Criar um produto final com interface gráfica profissional e funcionalidades de automação condizentes com a necessidade;
- Integrar o produto com os recursos avançados de Analytics da AWS;
- Criar um frontend e um site para hospedar o serviço;
- Documentar o processo e metodologias;

## Funcionalidades MVP

- Device conectado a um sensor de umidade e temperatura publicando os dados de leitura num tópico periodicamente.
- Dispositivo com RTC e relés para controlar o fotoperíodo e o exaustor.
- Alarme de inicio e fim do fotoperíodo diariamente.
- Poder configurar o fotoperíodo.
- Dispositivo com relés para controlar o umidificador e o ventilador.
- Dispositivo com tela e input para monitoramento e gerenciamento. 
- Dispositivo de monitoramento deve receber os dados do sensor de umidade e temperatura do tópico correspondente e exibir na tela.
- Dispositivo com tela e input deve poder selecionar horários de fotoperíodo e enviar a um tópico para configuração do dispositivo com RTC.
- Dispositivo com tela e input deve controlar o exaustor, ventilador e umidificador.
- Regras para ligar o ventilador e umidificador automaticamente de acordo com os dados de temperatura e umidade.
- Armazenar os dados de telemetria ambiente no DynamoDB com o timestamp como chave primária.
- Tratar reconexão de internet em caso de queda e reconexão com a AWS IoT.

## Metodologia

EDA Event Driven Architecture

O projeto usará EDA como design pattern arquitetural. A comunicação entre os componentes é modelada usando streams de eventos realizando notificações de mudança de estado da aplicação e dos componentes promovendo baixo acoplamento. Eventos são publicados e recebidos por meio de inscrição em determinados eventos por parte dos componentes interessados. De forma que tanto o publisher quanto o subscriber não conheçam a identidade um do outro, ficando está tarefa por contra do broker.

A assincronicidade promovida pelo padrão Event Driven referesse a otimização de tempo, onde não temos bloqueios de recurso para o atendimento das requisições como tradicionalmente ocorre em componentes como comunicação síncrona.