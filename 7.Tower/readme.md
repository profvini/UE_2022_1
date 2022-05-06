# Projeto Tower Defense FPS
Desenvolvido por Carlos Reis, Felipe Brocker e Filipe Rubin na Unreal Engine 5, o projeto se trata de um jogo estilo tower defense, onde o jogador deve proteger o "castelo" de vários inimigos (Aliens) que tentarão atacar as entradas do castelo.

# Gameplay
A gameplay é em estilo FPS e foi feita a partir de pacotes de conteúdos padrões da Unreal, com leves modificações para combinar com o estilo do jogo. Outros fatores característicos são a vida da base, que é calculada a partir da quantidade de barreiras (4 no jogo final, mas pode ser alterada dentro do projeto) e o fato de que os inimigos não atacam o jogador diretamente, mas sim o castelo, que é a preocupação de fato do jogador.

# Detalhes técnicos e guias
O jogo foi desenvolvido utilizando blueprints em todas as classes (Actors, Game Mode, Widgets, etc.).
### Como fazer o sistema de munições
A partir do blueprint FPS padrão da Unreal, adicionamos uma condição (Branch) para que o personagem possa atirar, e após o tiro a variável Ammo é subtraída:
<!-- teste -->
![Screenshot_14](https://user-images.githubusercontent.com/89143853/167056587-b609ed04-7963-49c8-a674-dc5882b564fe.png)
<!-- teste -->
### Como o sistema de rounds funciona
Dentro do Game Mode utilizado, vamos precisar de 3 variáveis para controlar, respectivamente, o round atual, a quantidade de inimigos que "spawnaram" este round e a quantidade de inimigos que foram mortos este round:
<!-- teste -->
![Screenshot_15](https://user-images.githubusercontent.com/89143853/167158316-783d3c19-afeb-483d-8244-5d504b51d3a0.png)
<!-- teste -->
Após criadas, precisaremos de um evento para iniciar um novo round e spawnar inimigos (utilizando um timer em loop) enquanto o número deles for inferior ao algotitmo utilizado:
<!-- teste -->
![Screenshot_18](https://user-images.githubusercontent.com/89143853/167161158-662cd413-17f0-4619-a8d0-b490bea082b0.png)
<!-- teste -->
Nota: O algoritmo utilizado é que o número máximo de inimigos por round deverá ser o número do round atual multiplicado por dois, somado com 4.
O evento acima que spawna novos inimigos é chamado por um timer que é ligado em todo início de round (e finalizado quando todos os inimigos foram spawnados).

Por último, precisaremos de um evento ou função que será chamada para realizar a troca de rounds quando o número de inimigos mortos for igual ao número de inimigos totais do round (algoritmo explicado acima):
<!-- teste -->
![Screenshot_20](https://user-images.githubusercontent.com/89143853/167175744-f37141ae-92fb-4263-afc3-8239745cffea.png)
<!-- teste -->
