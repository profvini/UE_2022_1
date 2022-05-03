Grupo: Bruno, Gabriel e Roberta

Trabalho Arco e Flecha

Projeto desenvolvido na Unreal versão 4.27, onde o usuário consegue praticar arco e flecha em um cenário com visão primeira pessoa. Para este projeto foram utilizadas "blueprints" para os códigos e animação do arco, além disso este trabalho foi criado a partir de um projeto de visão primeira de primeira pessoa que já vem pronto na Unreal. Neste projeto pronto, o jogador já consegue mexer em uma arma e atirar, porém essa mecânica já foi descartada logo de inicio deixando apenas a câmera. 

No objeto do jogador, além de ter tirado a arma, foi colocado o arco, foi adicionado um script para recarregar as flechas e foi adicionado mais alguns eventos para posicionar o arco na tela de maneira adequada.  

![Imagem1](/11.ArcoeFlecha/Imagensdoprojeto/Script_primeirapessoa.png?raw=true)

Além de acrescentar eventos para posicionar o arco, também há eventos para as ações que o jogador pode fazer que é puxar o arco e atirar.

![Imagem2](/11.ArcoeFlecha/Imagensdoprojeto/Eventos1_primeirapessoa.png?raw=true)

![Imagem3](/11.ArcoeFlecha/Imagensdoprojeto/Eventos2_primeirapessoa.png?raw=true)

![Imagem4](/11.ArcoeFlecha/Imagensdoprojeto/Eventos3_primeirapessoa.png?raw=true)

No arco foi adicionado eventos de ações do arco no blueprint, as ações que ele pode fazer é puxar, recarregar e atirar. Para ação de puxar foram colocados eventos divididos em três partes, uma parte para o quando o jogador começa a puxar a corda, outra quando ele para de puxar mas não finaliza a ação e outra pra quando o jogador solta a corda para atirar, isso foi feito por causa da mecânica e animação. 

![Imagem5](/11.ArcoeFlecha/Imagensdoprojeto/Eventos1_Arco.png?raw=true)

Também foram adicionados eventos que recarregam o arco, nessa parte também foi colocado códigos para determinar o local que a flecha vai ficar no arco, e além disso também foi determinado um número de flechas que o jogador tem. E por fim, foram colocados eventos para o momento que o jogador atira.

![Imagem6](/11.ArcoeFlecha/Imagensdoprojeto/Eventos2_Arco.png?raw=true)

![Imagem7](/11.ArcoeFlecha/Imagensdoprojeto/Eventos3_Arco.png?raw=true)

Para as flechas foram criados eventos para que elas possam ser disparadas, além disso foram criados scripts para os estados da flecha. Esse scripts sobre os estados da flecha foram feitos para que algumas ações não ocorram, como por exemplo evitar que o jogador atire quando uma flecha esta no ar ainda. Existe scripts para o inicio e fim dos estados, além de outro para definir as ações dos estados da flecha.

![Imagem8](/11.ArcoeFlecha/Imagensdoprojeto/Eventos1_Flechas.png?raw=true)

![Imagem9](/11.ArcoeFlecha/Imagensdoprojeto/Script1_Flecha.png?raw=true)

![Imagem10](/11.ArcoeFlecha/Imagensdoprojeto/Script2_Flecha.png?raw=true)

![Imagem11](/11.ArcoeFlecha/Imagensdoprojeto/Script3_Flecha.png?raw=true)

![Imagem12](/11.ArcoeFlecha/Imagensdoprojeto/Script4_Flecha.png?raw=true)

![Imagem13](/11.ArcoeFlecha/Imagensdoprojeto/Script5_Flecha.png?raw=true)

Para a animação foi feita uma bledspace onde foram colocadas duas animações, uma é o arco estático e a outra é o arco com a corda puxada. Depois de finalizada essa parte foi feita uma blueprint para que essas ações fossem executadas.

![Imagem14](/11.ArcoeFlecha/Imagensdoprojeto/Blendspace_Anim.png?raw=true)

![Imagem15](/11.ArcoeFlecha/Imagensdoprojeto/Eventos1_Animar.png?raw=true)
