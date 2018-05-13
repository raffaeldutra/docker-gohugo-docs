---
title: Criando nossa imagem utilizando o Dockerfile
weight: 7
pre: "<b>1.3.2 </b>"
chapter: false
---

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
