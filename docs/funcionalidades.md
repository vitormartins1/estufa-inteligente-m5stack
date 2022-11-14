# Funcionalidades

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