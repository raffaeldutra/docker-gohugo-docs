---
title: Instalando
weight: 5
pre: "<b>2 </b>"
chapter: false
---

Para instalar Docker CE (Community Edition), você precisa de versão 64 bits.

Agora para instalarmos isso vai depender de bastante coisa, porém vamos trabalhar de maneira genérica, então segue duas formas:

Forma 1.

* Uma máquina virtual (VM): pode ser utilizando Virtualbox, VMware, tanto faz.
  * VM com acesso para internet.
  * VM com placa em modo bridge.  
  * Curl instalado **sudo apt-get install curl --yes**

> Atenção: esta VM precisa ter uma interface em modo bridge para ter acesso aos containers que iremos estudar durante o workshop

Forma 2.

* Se você já for usuário Linux nativo, pode realizar diretamente sem necessitar de máquina virtual.

## Formas de instalar docker

Existem algumas formas de instalar Docker, porém vamos ver as duas mais comuns.


<a name="como-obter-docker"></a>
## Como obter Docker para outros sistemas?

- [Link para documentação oficial](https://docs.docker.com/install/)
    - [Instalando em Windows](https://docs.docker.com/docker-for-windows/install/)
    - [Instalando em Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
    - [Instalando em Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    - [Instalando em MacOS](https://docs.docker.com/docker-for-mac/install/)
