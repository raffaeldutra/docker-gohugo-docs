# O básico

Verifique se está com docker corretamente funcionando, para isso execute o comando:

```
docker version
```

Sua saída deve ser algo parecido com:

```
rafael @ nazgul ~
└─ $ ▶ docker version
Client:
 Version:	17.12.0-ce
 API version:	1.35
 Go version:	go1.9.2
 Git commit:	c97c6d6
 Built:	Wed Dec 27 20:03:51 2017
 OS/Arch:	darwin/amd64

Server:
 Engine:
  Version:	17.12.0-ce
  API version:	1.35 (minimum version 1.12)
  Go version:	go1.9.2
  Git commit:	c97c6d6
  Built:	Wed Dec 27 20:12:29 2017
  OS/Arch:	linux/amd64
  Experimental:	true
```


# Comandos

Para verificar todos os comandos proporcionados por Docker, simplesmente digite:

```
docker
```

Importante: não esqueça que a linha de comando (CLI) é sua melhor amiga, caso não souber como um comando continua, ou seja, opções deste comando, simplesmente digite:

```
docker <comando> --help
```


## Rodando um container

```
docker run alpine hostname
```

Você provavelmente teve uma resposta com letras e números, algo como: *7ed46aef747a*.  
O que acabamos de ver aqui é o nome do container no momento que você o executou.  

Vamos explicar por partes o que o comando acima faz:

* **docker run** executa um container
* **alpine** é o nome da imagem que estamos Utilizando
* **hostname** é o comando que é executado dentro do container, por isso obtemos aquele conjunto de números e letras como resposta quando executamos o comando.

O que iremos ver agora é:

* Executando o comando acima algumas vezes, o resultado mudou?


## Utilizando imagens

Tudo que iremos executar em um container, vem de uma imagem e essa imagem pode ser uma que você mesmo criou ou uma imagem oficial, como foi o nosso caso acima como o Alpine.

> Apenas por conhecimento, Alpine é uma distribuição Linux super pequena que neste exato momento em sua versão 3.7.0 tem uma iso de 130MB e o mesmo vale para sua imagem para container, acredite, são 4.5MB de tamanho.

Execute o comando:

```
docker images
```

E o resultado deve ser algo assim:

```
rafael @ nazgul ~
└─ $ ▶ docker images
REPOSITORY                          TAG                    IMAGE ID            CREATED             SIZE
golang                              1.10.0-alpine3.7       85256d3905e2        7 weeks ago         376MB
maven                               3.5.2-jdk-8            31eec910d005        7 weeks ago         748MB
ubuntu                              16.04                  0458a4468cbc        2 months ago        112MB
ubuntu                              latest                 0458a4468cbc        2 months ago        112MB
raffaeldutra/gohugo                 latest                 7d6cac06f35c        2 months ago        1.11GB
golang                              latest                 3858fd70eed2        2 months ago        735MB
python                              2.7-alpine             0781c116c406        2 months ago        72.4MB
python                              3.6.4-alpine3.7        4b00a94b6f26        2 months ago        83.4MB
alpine                              3.4                    c7fc7faf8c28        3 months ago        4.82MB
alpine                              latest                 3fd9065eaf02        3 months ago        4.15MB
nginx                               latest                 3f8a4339aadd        3 months ago        108MB
jenkins                             latest                 5fc84ab0b7ad        3 months ago        809MB
jenkins                             2.60.3-alpine          2ad007d33253        5 months ago        223MB
maven                               3.5.2-jdk-8-alpine     293423a981a7        5 months ago        116MB
java                                openjdk-8-jdk-alpine   3fd9dd82815c        13 months ago       145MB
java                                8u102-jre              13f413e924a3        17 months ago       309MB
```

O que iremos ver agora é:

* Como procurar uma imagem?

```
docker search <imagem>
```

* Como remover uma imagem?

```
docker rmi alpine
```

> Aqui iremos obter um erro, pois temos aquele primeiro container -- docker run alpine hostname -- em funcionamento e não é possível remover uma imagem onde há containers rodando.

* Como saber se a imagem que vou utilizar é uma imagem oficial?

```
docker search ubuntu
```

* Como baixamos uma imagem?

```
docker pull ubuntu
```

