
# Metodologia

A metodologia contempla as definições das ferramentas utilizadas pela equipe tanto para a manutenção dos códigos e dos demais artefatos quanto para a organização do time na execução das tarefas do projeto.

## Controle de Versão

O projeto segue a seguinte convenção para o nome de branches:

- `main`: versão estável já testada e pronta para produção
- `development`: versão de desenvolvimento de novas features do software

Será adotado o modelo trunk-based development para que o projeto sempre seja desenvolvido num estado tal que possa ser passado para produção.

A branch development será uma feature branch e será usada para criação e desenvolvimento de novas features. Quando o desenvolvimento da feature terminar o código será efetivamente mesclado com a main branch e deverá estar pronto para produção.

## Gerenciamento de Projeto

### Processo

Para organização e distribuição de demandas e tarefas do projeto será utilizado o github projects, organizando demandas como issues e histórias de sprints como milestones.

- `Product Backlog`: recebe as tarefas a serem trabalhadas e representa o Product Backlog. Todas as atividades identificadas no decorrer do projeto também devem ser incorporadas a esta lista.
- `To Do`: Representa o backlog da sprint atual.
- `Doing`: Representa uma issue iniciada em progresso.
- `Test`: A issue está sendo testada e tendo sua funcionalidade validada.
- `Done`: Issues que passaram pelos testes e controle de qualidade e estão prontos para ser colocado em produção.
- `Block`: Quando existe algum impedimento para a conclusão da issue.

[Estufa Inteligente MVP Github Project](https://github.com/users/vitormartins1/projects/1)

O projeto adota a seguinte convenção para etiquetas:

- `documentation`: melhorias ou acréscimos à documentação
- `bug`: uma funcionalidade encontra-se com problemas
- `enhancement`: uma funcionalidade precisa ser melhorada
- `feature`: uma nova funcionalidade precisa ser introduzida

### Ferramentas

As ferramentas empregadas no projeto são:

| Tipo | Nome | Link de acesso |
|----------|------------|------------|
| Repositório de código fonte | GitHub | https://github.com/vitormartins1/estufa-inteligente-m5stack |
| Gerenciamento do Projeto | GitHub Projects | https://github.com/users/vitormartins1/projects/1 |
| Diagrama de Arquitetura | C4 Plant UML | https://github.com/plantuml-stdlib/C4-PlantUML
| Edição de Código Fonte | UIFlow Web IDE | https://flow.m5stack.com/ |
| Instalação de Firmware | UIFlow Firmware Burning Tool | http://docs.m5stack.com/en/download
| Banco de Dados | DynamoDB | https://aws.amazon.com/pt/dynamodb/ |
| Broker MQTT | AWS IoT Core | https://aws.amazon.com/pt/iot-core/ |
| Biblioteca Gráfica | LVGL - Light and Versatile Graphics Library | https://lvgl.io/ |

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