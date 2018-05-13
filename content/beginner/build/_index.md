---
title: Criando sua imagem com Dockerfile
weight: 8
pre: "<b>5 </b>"
chapter: false
---

Para criamos nossa imagem, precisamos de um arquivo Dockerfile conforme visto [aqui](dockerfile/dockerfile). Com este arquivo podemos criar nossas próprias imagens de uma forma organizada e automatizada.

Para criarmos ela, devemos executar o comando

```
docker build --tag nomeDaImagemQueDeseja:versao.1 .
```

Devemos atentar par duas coisas aqui:

1 - O arquivo Dockerfile deve estar (mas podemos passar parâmetro, mas não vamos discutir isso agora) no mesmo diretório onde você está executando o comando.

2 - Existe sim um . (ponto) final no comando, ele diz de uma maneira simplificada que nosso Dockerfile está neste diretório.
