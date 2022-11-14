# Estufa Inteligente M5Stack
 Estufa inteligente com soluções automatizadas de IoT.

O projeto consiste num sistema de monitoramento de estufa inteligente que coleta dados de ambiente internos, controla o tempo que as luzes ficam acesas, controla a intensidade da luz de acordo com a temperatura externa e interna, criando um ambiente ideal para as plantas usando IoT Analytics. Permite controlar e visualizar todas essas funcionalidades pelo dispositivo de controle e monitoramento M5Stack Core2. Os dados de ambiente interno serão captados com M5Atom e Env3 e armazenados no DynamoDB para processamento posterior pelos serviços de analytics. O Led de cultivo será controlado pelos relés do M5Switch de acordo com o horário de ligar/desligar configurados. Todos os dispositivos estarão se comunicando via MQTT com a AWS IoT usando tópicos, regras e shadows quando aplicável.

## Instruções de utilização

Assim que a primeira versão do sistema estiver disponível, deverá complementar com as instruções de utilização. Descreva como instalar eventuais dependências e como executar a aplicação.

Não deixe de informar o link onde a aplicação estiver disponível para acesso.

Se houver usuário de teste, o login e a senha também deverão ser informados aqui (por exemplo: usuário - admin / senha - admin).

O link e o usuário/senha descritos acima são apenas exemplos de como tais informações deverão ser apresentadas.

# Documentação

<ol>
<li><a href="docs/documentacao-de-contexto.md"> Documentação de Contexto</a></li>
<li><a href="docs/especificacao-do-projeto.md"> Especificação do Projeto</a></li>
<li><a href="docs/funcionalidades.md"> Funcionalidades</a></li>
<li><a href="docs/metodologia.md"> Metodologia</a></li>
<li><a href="docs/projeto-de-interface.md"> Projeto de Interface</a></li>
<li><a href="docs/template-padrao-da-aplicacao.md"> Template Padrão da Aplicação</a></li>
<li><a href="docs/arquitetura-da-solucao.md"> Arquitetura da Solução</a></li>
<li><a href="docs/iot-core.md">IoT Core</a></li>
<li><a href="docs/apresentacao-do-projeto.md"> Apresentação do Projeto</a></li>
<li><a href="docs/referencias.md"> Referências</a></li>
</ol>

# Código

<li><a href="src/"> Código Fonte</a></li>
<li><a href="src/README.md"> Instruções de utilização</a></li>

# Apresentação

<li><a href="presentation/README.md"> Apresentação da solução</a></li>
