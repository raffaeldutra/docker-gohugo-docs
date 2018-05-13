---
title: Rodando um container
weight: 7
pre: "<b>3.2 </b>"
chapter: false
---

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
