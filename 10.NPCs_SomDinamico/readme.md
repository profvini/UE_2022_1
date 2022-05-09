Projeto Unreal 4 de Johann Alfeu, Emiliano e Gabriel Matusiak

ÁUDIO DINÂMICO:

1 - Som de passos variados para superfícies diferentes

Primeiramente, precisamos buscar os efeitos sonoros que pretendemos usar no nosso projeto, você pode pesquisar em sites de efeitos sonoros ou gravar eles você mesmo, lembre-se também de procurar as variações para esses passos, no exemplo em que vamos trabalhar, vamos usar 3 tipos diferentes de passo para 3 materiais diferentes.

Logo após conseguir esses efeitos sonoros, vamos adicioná-los ao nosso projeto, para fazer isso, basta arrastar os arquivos para alguma pasta dentro do seu projeto.

![image](https://user-images.githubusercontent.com/89028609/167345890-bd7dbd8f-062d-4250-93f4-c25e687a4e33.png)

Para cada variação dos passos, vamos criar suas respectivas pastas separadas para ficar mais organizado.

![image](https://user-images.githubusercontent.com/89028609/167345939-26d5f991-3aa3-4dbd-8343-a88b7711411f.png)

Primeiramente, vamos abrir a pasta “DIRT” e mexer com os arquivos lá dentro. A primeira coisa que vamos adicionar, é uma “Sound-Cue”, clicando com o botão direito em qualquer parte da pasta e dentro da opção “Sounds”, clique no objeto “Sound-Cue”.

![image](https://user-images.githubusercontent.com/89028609/167346032-6ec24736-587b-4383-9b21-b97c1224e6f3.png)

Vamos renomear a Sound-Cue para “DirtFootstep” e clicar duas vezes em cima dela, abrindo seu painel de edição. Dentro do painel de edição, vamos arrastar os arquivos que estão na pasta DIRT para dentro da Sound-Cue.

![image](https://user-images.githubusercontent.com/89028609/167346083-8c0ddf75-19fe-4020-822c-1780db9ad546.png)

Depois de adicionar os arquivos na Sound-Cue, vamos adicionar uma função de Random e um Modulator. A função random vai randomizar a ordem em que os sons vão tocar, evitando repetir o mesmo som várias vezes enquanto caminha, por isso é importante ter pelo menos mais de 2 efeitos sonoros. O modulator vai servir para definir valores aleatórios de tom e volume para variar um pouco os sons, a adição desse efeito não é obrigatória.

![image](https://user-images.githubusercontent.com/89028609/167346199-41860391-4d99-47c6-98e6-14edda769ddb.png)

Depois de ter feito isso, podemos salvar, e fechar a Sound Cue.

Agora vamos acessar as preferencias do projeto, indo em Edit -> Project Settings...

![image](https://user-images.githubusercontent.com/89028609/167346245-500f3eac-9ecc-406c-b60e-ad4076fc1be2.png)

Dentro das configurações, na aba “Engine” ao lado, procure a opção “Physics”. Na aba Physics, vamos descer até encontrar a aba “Physical Surface”, e dentro dela, vamos adicionar os tipos de superfície que vamos usar no projeto.

![image](https://user-images.githubusercontent.com/89028609/167346434-8821f24d-13b4-46c2-aec4-e9d0a03a9a2d.png)

No momento, vamos adicionar apenas “Grass” e “Dirt” e deixamos Default para qualquer outra superfície além dessas duas.

Depois de ter criado essas superfícies físicas, voltamos à pasta “DIRT” que estávamos trabalhando, e clicamos com o botão direito do mouse em qualquer parte dela para criar um material físico, e vamos renomear este material para “Dirt_Footstep_PM”. 

![image](https://user-images.githubusercontent.com/89028609/167346687-bb3ad145-fba3-4144-a641-a3488db37f1b.png)

Dentro desse material físico, vamos aplicar a propriedade que criamos no passo anterior, na última opção chamada “Physical Properties”, vá até “surface type” e selecione a superficie “Dirt” que criamos.

Lembrando que este processo inteiro até agora deve ser repetido entre todas as variações de passos que você tiver. 

Suas pastas devem estar assim agora:

![image](https://user-images.githubusercontent.com/89028609/167346542-181c4579-29f8-460f-a98e-35b0f64df52c.png)

![image](https://user-images.githubusercontent.com/89028609/167346564-b47fe03a-4d5b-4d5b-8a77-d72efc3104d4.png)

![image](https://user-images.githubusercontent.com/89028609/167346590-01835c51-cf2f-4a91-a183-72ce479dcfec.png)

(a pasta “NORMAL” não tem um material físico pois vamos usa-la como superfície default)

Com tudo isso feito, vamos para as animações que vão tocar esses áudios.

Como um exemplo, vamos entrar na pasta “Mannequin -> Animations” e vamos selecionar a animação de correr “ThirdPerson_Run”. Clicando duas vezes na animação, um menu de edição irá abrir.

![image](https://user-images.githubusercontent.com/89028609/167346792-47bcfadc-be09-4fbf-98ab-a18c8c25dab3.png)

Vamos pausar a animação no frame em que o personagem encosta com o pé no chão pela primeira vez e dentro timeline, na aba “Notifies” vamos clicar com o botão direito, e selecionar “Add Notify” e vamos criar um novo Notifier.

![image](https://user-images.githubusercontent.com/89028609/167346862-b0cb3db7-68af-43ef-8098-f5667acf7fa9.png)

Vamos chamar esse notifier de “FootstepNotify”, e ele vai servir para chamar uma função na máquina toda vez em que o personagem tocar no chão. 

![image](https://user-images.githubusercontent.com/89028609/167346904-39766653-a244-4793-9763-5e485c7ce030.png)

Com isso feito, podemos salvar e fechar essa janela de edição. Vamos agora abrir a blueprint de animação do personagem, localizada na mesma pasta dessas animações.

![image](https://user-images.githubusercontent.com/89028609/167346946-92626ccd-2578-4f2a-a8f7-a686039eef0e.png)

Dentro da blueprint de animação, vamos ao “Event Graph” e mexer um pouco com os nodes.

A primeira função que vamos chamar é o notifier que criamos dentro da animação de correr, para fazer isso, clicamos com o botão direito do mouse no espaço de blueprints, e adicionamos o “FootstepNotify”.

![image](https://user-images.githubusercontent.com/89028609/167347013-da4b26d4-b8d9-4705-9f40-cbff5735cdc4.png)

Puxando deste evento, vamos adicionar a função “LineTraceByChannel”, que serve para analisar o caminho em que o player percorre. Para saber a localização e posição certa do player, vamos clicar em uma parte vazia do blueprint e chamar o “Get Player Character” e um “GetActorLocation”, isso vai manter a posição do player sempre checada para que não haja problemas. A função “GetActorLocation” não tem como posição inicial os pés do player, então para arrumar isso, teremos que puxar o node de Return Value dela e adicionar um “Vector - Vector”.

![image](https://user-images.githubusercontent.com/89028609/167347063-465063bc-b453-4a0c-b5d3-8510d263504d.png)

No valor Z dessa função, colocaremos um valor de 150, para que a checagem de superfície fique diretamente abaixo dos pés do player, esse valor pode variar se você tiver um modelo com bones diferentes.

Adicionando todos juntos, seus blueprints devem estar desse jeito:

![image](https://user-images.githubusercontent.com/89028609/167347110-21162546-53d5-4898-8280-d6f8437f84c4.png)

Puxando o node Out Hit de “LineTraceByChannel”, vamos adicionar a função “Break Hit Result” que vai trazer os resultados da checagem de passos, clique na setinha dentro dessa função para mostrar mais detalhes sobre. Também do Out Hit, vamos chamar a função “Get Surface Type” que vai servir para puxar os tipos de superfície que criamos, puxando um node dessa função, chamaremos “Switch on EPhysicalSurface” nela vai ter os nodes com as devidas superfícies. Conecte “LineTraceByChannel” com um branch à essa função e conecte o Return value de “LineTraceByChannel” como condição nesse branch.

Seus blueprints devem estar desse jeito:

![image](https://user-images.githubusercontent.com/89028609/167347168-7b1a1939-ac23-443a-aa55-7dbd16c2285a.png)

Para finalizar, vamos adicionar os efeitos sonoros, puxando cada um de seu devido node no “Switch on EPhysicalSurface”. Ao puxar o node, pesquise “Play Sound at Location” e dentro da função, selecione sound, e procure a devida Sound Cue criada para esta superfície. Arraste o node de location de “Break by Result” para o location dessas funções de som. 

![image](https://user-images.githubusercontent.com/89028609/167347227-3d98bc56-cb7d-47be-bca4-89fd77d904b1.png)

Neste exemplo usamos apenas 3 tipos diferentes de passos, mas isso pode ser aplicado com muito mais variações. 
















