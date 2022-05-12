Link do Drive com o arquivo dos modelos 3D modelados, vídeo gravado na Unreal 5.0 mostrando os arquivos e a gameplay, o PowerPoint da apresentação e o arquivo .uproject com o jogo recriado na Unreal 4.27.
https://drive.google.com/drive/folders/1lJcAfDR691z4EAM3HJvZzIwW5dscnxL4?usp=sharing

A ideia de jogo seria fazer uma simulação do White Room Experiment, onde o player passaria algumas horas preso no quarto e em alguns momentos aleatórios iria aparecer um monstro para atacar ele e matar, acabando o jogo. A única forma do player conseguir sobreviver é ele se escondendo embaixo da cama.

CONTROLES DO PLAYER:
Os controles foram criados usando inputs e Axis Mappings, um para ele se mover para frente e para trás, outro para os lados e dois para o movimento da câmera usando o mouse.
Frente e trás:
Frente -> Seta para cima e escala +1,0. 
Para trás -> Seta para baixo e escala -1,0
Lados:
Direita -> Seta da direita e escala +1,0
Esquerda -> Seta da esquerda e escala -1,0
Câmera e mouse:
LookUp
Mouse Y e escala -1,0
Turn
Mouse X e escala +1,0

Para essa configuração do mouse funcionar é preciso habilitar na câmera do player para ele usar a rotação do peão (que no caso é o player).

Na programação do Player usando as BluePrints, é preciso chamar os inputs e adicionar a "Entrada de movimento" para os movimentos nas setas do teclado. E configurar a câmera para ser a visão do player usando o "Get World Rotation".

A programação do mouse também chama os inputs, no LookUp chama a "Entrada de inclinação do controlador" e no Turn chama a "Entrada de guinada do controlador".

SISTEMA DE VIDA

Para fazer o sistema de vida, foi criada uma variável do tipo Integer com o valor de 10 chamada VidaPlayer e uma variável do tipo Boolean para fazer a verificação do status do player, se ele está vivo ou não, essa verificação é feita a todo momento no jogo (Evento Tique).

Se a vida do Player for <= 0 ele vai dar o status de que ele está morto(variável Boolean) e se ela for verdadeira irá desativar todas as entradas de movimento.

TRIGGERBOX

Para o Player receber dano ao colidir com o inimigo, foi colocado uma TriggerBox em volta do inimigo. Na BluePrint do Level irá colocar a condição de que se o player sobrepor a TriggerBox, irá subtrair 10 da variável VidaPlayer.

LUZES PISCANDO

A luz piscando foi criada usando os Atores e adicionando um ponto de luz, assim é possível configurar para desde o início do jogo, a luz ter uma oscilação na sua intensidade no período de atraso de 0,1 segundos. E o valor da intensidade varia de 500 a 5.000. 
