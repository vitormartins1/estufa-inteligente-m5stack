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

## Execução das funcionalidades

<span style="color:red">Pré-requisitos: <a href="2-Especificação do Projeto.md"> Especificação do Projeto</a></span>, <a href="3-Projeto de Interface.md"> Projeto de Interface</a>, <a href="4-Metodologia.md"> Metodologia</a>, <a href="3-Projeto de Interface.md"> Projeto de Interface</a>, <a href="5-Arquitetura da Solução.md"> Arquitetura da Solução</a>

Implementação do sistema descrita por meio dos requisitos funcionais e/ou não funcionais. Deve relacionar os requisitos atendidos com os artefatos criados (código fonte), deverão apresentadas as instruções para acesso e verificação da implementação que deve estar funcional no ambiente de hospedagem.

Por exemplo: a tabela a seguir deverá ser preenchida considerando os artefatos desenvolvidos.

|ID    | Descrição do Requisito  | Artefato(s) produzido(s) |
|------|-----------------------------------------|----|
|RF-001| Permitir que o usuário cadastre tarefas | tarefas.shtml / tarefas.cs / controllertarefas.cs | 
|RF-002| Emitir um relatório de tarefas no mês   | relatorio.shtml |

# Instruções de acesso

Não deixe de informar o link onde a aplicação estiver disponível para acesso (por exemplo: https://adota-pet.herokuapp.com/src/index.html).

Se houver usuário de teste, o login e a senha também deverão ser informados aqui (por exemplo: usuário - admin / senha - admin).

O link e o usuário/senha descritos acima são apenas exemplos de como tais informações deverão ser apresentadas.