e para baixarmos uma versão específica, como Ubuntu 18.04? Para isso passe após o : a versão que quer utilizar

```
docker pull ubuntu:18.04
```


## Gerenciando os containers

Para podermos utilizar os comandos de stop e start, por exemplo, precisamos ter um container que de fato esta parado ou rodando, certo? então agora vamos rodar um container um pouco mais "complexo".

> Atenção, localhost é para máquinas que estão com Docker rodando diretamente no "bare metal", se estiver utilizando VM acesse o IP desta VM, algo como 192.168.25.100 - 10.100.111.222

Abra um browser e acesse http://localhost:45000 e a página não foi localizada, certo?

Execute o seguinte comando:

```
docker run --detach --publish 45000:80 nginx
```

Agora abra novamente o endereço http://localhost:45000 - Magic!

Certo, agora temos um servidor web funcionando com apenas um comando na porta 45000 e com isso em funcionamento podemos utilizar os comandos de stop e start.

Vamos parar o container:

```
docker container stop <id do container>
```

Acesse novamente o seu browser e tente acessar a porta 45000.

Vamos subir novamente o container com o comando:

```
docker container start <id do container>
```


## Manipulando containers

O comando que executamos incialmente *docker run alpine hostname* é o mais básico possível para termos um container em "funcionamento". O "funcionamento" entre aspas é o que iremos discutir neste momento.

Antes tentamos remover a imagem *alpine* e obtivemos um erro, mas o que causou o erro? Foi devido que o container está rodando. Então como sabemos se um container está rodando? ou melhor, como sabemos o "status" de um container?

Utilize o comando:

```
docker container <comando>
```

* Queremos listar containers?

```
docker container ls
```

* Queremos parar?

```
docker container stop <nome do container> ou <id do container>
```

* Queremos iniciar?

```
docker container start <nome do container> ou <id do container>
```

Para a lista de comandos que podemos utilizar, simplesmente execute:

```
docker container
```


## Limpando o que não é usado

Você irá notar que depois de muitos comandos para lá e para cá, muitas coisas ficaram para trás, como containers parados, imagens não "funcionais" e etc. Para limparmos essa bagunça, execute o comando abaixo:

```
docker system prune
```

Você irá receber algo do tipo:

```
rafael @ nazgul ~
└─ $ ▶ docker system prune
WARNING! This will remove:
        - all stopped containers
        - all networks not used by at least one container
        - all dangling images
        - all build cache
Are you sure you want to continue? [y/N] y
Deleted Containers:
7ed46aef747a7726285ecde46f7fbcd37fb932e1d106a5552a5ec6205cb45f2f
847d0f4d36f2b295804778ea69d33e3f9e4fbaf968fec9c244126955aba50e9b
a47ad7b67d69698896b290f6daf7e4f65760a38a15a2ba10ed87e3d33ecc1032
dfcbe65a5ae70c204abec0f8a224d1373804c64a927ada38f09d773aca29020d
62126d53d79232d6bd687a68990e5ef05b5e9e3f8e678286994e2370e9c6faed
b9427ac05e95b6a7256dec9d53578ed1d05c6792333917e69be5f71e074a5a50
076a96cd455ad7d7a97d2756b8bd1768aa474fccb7c73022fc94aa013ff0a274
afdf2d8219b5917ba9e110657e0364d7c9f407e1871631669912b626bf6033a8
498da065d6e5f19e27828336a9c0a72dcce284de7ccf21e469266fb8a67a7e3d
a5dadf4de7549d7923aa9a00b5851813efd8ac7f1dd2410397865bc64955af57
365ae9546d039aba3e8df2abc5132310e2ec67f54bc20e0ac6c2e5b35e55052a
5c0e6625bda621820dc18479231a7018d7c11dd6fa933c0c4842e575041a34a0
f0e9646730cd1bd8360e2fa2a71c8bfb3910968047acffe01f772c88f75b940e

Deleted Images:
deleted: sha256:2d92e5d5adbe5e207b36d93bd14d8b75919d4a118c86f4b137a9c46481b98fef
deleted: sha256:8ae3118b00c274114fd91dc96628b845e0ff4722717bfdf343c2207bad1ec01f

Total reclaimed space: 70.62MB
```
