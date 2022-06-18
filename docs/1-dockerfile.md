# Dockerfile

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

Aqui um exemplo utilizando como base a imagem Nginx que já estavámos utilizando anteriormente com o máximo de comandos que o Dockerfile suporta e que vimos acima.

```bash
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

## Criando imagens sem Dockerfile

Sim, nós também podemos criar imagens sem precisar de Dockerfile. Vamos ver o seguinte:

```bash
docker run --interactive --tty ubuntu /bin/bash
```

Com este comando nós "entramos" no container. Dentro do container podemos fazer o que quisermos, como adicionar arquivos, remover arquivos, adicionar pacotes e etc.

Vamos então adicionar um pacote. No container, execute:

```bash
apt-get update && apt-get install curl
```

## Interagindo

Até agora fizemos alguns poucos exemplos, vamos entrar de fato em um container e trabalhar um pouco com ele.

Execute o seguinte comando:

```
docker run --interactive --tty --publish 45000:80 nginx /bin/bash
```

* Edite o arquivo **/usr/share/nginx/html/index.html** com o vim

O que aconteceu?

```
apt-get update && apt-get install vim --yes
```

Vamos acessar novamente o nosso web server na porta 45000 e percebemos que? Pois então, ao entrarmos dentro de um container, nós "perdemos" a execução de comando/entrypoint que a imagem foi destinada e para entedemos melhor, vamos ver como esta imagem do **nginx** foi criada. Para isso nós iremos acessar um repositório desta imagem no [Github](https://github.com/nginxinc/docker-nginx).

Docker Hub é um repositório aberto de imagens de onde todas imagens públicas, inclusive esta que estamos usando neste momento, estão sendo utilizadas. Você pode criar sua propria imagem e envia-lá sem problema algum para o Docker Hub, apenas atente para não deixar nenhum tipo de credential "boiando" por lá.

Vamos então [abrir o repositório do Nginx](https://hub.docker.com/_/nginx/) e ver de mais perto o que estamos conversando.

Ao abrirmos o arquivo de como é feita a imagem, percebemos na última que existe um comando chamado **CMD ["nginx", "-g", "daemon off;"]**. Este comando nos diz o seguinte em uma tradução livre "quando você rodar um novo container eu automaticamente vou invocar o comando nginx -g daemon para você". No nosso caso, acessamos o container de modo que estamos "brincando" com ele e este comando não foi executado pois ele somente é dispararado quando não passamos um novo parâmetro para ele, que foi o **/bin/bash**.

Dockerfile é este arquivo que estamos acessando neste momento e entendendo sua "planta baixa" de como funciona sua imagem e que também entraremos para falar somente dele.

Voltamos ao nosso problema inicial. Percebemos que ao entrar no container que está rodando Nginx ele não subiu o serviço e com isso nos vem a pergunta simples, como levantamos o serviço do nginx? simples, digite o comando **nginx** e acesse novamente o endereço http://localhost:45000


> Trabalhar com containers no início pode ser tão trabalhoso como de fato é :-)

Agora acesse novamente http://localhost:45000 e veja sua nova página.

Porém nós podemos fazer algo melhor sem "encostar" no container, algo interessante como *volumes* que veremos mais em breve.