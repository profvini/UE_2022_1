# Projeto Tower Defense FPS
Desenvolvido por Carlos Reis, Felipe Brocker e Filipe Rubin na Unreal Engine 5, o projeto se trata de um jogo estilo tower defense, onde o jogador deve proteger o "castelo" de vários inimigos (Aliens) que tentarão atacar as entradas do castelo.

# Gameplay
A gameplay é em estilo FPS e foi feita a partir de pacotes de conteúdos padrões da Unreal, com leves modificações para combinar com o estilo do jogo. Outros fatores característicos são a vida da base, que é calculada a partir da quantidade de barreiras (4 no jogo final, mas pode ser alterada dentro do projeto) e o fato de que os inimigos não atacam o jogador diretamente, e sim o castelo, que é a preocupação de fato do jogador.

# Detalhes técnicos e guias
O jogo foi desenvolvido utilizando blueprints em todas as classes (Actors, Game Mode, Widgets, etc.)
### Como fazer o sistema de munições
A partir do blueprint FPS padrão da Unreal, adicionamos uma condição (Branch) para que o personagem possa atirar, e após o tiro a variável Ammo é subtraída:
![Screenshot_14](https://user-images.githubusercontent.com/89143853/167056587-b609ed04-7963-49c8-a674-dc5882b564fe.png)

[Trabalho em progresso...]
