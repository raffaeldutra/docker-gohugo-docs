---
title: Utilizando imagens
weight: 8
pre: "<b>3.3 </b>"
chapter: false
---

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
