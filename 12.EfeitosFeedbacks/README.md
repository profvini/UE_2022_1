# Efeitos e Feedbacks

#### Apresentação ####

Grupo: Matheus Petrus, Gustavo Justo Neves

Esse foi um trabalho com a proposta de simplificar a adição de efeitos visuais para projéteis em um jogo na Unreal Engine 4.

O processo de desenvolvimento foi utilizado o sistema de blueprints da própria engine.

Neste exemplo foi usado um arco e flecha, mas facilmente pode ser aplicado em outros projéteis e ser usado como magias outras armas.

Para utilizar o sistema simplificado de efeitos você deve entrar na pasta de "Feedbacks".

![Imagem4](/ArquivosReadme/Screenshot_1.png?raw=true)

Dentro da pasta de feedbacks você vai achar o actor "feedback".

![Imagem5](/ArquivosReadme/Screenshot_2.png?raw=true)

Você deve torná-lo filho do projétil que deseja os efeitos.

![Imagem6](/ArquivosReadme/Screenshot_3.png?raw=true)

E posicionar na posição desejada, lembrando que tem que ser em um local onde ele possa colidir com outros objetos.

![Imagem7](/ArquivosReadme/Screenshot_4.png?raw=true)

####Blueprints####

Primeiramente  vai ser feita a inicializado dos inputs e o tipo do efeito padrão, também foi determinado para as teclas "1,2,3 e 4" um tipo de efeito para haver a troca do efeito durante a execução do jogo. essa parte seria apenas para a demonstração dos efeito e como exemplo de aplicação.

![Imagem2](/ArquivosReadme/IncializacaoDosInputsSelecaoDosTipos.png?raw=true)

Nesta parte é onde a troca dos feitos está sendo feita, e é aqui onde você pode usar as partículas de sua preferência.
![Imagem1](/ArquivosReadme/EfeitoNaFlecha.png?raw=true)

Aqui é quando o projétil colide em algo ele chama o efeito  para mostrar a colisão.
![Imagem3](/ArquivosReadme/SpawnEfeitoDeColisao.png?raw=true)

Todo o projeto foi feito para 4 tipos de efeitos diferentes, mas ele pode ser facilmente expansível para muitos mais.

####Gifs De Demonstração####

Troca de Efeitos
![Gif1](/ArquivosReadme/Animação23.gif?raw=true)

Disparo e colisão
![Gif2](/ArquivosReadme/Animação25.gif?raw=true)
