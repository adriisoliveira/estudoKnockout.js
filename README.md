# estudoKnockout.js
Arquivos de teste do knockout.js

Este projeto contem um teste de funcionalidades do knockout.js

Knockout.js

O que é: uma biblioteca que simplifica a construção de interfaces gráficas dinâmicas com JavaScript, através da utilização do padrão MVVM.
Ela atualiza automaticamente os elementos do seu UI sempre que ocorrem alterações do modelo de dados, ou seja, trabalhando com knockout você vai ter um modelo que vai representar e ações que vão controlar a interface, ele vai proporcionar uma tela onde modificações realizadas no html ou na própria classe viewModel / controler, essa classe vai ter uma ligação direta com a tela, os valores, componentes, comportamento, eventos dos componentes. Ele trabalha no foco da ligação e o controle do comportamento e valores dos componentes com um controle. Ele abrange também pontos como roteamento.
O knockout trabalha focado no bind dos elementos de dela com a viewModel/controler. Voce pode construir UIs dinâmicas e complexas usando facilmente contextos, ou seja, você consegue modularizar a interface, um trecho de código que controla um determinado conjunto de componentes composto de vários contextos e várias viewModels controlando determinados conjuntos da sua página.
Implementação personalizada de bindings para facilitar a reutilização. É através dos binds que conseguimos conectar os elementos da tela com o html.
JavaScript puro, funciona em qualquer navegador.
Via de regra, e ele não depende de nenhuma outra biblioteca com exceção de alguma funcionalidade da aplicação que necessite de uma biblioteca específica.
Pode ser adicionado na aplicação web existentes sem a necessidade de grandes mudanças na arquitetura.
O knockout, muito facilmente, pegamos uma página da aplicação, coloca o knockout, cria n comportamentos na página, e ela funciona nem muita complicação. É uma ferramenta interessante para adicionar uma funcionalidade a uma página determinada, trabalhando com listas, lentes e vários outros, criando uma tela dinâmica e legal.

O que é o JQuery?

O JQuery é um seletor de componentes, para manipular num nível mais baixo, selecionar itens da tela, elementos, pegar elementos específicos, contar elementos filhos, fazer a modificação de algum atributo, aplicar estilo, etc.




Como usar Knockout?

Voce vai colocar uma tag primeiro, no script no html e adicionar uma referencia para o knockout. Basicamente para usar o knockout é necessário referenciar ele o script.
<script type= ‘text/javascript’ src= ‘knockout-3.4.0.js’ ></script>
Ai cria-se uma classe que controla os elementos de tela e aplica-se o blind do knockout nessa tela.
O knockout tem a documentação no knockout.js.com

O que é o MVVM?

É um padrão de projeto, um design pater, que foi criado em 2005, por um dos arquitetos do WPF do .net(um conjunto de componentes/um framework pra interface de aplicações desktop e web, ele tem algo muito parecido ou até avançado que o knockout dos componentes dele).
O mvvm visa estabelecer uma separação de responsabilidades através de uma classe (ViewModel) entre o modelo de objetos (Model) (WebService, API ou similar) e a interface (View) com a qual o usuário interage. O mvvm trabalha entre os dados, repositório ou uma camada que te entregue dados, controlando assim essas informações. O viewModel modifica alguma coisa e a view atualiza e vice versa.
O mvvm é um padrão e o knockout é baseado nesse padrão.

Observables

Observables são objetos observáveis JavaScript que podem notificar os assinantes / observadores sobre mudanças.
Aplicam o design pattern Observer – O padrão de design oberver ele implementa uma forma, da uma diretriz para que se implemente uma estrutura onde objetos observem mudanças em outros objetos (observáveis) e esses observáveis possam notificar os seus observadores quando ocorre uma mudança ou algo que interesse a esses observadores.
O objeto observável vai ter uma lista de observadores, em dado momento, o observador vai ser inscrito na lista de observadores na lista de objetos observáveis. Sempre que tiver uma modificação na lista de observáveis, ele vai percorrer a lista de observadores e vai notificar os objetos observadores que houve uma mudança.
Existem observables comuns como string, int, float, e existem observablos arrays, e também os computed observables.  

