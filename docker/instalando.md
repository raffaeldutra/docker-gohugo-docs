## Pré requisitos

Isso vai depender de bastante coisa, porém vamos trabalhar de maneira genérica, então segue a lista:

* Uma máquina virtual (VM): pode ser utilizando Virtualbox, VMware, tanto faz.
  * VM com acesso para internet.
  * VM com placa em modo bridge  
* Se você já for usuário Linux nativo, pode realizar diretamente sem necessitar de máquina virtual.

> Atenção: esta VM precisa ter uma interface em modo bridge para ter acesso aos containers que iremos estudar durante o workshop.


## A maneira Linux simples de ser

Baixe Docker com o comando mágico (funciona somente em Sistemas Operacionais). Windows, sorry :-)

```bash
curl -fsSL https://get.docker.com/ | sh
```

<a name="como-obter-docker"></a>
## Como obter Docker para outros sistemas?

- [Link para documentação oficial](https://docs.docker.com/install/)
    - [Instalando em Windows](https://docs.docker.com/docker-for-windows/install/)
    - [Instalando em Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
    - [Instalando em Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    - [Instalando em MacOS](https://docs.docker.com/docker-for-mac/install/)
