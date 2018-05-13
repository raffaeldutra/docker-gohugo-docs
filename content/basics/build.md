---
title: Criando sua imagem usando Dockerfile
weight: 6
pre: "<b>1.4 </b>"
chapter: false
---

Para criamos nossa imagem, precisamos de um arquivo Dockerfile conforme visto [aqui](dockerfile.md). Com este arquivo podemos criar nossas próprias imagens de uma forma organizada e automatizada.

Para criarmos ela, devemos executar o comando

```
docker build --tag nomeDaImagemQueDeseja:versao.1 .
```

Devemos atentar par duas coisas aqui:

1 - O arquivo Dockerfile deve estar (mas podemos passar parâmetro, mas não vamos discutir isso agora) no mesmo diretório onde você está executando o comando.

2 - Existe sim um . (ponto) final no comando, ele diz de uma maneira simplificada que nosso Dockerfile está neste diretório.

# Criando sua imagem sem Dockerfile

Sim, nós também podemos criar imagens sem precisar de Dockerfile. Vamos ver o seguinte:

```
docker run --interactive --tty ubuntu /bin/bash
```

Com este comando nós "entramos" no container. Dentro do container podemos fazer o que quisermos, como adicionar arquivos, remover arquivos, adicionar pacotes e etc.

Vamos então adicionar um pacote. No container, execute:

```
apt-get update && apt-get install curl
```