Computed Observables

São funções depende pentes de um ou mais observáveis e serão atualizados automaticamente sempre que qualquer uma destas dependências sofrer alterações. São funções que no seu corpo que vão referenciar observables da vm e se qualquer um dos observables sofrerem alterações esse computed observables vai ser reavaliado.
Declaração da compuded observable


Pure Computed Observables

S seu computed observable apenas calcula e retorna um valor (não será modificado o valor de outro observable), baseado em outros observables então o Pure Computed Observable é a melhor escolha, pois ele gerenciará suas dependências e o uso de memória de uma forma mais eficiente.

Computed Observables Automáticos

Se o seu computed observables será usado apenas em sua UI(tela), você deveria cria-lo como uma function javascript, o knockout reconhecerá as dependências existentes e criará um Computed Observable automaticamente.

Binding

O binding do knockout fornece uma maneira concisa e poderosa para conectar os dados do seu view Model com a interface do usuário. Ele é um objeto, ele implementa o desgin parttern obsverver.
Como realizar um binding?
O binding do knockout necessita de dois itens, um Nome que define o tipo de binding e um valor que define a propriedade que será vinculada a ele, ou qualquer expressão de javascript válida.
É declarado dentro do atributo html DATA-BIND e pode ser usado múltiplos bindings para um mesmo elemento.
<elemento data-bind= “nome:valor”></elemento>
Quando você tem mais de um bind para o mesmo elemento você coloca a “virgula” e o próximo bind, para quantos binds forem necessários.
Podem ser feitos binds multiplus de binds diferentes que não tem relação ou que tem relação.
Quando você define um select você tem um binds chamado option0s que tem alguns binds que você define que são utilizados pra geração das opções do select, você define  a lista, o display, você define qual o valor apresentado, quem vai receber o valor da seleção, qual propriedade do objeto vai receber o valor. E tem um bind selected ptions onde você define uma propriedade ou uma lista de objetos e valores que existem nesse bind que está criando a lista de opções e cruza a opções.
Pode usar por exemplo, um bind value, um bind text, um bind css, etc.
No site do knockout define tres tipos de binds:
Texto e Aparência;
Controle de fluxo;
Campos de formulário;
(mais usados)

*attr – atribute


Binding Context

O que?
O binding context é um objeto que contem dados que podem ser referenciados em seus bindings.
Quando ApplyBindings é executado o knockout automaticamente cria e gerencia um bindigns contexte, é o nível mais alto de contextos, representado pelo viewModel, informado em ko.applyBindings (viewModel)
Quando você usa um binding de fluxo de controle, como com foreach, é criado um novo contexto filho, contendo unformações mais específicas que o contexto principal.
Propriedades do Bind Context
$parent – representa o contexto de onde se origina o contexto atual.
$parents- uma coleção com todos os contextos anteriores na hierarquia do contexto. Sendo $parents [o] seu pai deireto e $parents[parents.lenght] o maior contexto na hierarquia.
$root – representa o contexto principal, na mais alta posição da hierarquia, é o objeto passado para ko.applyBindings()
$data  - representa o contexto corrente, acima dele estão os $parents (o contexto que você está trabalhando no momento.
$index – existe apenas no contexto criado pelo binding Foreach, representa a posição do objeto que está sendo manipulado pelo loop no momento (índice de execução do loop da interação que está sendo manipulada pelo foreach)
$element – representa o elemento do DOM que gerou o contexto corrente


Template Bindings

É uma forma de preencher um elemento HTML com um trecho de código (html) reutilizável, alcançando construções de estruturas mais complexas, hierárquicas e de forma modular facilitando sua compreensão, ou seja, quando você redenrizar a estrutura você vai preencher com outro trecho de html.
Existe duas maneiras de utilizar o template Bindgs.
Uma é usando o mecanismo nativo do knockout e outra é usando um mecanismo de terceiros, acoplado a biblioteca.
