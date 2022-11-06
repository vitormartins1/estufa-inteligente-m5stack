# Arquitetura da Solução

Definição de como o software é estruturado em termos dos componentes que fazem parte da solução e do ambiente de hospedagem da aplicação.

## Diagrama de Arquitetura

O diagrama de arquitetura ilustra graficamente como será a estrutura da arquitetura da solução, e como cada os microsserviços e componentes estarão interligados. 

![Diagrama de Arquitetura](../out/docs/arquitetura/arquitetura/arquitetura.png)

## Modelo ER (Projeto Conceitual)

O Modelo ER representa através de um diagrama como as entidades se relacionam entre si na aplicação interativa. 

## Projeto da Base de Dados

O projeto da base de dados corresponde à representação das entidades e relacionamentos identificadas no Modelo ER, no formato de tabelas, com colunas e chaves primárias/estrangeiras necessárias para representar corretamente as restrições de integridade.
 
Para mais informações, consulte o microfundamento "Modelagem de Dados".

## Tecnologias Utilizadas

Descreva aqui qual(is) tecnologias você vai usar para resolver o seu problema, ou seja, implementar a sua solução. Liste todas as tecnologias envolvidas, linguagens a serem utilizadas, serviços web, frameworks, bibliotecas, IDEs de desenvolvimento, e ferramentas.

Apresente também uma figura explicando como as tecnologias estão relacionadas ou como uma interação do usuário com o sistema vai ser conduzida, por onde ela passa até retornar uma resposta ao usuário.

Nesta seção são apresentados os detalhes técnicos da solução criada pela equipe, tratando dos componentes que fazem parte da solução e do ambiente de hospedagem da solução.

## Diagrama de Componentes
Os componentes que fazem parte da solução são apresentados na Figura abaixo:
 
![Diagrama de Componentes](img.png) 

A solução implementada conta com os seguintes módulos:

- Navegador: Local da interface básica do sistema, onde será processado todos elementos estruturais das páginas requisitadas na Web, tais como: arquivos (HTML, CSS, JavaScript), imagens e vídeos que implementam as funcionalidades do sistema.

- Implantação: Local de armazenamento do código-fonte, onde a aplicação será colocada no ar, ou seja, é disponibilizada para uso, seja em um ambiente de desenvolvimento, de teste ou em produção.

- Hospedagem: local de armazenamento dos arquivos estáticos que compõem as páginas web, requisitadas através dos navegadores. 

- Banco de Dados: Local de armazenamento das informações processadas na aplicação e que retornam as requisições geradas nos navegadores.

## Implantação
O site utiliza a plataforma do Heroku como ambiente de implantação do site do projeto. O site é mantido no ambiente da URL: https://www.heroku.com/home

A publicação do site no Heroku é feita por meio de uma submissão do projeto (push) via Github para o repositório remoto que se encontra no endereço: 
https://git.heroku.com/link_exemplo.git


## Hospedagem
“O Amazon Simple Storage Service (Amazon S3) é um serviço de armazenamento de objetos que oferece escalabilidade, disponibilidade de dados, segurança e performance líderes do setor. Clientes de todos os portes e setores podem armazenar e proteger qualquer quantidade de dados de praticamente qualquer caso de uso, como data lakes, aplicações nativas da nuvem e aplicações móveis. Com classes de armazenamento econômicas e recursos de gerenciamento fáceis de usar, você pode otimizar custos, organizar dados e configurar controles de acesso ajustados para atender a requisitos específicos de negócios, organizacionais e de conformidade”. Fonte: Amazon -  https://aws.amazon.com/pt/s3/


## Banco de Dados
O PostgreSQL trata-se de um SGBD relacional, orientado a objetos, no qual objetos definidos pelo usuário e a abordagem de tabela são combinados para criar estruturas mais complexas de dados. Ele pode lidar com qualquer carga de trabalho, tanto para produtos de máquina única quanto para aplicativos complexos, e apresenta algumas vantagens:

•	Escalável - A escalabilidade vertical é um recurso do PostgreSQL. Como quase todas as soluções de software personalizadas tendem a crescer, resultando na expansão do banco de dados, essa opção oferece suporte ao crescimento e ao desenvolvimento dos negócios muito bem.

•	Suporte para tipos de dados personalizados - O PostgreSQL suporta nativamente um grande número de tipos de dados padrão, como JSON, XML, etc. O PostgreSQL obtém vantagem disso, pois é um dos poucos bancos de dados relacionais que oferece forte suporte para a funcionalidade NoSQL. Além disso, permite que os usuários definam seus próprios tipos de dados. 

•	Ferramentas de terceiros fáceis de integrar - O sistema de gerenciamento de banco de dados PostgreSQL oferece suporte a ferramentas adicionais, tanto gratuitas quanto comerciais. 

•	Código aberto e comunidade - É totalmente de código aberto e apoiado por uma comunidade, o que o fortalece como um ecossistema completo. Além disso, os desenvolvedores sempre podem contar com o suporte rápido e gratuito da comunidade.

## Dispositivos

| Imagem | Dispositivo | Aplicação | Quantidade |
|--------|-------------|-----------|------------|
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_8078b53c-8d2e-4445-84aa-1ed1d4898874_1200x1200.jpg?v=1654830268"> | M5 Stack Core 2 | Será usado como uma central de controle e monitoramento conectado ao sistema que exibirá dados coletados e poderá definir configurações do sistema | 1 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_2e4a5d8d-c739-405a-9494-431e2edec8ae_1200x1200.jpg?v=1655692121">  | M5 Stack Atom Lite | Leitura do sensor de ambiente e controle dos relés do ventilador e umidificador. | 2 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_879fd0f2-cbe5-45b3-9056-6f3185e7530f_1200x1200.jpg?v=1655692021"> | M5 Stack Atom Matrix | Controle dos relés de fotoperíodo e exaustão. Os leds da matriz são úteis para feedback de status de conexão e alarmes. | 1 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/3_cf4d6f58-dddd-4a70-8bd5-9628775151ab_1200x1200.jpg?v=1607929895"> | Atom HUB Switch D | Módulos relé para automatizar o fotoperíodo, temperatura e umidade ambiente. | 2 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/4_a60a5e8c-7e5d-4706-9f6e-4c808a6c60e0_1200x1200.jpg?v=1627863922"> | Env3 Unit | Sensor ambiente que faz leituras de temperatura, umidade e pressão atmosférica. | 1 |
| <img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/products/4_b690441a-fb9a-455a-b481-ca85aaee8517_1200x1200.jpg?v=1627863925"> | RTC Unit | Relógio de tempo real com um alarme configurável. | 1 |