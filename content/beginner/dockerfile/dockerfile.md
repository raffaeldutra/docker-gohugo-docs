---
title: Dockerfile
weight: 6
pre: "<b>4.1 </b>"
chapter: false
---

Aqui um exemplo utilizando como base a imagem Nginx que já estavámos utilizando anteriormente com o máximo de comandos que o Dockerfile suporta e que vimos acima.

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
