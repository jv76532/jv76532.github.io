---
title: "Introdução +Hardcore a Computação"
date: 2026-02-26 13:00:00 +0800
categories: [Computação]
tags: [computação, programação, matemática]
math: true
---

Olá a todos! Neste post irei compartilhar um pouco do que aprendi com um vídeo clássico do grande Fábio Akita. Esse vídeo é o 'Introdução +Hardcore a Computação', que é excelente e todo programador iniciante como eu deveria assistir pelo menos umas 2 ou 3 vezes. Eu já assisti esse vídeo algumas vezes no passado, porém eu ainda era imaturo e não aprendi nada mesmo. Mas agora dessa vez na faculdade estou levando a sério os estudos e assisti mais uma vez ontem a esse vídeo. A algumas semanas antes tive minhas primeiras aulas da disciplina de Introdução a Computação, então muito que o Akita abordou no vídeo já estava fresco em minha mente e mesmo assim acredito que vou precisar assistir mais uma vez para ter certeza que não deixei passar nada. No vídeo o Akita menciona alguns canais, mas o principal foi o Ben Eater e vou está focando nessa parte aqui no post. Esse cara tem uma playlist inteira programando um chip de 8-bits chamado MOS 6502 que foi usado no Nintendinho e no Apple II. Apesar de ser um chip bem antigo, nós iniciantes temos muito que aprender com ele porque tudo aquilo que é moderno foi construído por cima dessa base e pelo menos assistir esse chip sendo programado no baixíssimo nível já é um baita de um exercício dos sistemas numéricos binário e hexadecimal como também entender o verdadeiro processamento que é feito na relação entre CPU e memórias. Neste post então vou abordar essas partes que tem muito a agregar em nosso conhecimento sobre computadores.

## A importância de entender o baixo nível

A principal razão de entender o que acontece ali no baixo nível é quebrar todo mistério e magia que existe em torno dos computadores e entender do que realmente se trata tornando o que antes ara misticismo em um sistema com partes bem definidas interconectadas que se organizam de forma hierárquica e isso abre muito a mente do programador para conseguir entender todo o resto como o 'por que isso' ou 'por que aquilo' sobre linguagens de programação e sistemas operacionais. Então, antes de seguir a diante quero deixar claro o que significa baixo nível e na verdade isso é algo bem fácil de entender. Os computadores são maquinas rápidas, muito rápidas mesmo, porém com o contra de serem burras. Um computador somente conhece dois algarismos numéricos, o '0' e o '1' que são os únicos algarismos do sistema numérico binário. As maquinas são construídas assim por uma questão de engenharia eletrônica dos computadores digitais que tem o proposito de serem programados para processar dados a nós humanos e possamos construir informação de forma automática daí. O uso do sistema binário permite trafegar dados de forma quase instantânea por meio de fios condutores entre o microprocessador, memórias e dispositivos de entrada e saída.

Se eu fosse explicar o nível mais baixo da computação teria que ir até a física por trás dos componentes eletrônicos que compõe a maquina, mas isso está completamente fora da minha alçada. Para simplificar as coisas já é o suficiente abordar aquilo que se restringe ao nível lógico que consiste nos sinais trocados entre as partes do computador que fazem executar suas operações processando dados afim de criar informação de forma automática. Então entenda que baixo nível é aquilo que está mais próximo do hardware, como dados que são lidos como instruções pelo chip e assim executando alguma operação, e logo o alto nível seria tudo aquilo mais próximo ao ser humano, como uma sequencia de dados convertidos por software a caracteres formando um texto legível na tela. Ainda essa ideia pode parecer um pouco abstrata dessa forma e para melhor entendimento do que realmente diferencia baixo/alto nível é necessário se aprofundar um pouco mais naquilo que é o baixo nível.

## Sistema numérico binário e hexadecimal

O sistema numérico convencional é o decimal que tem esse nome por possuir dez algarismos, $\mathcal{D} = \\{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\\}$. E esse sistema que usamos ele é posicional, significa que o valor de um algarismo vária dependendo de sua posição. Então, por exemplo, um número decimal quando decomposto fica assim: $(532)_{10} = 5 \times 10^2 + 3 \times 10^1 + 2 \times 10^0$. Entendendo o sistema decimal, agora vamos para o binário que é usado na lógica da maquina. Esse sistema possui apenas dois algarismos, por isso o nome binário, e ele também é posicional. E para facilitar a vida daqueles programadores que ficavam escovando bits nos primeiros computadores, foi adotado o sistema hexadecimal que é muito mais fácil de ler e escrever do que longas sequencias de zeros e uns. Como o nome sugere possui dezesseis algarismos, $\mathcal{H} = \\{0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, b, c, d, e, f\\}$. Nesse sistema temos os algarismos da base decimal mais outros 6 que são as primeiras letras do alfabeto. Para converter essas bases ao sistema decimal é usado a seguinte formula:

$$ (abcd)_{\beta} = (a \times \beta^3 + b \times \beta^2 + c \times \beta^1 + d \times \beta^0)_{10} $$

Convertendo binário e hexadecimal para decimal:

$$ (1011)_{2} = (1 \times 2^3 + 0 \times 2^2 + 1 \times 2^1 + 1 \times 2^0)_{10} = (11)_{10} $$

$$ (10F4)_{16} = (1 \times 16^3 + 0 \times 16^2 + 15 \times 16^1 + 4 \times 16^0)_{10} = (4.340)_{10} $$

Para converter qualquer base para decimal você multiplica o valor do algarismo em decimal pela base elevado ao expoente posicional, que da esquerda para direita começa em 0 depois 1, 2 e etc. Aí depois é só somar esses produtos. Assim fica mais fácil de entender que cada algarismo binário a esquerda a quantidade de valores que podem ser representados dobra. Nesse exemplo usamos um número binário de 4 algarismos e essa quantidade de bits poderia representar qualquer número entre 0 e 15, ou seja, são 16 números possíveis de se representar com 4 bits.

$$ 2^1 = 2 \quad 2^2 = 4 \quad 2^3 = 8 \quad 2^4 = 16 \quad 2^5 = 32 $$

Como o sistema hexadecimal tem dezesseis algarismos então cada algarismo é o mesmo que 4 binários.

$$ 16^4 = 2^{16} = 65.536 $$

### Bits, nibbles e bytes

Acabei usando o termo bit para me referir a um algarismo binário e acontece que existe outros nomes que são usados para descrever a quantidade de posições (ou bits) que um binário tem. Voltando ao sistema decimal a fim de explicar isso, nele a menor posição de um algarismo é a unidade que é seguida da dezena e essa seguida da centena e etc. No sistema binário funciona assim: um algarismo individual é chamado de bit, quando temos 4 bits chamamos o número de nibble e quando são 8 bits ou 2 nibbles o número é um byte. Depois disso, nomes revelantes para essas diferentes quantidades são apenas dados a grandes quantidades de bytes como um kilobyte que são 1024 bytes, megabyte que são 1.048.576 bytes, e depois tem gigabytes, terabytes e vai até yottabytes.

(tabela de byte até yottabyte)

### Operações com binários

(encontrei aqui algumas lacunas de conhecimento e quero me aprofundar antes de continuar a escrever) 

# Chip MOS 6502 e o que ele tem em comum com os chips modernos
# Programando um 'Hello, World!' no MOS 6502
# Linguagem Assembly e o Assembler
# Conclusão

