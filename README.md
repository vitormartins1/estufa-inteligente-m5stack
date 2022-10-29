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