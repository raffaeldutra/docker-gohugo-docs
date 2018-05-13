---
title: Dockerfile
weight: 5
pre: "<b>1.3 </b>"
chapter: false
---


Chegamos então ao arquivo principal de Docker, o tão conhecido **Dockerfile**. Dockerfile é um simples arquivo texto que contem todos os comandos para gerar uma imagem, apenas isso em sua forma mais resumida.

Se você já conhece um pouco de CLI (Command Line Interface) de GNU/Linux, provavelmente não terá nenhum problema para utilizar Dockerfile, pois ele é basicamente comando que você já usa.

Aqui está a lista dos comandos que você pode utilizar dentro do seu arquivo. Vamos explicar rapidamente o que cada um faz.

* FROM - define a imagem base para você iniciar sua nova imagem.
* LABEL - aqui é possível definir algumas informações para melhor organização de suas imagens, você pode usar quantas labels quiser.
* ENV - variáveis de ambiente que serão utilizadas dentro do container quando você invocar a imagem.
* RUN - aqui irão entrar todos os comandos que deseja executar assim que iniciar a buildar sua imagem.
* WORKDIR - de onde serão executados os comandos, este comando é um path apenas.
* VOLUME - possibilita o acesso de um diretório na sua máquina real.
* USER - qual usuário irá executar os comandos dentro da imagem, o padrão é root.
* ADD or COPY - copia arquivos e diretórios de sua máquina local para dentro da imagem.
* EXPOSE - expõe uma porta para ser acessada publicamente, como a porta 80, por exemplo
* CMD - executa um comando assim que você invocar a imagem.
* ENTRYPOINT - parecido com o CMD, mas aqui normalmente você coloca um script para ser iniciado.

Vou deixa aqui um exemplo utilizando como base a imagem Nginx que já estavámos utilizando anteriormente com o máximo de comandos que o Dockerfile suporta e que vimos acima.

```
FROM nginx:latest

LABEL description="Docker imagem que será gerada no nosso exmeplo."
LABEL maintainer="Rafael Dutra <raffaeldutra@gmail.com>"

ENV FOSSDAY Lajeado
ENV QUANDO 5/5 2018

RUN apt-get update && \
    apt-get install git --yes

ADD index.html /usr/share/nginx/html/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

## Criando nossa imagem utilizando o Dockerfile

É realmente simples gerarmos uma imagem com o nosso arquivo, segue um exemplo de como isto pode ser feito.

```
docker build --tag fossday/nginx:0.1 .
```

Agora vamos executar o nosso container baseado na imagem que acabamos de gerar.

```
docker run --interactive --tty --publish 46000:80 fossday/nginx:0.1 /bin/bash
```

Vamos acessa a url e ver o que nos espera, http://localhost:46000

* O que aconteceu?
* Qual o motivo de alterarmos o arquivo index.html em nossa máquina e nada aconteceu na página?
