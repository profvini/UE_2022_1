SISTEMA DE DIÁLOGO  
O sistema de diálogo para desenvolvimento da narrativa está estruturado em três pilares básicos: 1) a existência de um AIController (aqui denominado “DialogAIController”) para intermediar e gerir a interação entre as Behavior Tree de cada NPC e as escolhas de diálogo do jogador; 2) a existência de um componente de diálogo (aqui denominado “Dialog Component”) que identifica quais objetos na cena são interagíveis para diálogo; e 3) a existência de widgets (aqui denominados “DialogWidget” e “DialogEntryWidget) que aparecerão na tela como forma do jogador ler os diálogos e escolher respostas.

![TELA 01 - 3 PILARES](https://user-images.githubusercontent.com/101642150/166317490-8b6b8d31-90c2-4520-a127-bfac093ab1a4.PNG)

Além disso, para que o diálogo seja iniciado, existe uma Blueprint Interface (aqui denominada “Interaction Interface”) que ajuda a disparar o evento de interação desejado para o diálogo.

![TELA 02 - INTERACTION INTERFACE](https://user-images.githubusercontent.com/101642150/166318839-2335a396-16cf-4b36-bd8d-e4c6a22347e1.PNG)

Porém, antes de entrarmos no funcionamento em si do diálogo, precisamos ver a maneira pela qual esse sistema é identificado/ativado pelo jogador. E isso ocorre na blueprint “FirstPersonCharacter”. Tudo se inicia com uma linha constante (“LineTracebyChanel”) que verifica o que está em frente ao jogador. E a identificação do que está em frente ocorre por Tags colocadas em cada objeto do cenário com o qual se deseja que o jogador interaja. Aqui foi utilizada a tag “Dialog”.

![TELA 03 - TAG DE DIALOGO](https://user-images.githubusercontent.com/101642150/166318919-3a0a70e2-552f-4cea-9575-5b3b9ad85bd1.PNG)

Caso identificada pela linha constante a existência de um objeto com a tag desejada, o programa também verifica se uma variável bool permite a criação de um widget que convidará o jogador a interagir com o objeto. Essa variável bool (“Em Dialogo Block Widget Interagir”) serve para que a tecla de convite de interação não apareça caso um diálogo já esteja em andamento. Caso esteja tudo certo, o programa comanda a criação do widget de convite de interação, coloca ele na tela e transforma em positivo uma variável bool aqui denominada “Linha Interaction”, que se baseia na Tag “Dialog” para atestar que o tipo de interação disponível em frente ao jogador é uma de diálogo em vez de outras possíveis dentro do jogo.

![TELA 04 - TRACELINE E WIDGET CONVITE INTERAGIR](https://user-images.githubusercontent.com/101642150/166318959-f7628bf2-42fe-43af-9953-9de0f1bd7e6f.PNG)

Assim, o jogador está pronto para interagir. Caso ele aperte a tecla de interação, ainda dentro da blueprint “FirstPersonCharacter”, o programa vai checar se a variável bool “Linha Interaction” é verdadeira. Em seguida, transformará ela em falsa e mexerá na variável “Em Dialogo Block Widget Interagir” (vista anteriormente) para que nada interfira no diálogo que está por vir. Em seguida, o widget de interação é removido da tela.

![TELA 05 - Preparo interacao](https://user-images.githubusercontent.com/101642150/166319010-9d356799-34dd-46f5-a286-447353eeae0e.PNG)

O próximo passo acaba sendo o envio para o Interaction Interface das informações para o início do diálogo com o evento On Interaction., que funciona dentro da blueprint do DialogComponent.

![TELA 06 - Inicio Evento OnInteract](https://user-images.githubusercontent.com/101642150/166319060-2fa07107-9e6d-4755-b9f5-4259e7877140.PNG)

Como tal evento funciona dentro da blueprint do DialogComponent, vejamos como essa blueprint está estruturada. Primeiro, ela cria o DialogAIController em uma determinada posição no início do jogo com um evento Begin Play.

![TELA 07 - DialogComponent Begin Play](https://user-images.githubusercontent.com/101642150/166319101-f25f7ad9-c40e-4beb-bbd6-825a298449f3.PNG)

Depois entramos no chamado “Event On Interaction”, que é a maneira do DialogComponent controlar a aparição dos widgets para o funcionamento do diálogo. Assim, no evento de interação os widgets aparecem e comandam o início da BehaviorTree através de sua respectiva BlackBoard.

![TELA 08 - Inicio OnInteraction](https://user-images.githubusercontent.com/101642150/166319144-42487990-3bed-43a9-9c1c-54b388fd932b.PNG)
![TELA 09 - Inicio BehaviorTree](https://user-images.githubusercontent.com/101642150/166319162-a1479788-01ad-4e1c-8f65-ecdec0b9a7f0.PNG)

A Behavior Tree utilizada pelo NPC é determinada através do componente colocado no objeto, dentre aquelas previamente criadas e vinculadas a uma BlackBoard (que comanda como um cérebro um conjunto de diferentes Behavior Trees).

![TELA 10 - ESCOLHA BehaviorTree](https://user-images.githubusercontent.com/101642150/166319216-6138e048-5a44-4a66-8dff-f025748503f8.PNG)

Antes de passarmos para a Behavior Tree, no entanto, precisamos ver o encerramento dos diálogos, que também se encontra dentro do DialogComponent. Na chamada do evento de saída do diálogo, há o retorno para o modo padrão de jogo e o comando de parada da lógica comandada pelo AIController.

![TELA 11 - Evento Exit DialogComponent](https://user-images.githubusercontent.com/101642150/166319268-bf5dd1dc-f772-41f7-b3c9-cbb2cf5b37f0.PNG)

Na sequência na mesma blueprint, após se parar a lógica, há a remoção do widget de diálogo da tela e a liberação do bloqueio de interação através da variável bool “Em Dialogo Block Widget Interagir”.

![TELA 12 - Evento Exit Parte Final](https://user-images.githubusercontent.com/101642150/166319312-9934bda2-8818-43d9-8674-79523b4b4692.PNG)

Assim, estaria encerrada a interação de diálogo. Mas como ela de fato ocorre enquanto está sendo executada? Para isso ainda precisamos ver o funcionamento dos widget e das behavior tree. Começaremos pelo já referido “Dialog Widget”, que possui duas partes fundamentais:

![TELA 13 - Designer e Graph](https://user-images.githubusercontent.com/101642150/166319369-05fecf5c-9d1f-43e5-b730-765b86317a28.PNG)

Dentro da blueprint de design existirá a configuração do que aparecerá na tela para o jogador durante o diálogo, tanto quando o NPC estiver falando (aqui utilizando-se o “speak”) quanto quando o jogador estiver respondendo (aqui utilizando-se o “reply”).

![TELA 14 - Hierarchy Designer](https://user-images.githubusercontent.com/101642150/166319407-bab8f193-6f99-4b72-a77f-593eef7935ae.PNG)

As questões de aparência podem ser configuradas de infinitas maneiras. O fundamental é que as “Size Box” e o texto/lista estejam marcados como variáveis. Além disso, as “Size Box” devem ter sua visibilidade colocada para “Collapsed”, enquanto o “Speak” deve ser configurado para “Not Hit – Testable (Self Only)” e o “Reply” para “Visible”.

![TELA 15 - NotHit](https://user-images.githubusercontent.com/101642150/166319440-32c06e5a-a3a5-43d6-8cac-4e3e36a09c58.PNG)

Visto isso, podemos passar para os nodos que moldam o comportamento do diálogo. Dentro do “Graph” do “Dialog Widget” possuímos três eventos principais: Speak, Reply e Exit. O “Exit” chama a função de encerramento existente dentro do Dialog Component e já vista anteriormente.

![TELA 16 - Exit DialogWidget](https://user-images.githubusercontent.com/101642150/166319509-eaa5f0f3-c971-418c-a656-2675dabdf2c6.PNG)

Já a “Speak” comanda que as falas do NPC apareçam na tela, usando uma variável “Enum” denominada “Dialog State – Speak or Reply” para alternar o programa entre a fala do NPC e a resposta do jogador.

![TELA 17 - Speak DialogWidget](https://user-images.githubusercontent.com/101642150/166319543-df4bf126-ad36-4223-9daa-76ff3ddbd036.PNG)

E tal alternância ocorre em uma função dentro da blueprint do DialogWidget, disposta como a seguir:

![TELA 18 - Set Dialog State](https://user-images.githubusercontent.com/101642150/166319571-083ca93c-e480-4696-8c5c-03b4c96c04c3.PNG)

Aproveitando a questão de funções, cabe salientar a existência de outra função dentro do DialogWidget, que também é fundamental para o controle de passagem entre “Speak” e “Reply”. O evento de clique no mouse:

![TELA 19 - On Mouse down](https://user-images.githubusercontent.com/101642150/166319619-b13928ee-94a1-4229-a179-49f78ef052d0.PNG)

Assim, antes de mostrar os nodos do “Reply”, cabe ressaltar que a lista de variáveis do DialogWidget são reflexo das variáveis já mencionadas na disposição visual junto daquelas necessárias para o controle de mudanças entre “Speak” e “Reply”.

![TELA 20 - Variaveis DialogWidget](https://user-images.githubusercontent.com/101642150/166319657-a7954c84-2cf5-4deb-bb3b-67f65dfd9948.PNG)

Já os nodos do evento “Reply” seguem o mesmo padrão de alternância ao final, com a adição de que lidam com uma listagem de possíveis respostas do jogador.

![TELA 21 - Reply Parte 01](https://user-images.githubusercontent.com/101642150/166319708-c41f7aa6-803d-46df-bc55-712c26f32e91.PNG)
![TELA 22 - Reply Parte 02](https://user-images.githubusercontent.com/101642150/166319722-91675b14-839a-4abf-b4e1-a04e42a13260.PNG)

Assim se termina a parte do comando do que aparece na tela. No entanto, ainda falta o que roda por trás das Behavior Tree para que se indique quais os “reply” ou “speak” que aparecerão na tela pelos comandos do DialogWidget. Para isso, é necessária a existência de um BlackBoard e de quantas Behavior Trees forem desejadas para o jogo. No tocante à BlackBoard, o vínculo com o já visto até aqui se dá por duas keys:

![TELA 23 - DialogfromBB](https://user-images.githubusercontent.com/101642150/166319762-3c7487b8-0340-482a-854e-b2029d4661f9.PNG)
![TELA 24 - ReplyfromBB](https://user-images.githubusercontent.com/101642150/166319770-061cd34a-bf11-4f21-9958-1e56ab8ed870.PNG)

Como cérebro, a BlackBoard comanda as Behavior Tree através de suas variáveis (keys) e das Tasks que podemos configurar para que sejam executadas durante o funcionamento da Behavior Tree. Nesse caso, o ato de Speak ou Reply acaba sendo um nodo a ser executado dentro de uma Behavior Tree, utilizando-se tasks de Reply ou Speak vinculadas ao funcionamento visual estruturado pelo DialogWidget. Vejamos a task “SpeakTaskNPC”:

![TELA 25 - SpeakTask](https://user-images.githubusercontent.com/101642150/166319957-998bc5d6-e42c-4e83-b17e-667a936c1e2b.PNG)

E agora a “ReplyTaskNPC”:

![TELA 26 - ReplyTask](https://user-images.githubusercontent.com/101642150/166319996-c687175b-15b1-41c7-98a5-3a87bc837bc1.PNG)

Além dessas duas tasks, é fundamental também a existência de uma que comande o final da interação com a Behavior Tree, a qual aqui chamaremos de “Exit NPC”:

![TELA 27 - Exit Task](https://user-images.githubusercontent.com/101642150/166320036-7ba0bf7d-77b6-4a94-ab71-2b35564783f2.PNG)

Desse modo, através da utilização dessas três tasks, existirão infinitas possibilidades de diálogo, comandadas através da Behavior Tree, que poderá ficar semelhante a esta a seguir:

![TELA 28 - BehaviorTree](https://user-images.githubusercontent.com/101642150/166320075-b40d66f0-1c97-4859-8db8-013fd716228f.PNG)

Notamos a alternância entre tarefas de “Speak” e de “Reply”, que se refletirão na interação na tela. Em adição, pode-se criar outras tasks de Behavior Tree para modificar e incrementar a utilização do sistema de diálogo, como as duas que aparecem no canto da imagem anterior. Elas modificam variáveis da BlackBoard e marcam para o sistema informações que repercutirão em outras interações com diferentes Behavior Trees, desde que comandadas pela mesma BlackBoard.

Por exemplo, a task demonstrada abaixo marca uma variável bool “Talked_NPC01” como verdadeira:

![TELA 29 - Task Talked](https://user-images.githubusercontent.com/101642150/166320117-6993e498-10e1-4026-8b3a-fe99b492ab77.PNG)

Já em outra BehaviorTree essa mesma variável bool pode ser utilizada para determinar um comportamento ou outro pelo NPC:

![TELA 30 - Task Talked Used](https://user-images.githubusercontent.com/101642150/166320181-79021806-1c7b-46e2-8466-3c2e51ffff6e.PNG)

Isso ainda abre infinitas possibilidades de interação pelo sistema de diálogos, seja ele disposto a partir dessa construção ou de outra.
