---
title: Criando sua imagem sem Dockerfile
weight: 8
pre: "<b>1.4.1 </b>"
chapter: false
---

Sim, nós também podemos criar imagens sem precisar de Dockerfile. Vamos ver o seguinte:

```
docker run --interactive --tty ubuntu /bin/bash
```

Com este comando nós "entramos" no container. Dentro do container podemos fazer o que quisermos, como adicionar arquivos, remover arquivos, adicionar pacotes e etc.

Vamos então adicionar um pacote. No container, execute:

```
apt-get update && apt-get install curl
```
