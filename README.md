# linhabraile
Projeto open source - linha braile
21/06/2019

Analisando uma postagem no facebook fui verificar o custo do aparelho "linha braile". Nossa como o pessoal explora, o custo é altíssimo. Queria ser rico para trampar só desenvolvendo produtos de tecnologia assistiva, com custo acessível para todos.

#Pensando numa solução:
passei a madrugada do feriadão analisando como é feita a escrita braile e fiz um modelo 3D no freecad da mecânica (acredito que funcione) na  teoria funciona, com um custo bem mais baixo.
Não consigo imprimir para testar na impressora 3D FDM, porque as peças são muito pequenas (algumas tem 1.5mm, 1mm e menores), teria que ser uma impressora 3D do tipo SLS, DLP ou algo do gênero que tenha mais precisão com peças pequenas.
Depois poderia tirar um positivo ou negativo no silicone e fazer em resina os clones das peças, reduzindo custo. Ou mandando em algum lugar para injetar em plástico resistente ou prensar em chapas de metal. (Primeiro precisa fazer o protótipo, testar e corrigir os problemas)

O princípio é o mesmo do cadeado com chave, quando entra a chave empurra o pino para cima conforme a posição que ele se encontra irá formar uma combinação, com isso gerando a letra.

Para quem interessar de fazer o protótipo, veja como foi feita a análise:
Cada célula braile é formada por 6 pinos, desenvolver bobinas de tração com imã (eletroimã), sairia muito caro. O tamanho das células são extremamente pequenos (< 2mm).
A ideia então se baseou no princípio da chave e do cadeado onde uma barra com 2 elevações empurram os pinos para cima. E molas empurram para baixo.
Cada barra consegue mover 3 pinos, sendo assim serão necessárias 2 para cada célula.
A barra tem 2 elevações e um área baixa. Uma das elevações a mais larga, serve para levantar os 3 pinos (a,b,c), fazendo as combinações (a,ab,abc,bc,c) e a elevação curta serve para levantar somente o pino do meio (b), a área baixa deixa os 3 pinos (a,b,c) abaixados. Com isso conseguimos controlar um lado da célula, duplicamos para o outro lado usando o mesmo princípio.
A barra é movimentada usando um motor de vibracall de 4mm(d) x 8mm(c) de baixo custo (tirando o peso da ponta) e colocando um parafuso junto ao seu eixo com a função de rosca deslizante. Na barra com as 2 elevações se fixa numa ponta a porca que irá puxar ou empurrar a barra, (no projeto não coloquei mas terá que ter uma canaleta que serve para a porca não rodar e sim deslizar em cima dessa canaleta puxando e empurrando a barra com as 2 elevações. É o mesmo princípio do eixo Z de impressora 3D (Graber) ou o motor de drive de CDrom que move a cabeça de leitura.

Os motores serão controlados através de placas com circuito ponte H e adaptação de tensão para 3V, por causa da tensão dos motores.
Estas pontes H serão controladas através de expansões de IO (cada célula precisa de 2 motores) se formos colocar 10 células precisaremos de 20 motores, para 20 células (40 motores) para 40 células braile (80 motores).
Cada placa de ponte H suporta 2 motores, sendo que cada entrada que controla 1 motor na ponte H precisamos de 2 dados (para girar de uma lado ou do outro, ou breque), então para cada célula braile (ou placa ponte H) precisaremos de 4 portas digitais vindas da placa principal (processador), para expandir usamos as placas de expansão de IO, com isso, conseguimos expandir o número de portas IO.

Agora o coração de tudo seria o microcontrolador ou microprocessador, acredito que de até para usar o arduino mega (+-40 reais - china), menor custo, porém menos recursos.
Pensei no Raspeberry Pi3 A+, que já tem bluetooth e wifi. (porém custa mais caro 220,00).

#Como vai funcionar ?
Um programador irá desenvolver e colocar um programa no Raspeberry que irá se comunicar com o smartphone e pc (bluetooth ou wifi). Ou arduino via USB. Talvez um programa para smartphone seja necessário.
Este irá converter os arquivos .pdf, doc, etc... em linhas de comandos e sinais que serão enviados na placa de expansão de GPIO e esta irá mandar os sinais nas placas ponte H.
A ponte H irá comandar os motores para puxar ou empurrar as barras (calibrando o tempo de rotação conseguimos posicionar no lugar certo), então irão levantar ou abaixar os pinos para que o deficiente visual consigia ler.
Não foi colocado no projeto, será necessário colocar alguns botões de controle para proceguir ou continuar o texto, pausando, etc. E outras funções que seja necessárias, neste ponto entra a conversa do programador, com o usuário para ver as necessidades e facilidades a serem implementadas.

Cotei ontem o valor das peças de eletrônica no Aliexpress e ficou em torno de 530,00 para 10 células braile, sem o custo da mecânica e o preço do programador. 
Se o pessoal ajudar e fizer open source como gostaria que fosse podemos ajudar muitas pessoas.
Estarei liberando o projeto no Github para quem interessar a desenvolver e melhorar o projeto. 
Por um mundo melhor para todos. Abraços.


https://pt.aliexpress.com/item/10-pcs-DC-M-dulo-de-Acionamento-Do-Motor-Invertendo-PWM-Velocidade-Dupla-H-Ponte-Stepper/32960086745.html?spm=a2g0o.cart.0.0.38c83c00TD1jQM

https://pt.aliexpress.com/item/Best-Price-10x-4x8mm-DC-1-5-3V-Micro-Cell-Phone-Coreless-Vibration-Motor-Vibrator-For/32694004681.html?spm=a2g0o.cart.0.0.38c83c00TD1jQM

https://pt.aliexpress.com/item/M-dulo-de-Expans-o-GPIO-32-8-bit-de-Entrada-Sa-da-IO-Estender-M/32947609674.html?spm=a2g0o.cart.0.0.38c83c00TD1jQM

https://www.filipeflop.com/produto/raspberry-pi-3-a/


