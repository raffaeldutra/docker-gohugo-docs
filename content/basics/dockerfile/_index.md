---
title: Dockerfile
weight: 6
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
