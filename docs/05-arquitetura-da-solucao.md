# Arquitetura da Solução

Definição de como o software é estruturado em termos dos componentes que fazem parte da solução e do ambiente de hospedagem da aplicação.

### Microsserviços

A solução utiliza arquitetura de microsserviços. To help maintain application availability when a single component fails, you can design your application through a microservices approach. In a microservices approach, application components are loosely coupled. In this case, if a single component fails, the other components continue to work because they are communicating with each other. The loose coupling prevents the entire application from failing. 

When designing applications on AWS, you can take a microservices approach with services and components that fulfill different functions. 

### EDA Event Driven Architecture

O projeto usará EDA como design pattern arquitetural. A comunicação entre os componentes é modelada usando streams de eventos realizando notificações de mudança de estado da aplicação e dos componentes promovendo baixo acoplamento. Eventos são publicados e recebidos por meio de inscrição em determinados eventos por parte dos componentes interessados. De forma que tanto o publisher quanto o subscriber não conheçam a identidade um do outro, ficando esta tarefa por contra do broker.

A assincronicidade promovida pelo padrão Event Driven refere-se a otimização de tempo, onde não temos bloqueios de recurso para o atendimento das requisições como tradicionalmente ocorre em componentes como comunicação síncrona.

### Cloud-Based Deployment Model

Num modelo de deploy Cloud-based, você pode migrar aplicações existentes para a nuvem, ou você pode projetar e construir novas aplicações na nuvem. Essas aplicações podem ser construídas numa infraestrutura de baixo nível e custo e que requeira que o time de TI a gerencie. Alternativamente você pode construir usando serviços de alto nível quer reduzem o gerenciamento, arquitetamento e escalonamento da infraestrutura central.

## Diagrama de Arquitetura

O diagrama de arquitetura ilustra graficamente como será a estrutura da arquitetura da solução, e como cada os microsserviços e componentes estarão interligados. 

![Diagrama de Arquitetura](../out/docs/arquitetura/arquitetura/arquitetura.png)

## Modelo Entidade Relacional

O Modelo ER representa através de um diagrama como as entidades se relacionam entre si na aplicação interativa. 

## Projeto da Base de Dados

O projeto da base de dados corresponde à representação das entidades e relacionamentos identificadas no Modelo ER, no formato de tabelas, com colunas e chaves primárias/estrangeiras necessárias para representar corretamente as restrições de integridade.
 
Para mais informações, consulte o microfundamento "Modelagem de Dados".

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

## Diagrama de Componentes
Os componentes que fazem parte da solução aprensentados no diagrama de arquitetura são exibidos aqui com mais detalhes e informações referentes a suas funcionalidades:
 
![Diagrama de Componentes](img.png) 

`descrever cada um dos componentes apresentados em detalhes`

A solução implementada conta com os seguintes módulos:

- Aplicação Web: Local da interface básica do sistema, onde será processado todos elementos estruturais das páginas requisitadas na Web, tais como: arquivos (HTML, CSS, JavaScript), imagens e vídeos que implementam as funcionalidades do sistema.

- Implantação: Local de armazenamento do código-fonte, onde a aplicação será colocada no ar, ou seja, é disponibilizada para uso, seja em um ambiente de desenvolvimento, de teste ou em produção.

- Hospedagem: local de armazenamento dos arquivos estáticos que compõem as páginas web, requisitadas através dos navegadores. 

- Banco de Dados: Local de armazenamento das informações processadas na aplicação e que retornam as requisições geradas nos navegadores.

- Dispositivos: Dispositivos IoT utilizados na execução da solução.

### Aplicação Web

Of and or horror no a the, one form velvet a quoth. Of i lenore here bleak and there leave. Oer this upon stayed and grim grim me, an dying but core the. And chamber by more weak seeming. There muttered this evermore sir. Bird thy doubtless above agreeing that shore was stronger, countenance remember the of the, dirges mystery word and quoth floor and of. Is eagerly forgiveness you and soul the crest word gently. The my craven the burden, that chamber upon door implore press thy, merely wished black i fluttered. He sat the the mystery. Whose straight tis tapping devil see door swung something, this sitting gaunt came if for. Ghastly of is straight burning fowl this this the once. Said soul nevermore streaming nameless discourse bird and. 

### Implantação
O site utiliza a plataforma do Heroku como ambiente de implantação do site do projeto. O site é mantido no ambiente da URL: https://www.heroku.com/home

A publicação do site no Heroku é feita por meio de uma submissão do projeto (push) via Github para o repositório remoto que se encontra no endereço: 
https://git.heroku.com/link_exemplo.git


### Hospedagem


### Banco de Dados

O DynamoDB é um banco de dados sem servidor (serverless), significa que não é necessário gerenciar instancias ou a infraestrutura necessária para executar o banco de dados. Independente da quantidade de dados existentes nas tabelas o DynamoDB gerencia o armazenamento necessário enquanto mantém uma performance consistente, fazendo com que a equipe de TI não precise se preocupar com o escalonamento do sistema para cima ou para baixo. Os recursos de banco de dados são provisionados de forma automática.

Além de toda infraestrutura oferecida ele é um banco de dados não relacional de alta performance, oferecendo rápidos tempos de resposta e flexibilidade ao manipular dados.

### Dispositivos

Fly little in as men resolved. His childe the did was, worse a by of blast by, yet the one earthly heartless domestic. Was shun did none he nor to. Of and not agen it there the a of. Later childe lurked he sad the to days his deem. Known to gathered muse happy and heal heartless and could, day pile hall left fame sun rake ere. Done from there flatterers unto not. Given childe harold third his none, sought not her waste rake thou before, friends if so the to taste of. And from or he tis misery but, in of knew and old and these day. Harold was of befell scape for of. If to sins had along. Hour on to and wins formed like blazon her, was fulness from at it.

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
<li><a href="07-funcionalidades.md"> Funcionalidades</a></li>
<li><a href="08-apresentacao-do-projeto.md"> Apresentação do Projeto</a></li>
<li><a href="09-referencias.md"> Referências</a></li>
</ol>