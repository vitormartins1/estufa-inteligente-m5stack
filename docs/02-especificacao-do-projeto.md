
# Especificações do Projeto

## Personas

### <span style="color:Green">**`Hector`**

|<img src="https://media.istockphoto.com/id/1347993286/photo/portrait-of-confident-young-professional-smiling-at-camera.jpg?b=1&s=170667a&w=0&k=20&c=bsCkI89m8rxHlsfKwnB1D1Inb2o51bjWMr-WW5xFi5s=">|**Hector** <br> 25 anos   |
|:---------------------------------------:|:-------------------------------:|
|**Ocupação** | Estudante de biologia
|**Motivação** | Manter as plantas utilizadas em suas pesquisas acadêmicas num ambiente estável 
|**Frustrações** | Mora sozinho e durante os dias de estágio não pode monitorar seus objetos de pesquisa|

### <span style="color:Green">**`Ursula`**

|<img src="https://images.pexels.com/photos/1239291/pexels-photo-1239291.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500">|**Ursula** <br> 31 anos   |
|:---------------------------------------:|:-------------------------------:|
|**Ocupação** | Dono de e-commerce de plantas
|**Motivação** | Ser a loja que vende as mudas mais saudáveis do brasil
|**Frustrações** | Muito tempo dedicado em intervenções no ambiente da estufa para atingir a qualidade desejada para seus clientes|

### <span style="color:Green">**`Erick`**

|<img src="https://media.istockphoto.com/id/1354077790/photo/man-working-at-home.jpg?b=1&s=170667a&w=0&k=20&c=OiE7jaLstvprIONAfwPjJFW3hDTPetHceX3JVGnr1T4=">|**Erick** <br> 45 anos   |
|:---------------------------------------:|:-------------------------------:|
|**Ocupação** | Contador
|**Motivação** | Automatizar tarefas e economizar dinheiro
|**Frustrações** | Não consegue cultivar peperômias pois a ambiente de sua casa sempre as deixa murchas|

### <span style="color:Green">**`Olinda`**

|<img src="https://media.istockphoto.com/id/1325192299/photo/young-woman-practicing-breathing-yoga.jpg?b=1&s=170667a&w=0&k=20&c=oIMzRRCroyKae1Gu4iG5bBtxgsiF0vZOktXWvmlP35c=">|**Olinda** <br> 36 anos   |
|:---------------------------------------:|:-------------------------------:|
|**Ocupação** | Atendente de caixa
|**Motivação** | Cuidar da filha 
|**Frustrações** | Não consegue uma colheita de qualidade para extrair o óleo medicinal que sua filha necessita |

### <span style="color:Green">**`Mike Tyson`**

|<img src="https://istoe.com.br/wp-content/uploads/2022/07/mike-tyson.jpg">|**Mike Tyson** <br> 56 anos   |
|:---------------------------------------:|:-------------------------------:|
|**Ocupação** | Ex-pugilista, altualmente no ramo de flores medicinais
|**Motivação** | Expandir seu negócio de flores
|**Frustrações** | Verão extremamente quente e seco da California diminui sua colheita considerávelmente |

### <span style="color:Green">**`Filipe Ret`**

|<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTLNWVbrIyscg-ijbfWZiwHlvln0gBt6l-s--Zo4834dkG2_WSpWtxA-enF5PXGlI9KVJU&usqp=CAU">|**Filipe Ret** <br> 33 anos   |
|:--------------------------:|:-------------:|
|**Ocupação** | Rapper, novo no ramo do agronegócio californiano
|**Motivação** | Oferecer a melhor qualidade para seus clientes
|**Frustrações** | Pouco tempo para gerenciar e garantir um padrão de qualidade para o negócio pois mora no Brasil |

### <span style="color:Green">**`Anitta`**

|<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTsCTAce31_ExqcVtv1Z6EcYO7etIz68aLfKg&usqp=CAU">|**Anitta** <br> 28 anos   |
|:--------------------------:|:-------------:|
|**Ocupação** | Cantora
|**Motivação** | Se conectar mais com a natureza 
|**Frustrações** | Rotina alta de shows impede de dar atenção a seu hobbie de cultivar flores |

## Histórias de Usuários

| EU COMO... `PERSONA`| QUERO/DESEJO ... `O QUE` |PARA `PORQUE`|
|:---------:|:------------:|:---------------:|
| PERSONA |	 |	 |

## Requisitos

As tabelas a seguir apresentam os requisitos funcionais e não funcionais que detalham o escopo do projeto.

### Requisitos Funcionais

Todos os problemas e necessidades que devem ser atendidos e resolvidos pelo software por meio de funções ou serviços são requisitos funcionais. 

A tabela a seguir apresenta os requisitos funcionais do projeto identificados por prioridade e importância no contexto do projeto.

|ID   |Descrição do Requisito| Prioridade |
|:---:|:--------------------:|:----------:|
|RF-01|Ligar e desligar a luz de acordo com o fotoperíodo pré-definido|ALTA|
|RF-02|Oferecer interface para configurar o fotoperíodo|BAIXA|
|RF-03|Ligar ou desligar o ventilador ou umidificador de acordo com limites de temperatura e umidade do ar|MÉDIA|
|RF-04|Oferecer interface para configurar limites de temperatura e umidade do ar|BAIXA|
|RF-05|Oferecer interface para ativar ou desativar a automação do ventilador ou umidificador|BAIXA|
|RF-06|Exibir os dados do sensor de clima ambiente no dispositivo de monitoramento e controle|ALTA|
|RF-07|Gerar gráfico com a relação entre a temperatura, umidade do ar e status dos relés do ventilador, umidificador e luz|BAIXA|
|RF-08|Os dispositivos devem se reconectar ao wi-fi e broker em caso de queda de energia ou perda de sinal|MÉDIA|
|RF-09|Oferecer interface para acionar diretamente o ventilador, umidificador ou exaustor|MÉDIA|



### Requisitos não Funcionais

Requisitos não-funcionais são os requisitos relacionados ao uso da aplicação em termos de desempenho, usabilidade, confiabilidade, segurança, disponibilidade, manutenibilidade e tecnologias envolvidas. 

A tabela a seguir apresenta os requisitos não funcionais identificados por prioridade e importância no contexto do projeto.

|ID  | Descrição do Requisito  |Prioridade |
|:--:|:-----------------------:|:--:|
|RNF-01|Deve usar basic ingest nos tópicos de leitura de sensor para economia de recursos|ALTA|
|RNF-02|Deve usar shadow things para os dispositivos que armazenam estados de botões e relés|ALTA|
|RNF-03|Deve seguir o princípio do mínimo privilégio e cada device apenas tem acesso aos recursos necessários para a execução de seu propósito|MÉDIA|
|RNF-04|Os dispositivos que compõe o sistema devem se comunicar sem fios|ALTA|
|RNF-05|Deve utilizar infraestrutura de nuvem on demand|BAIXA|


## Restrições

As questões que limitam a execução desse projeto e que se configuram como obrigações claras para o desenvolvimento do projeto em questão são apresentadas na tabela a seguir.

|ID| Restrição                                             |
|--|-------------------------------------------------------|
|RE-01|	O projeto MVP deverá ser finalizado até 31/12/2022|

## Diagrama de Casos de Uso

![Diagrama de de Casos de Uso](img/img.png)

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
</ol>