<p align="center"><img src="https://www.shareicon.net/data/128x128/2015/10/06/112721_development_512x512.png"></p>

<p align="center">
<a href="https://img.shields.io/badge/License-GPL%20v3-blue.svg"><img src="https://img.shields.io/badge/License-GPL%20v3-blue.svg" alt="License"></a>
</p>

# Leia

Por enquanto ainda estou formatando este documento, retorne em breve

# Sumário

- [Docker](#docker)
    - [TL;DR (Too Long, Didn't Read)](#tldr-too-long-didnt-read)
    - [Como obter Docker?](#como-obter-docker)
    - [Como criar uma imagem](#como-criar-uma-imagem)
    - [Como publicar a documentacao](#como-publicar-os-docs)
    - [Como rodar um servidor](#como-rodar-um-servidor)

## TL;DR (Too Long, Didn't Read)

Baixe Docker com o comando mágico (funciona somente em Sistemas Operacionais). Windows, sorry :-)

```bash
curl -fsSL https://get.docker.com/ | sh
```

<a name="como-obter-docker"></a>
## Como obter Docker?

- [Link para documentação oficial](https://docs.docker.com/install/)
    - [Instalando em Windows](https://docs.docker.com/docker-for-windows/install/)
    - [Instalando em Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
    - [Instalando em Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    - [Instalando em MacOS](https://docs.docker.com/docker-for-mac/install/)


# Como criar projeto Hugo

Rode em algum lugar o comando abaixo, mas atente que ele irá criar um diretório de nome "docker.rafaeldutra.me/hugo", altere caso necessário.

```bash
docker run --rm -detached --volume $(pwd):/docker.rafaeldutra.me raffaeldutra/docker-docs /usr/local/bin/hugo new site /docker.rafaeldutra.me/hugo
```

Dentro deste diretório trabalhe normalmente, ele contêm a estrutura básica para funcionamento do Hugo.

Agora adicione o seu tema para o diretório de themes.

<a name="como-criar-imagem"></a>
## Como criar uma imagem

Construa a imagem que irá rodar com o comando abaixo

```bash
docker build -t raffaeldutra/docker-docs .
```

<a name="como-publicar-site"></a>
## Como publicar os docs

Publicação de código, ou seja, transforma todos os arquivos.md para HTML

```bash
docker run -it -v $(pwd):/src -v $(pwd)/public:/src/public raffaeldutra/docker-docs
```

<a name="como-rodar-um-servidor"></a>
## Como rodar um servidor

Aqui é possível rodar Hugo em modo servidor

```bash
docker run -it -v $(pwd):/src -v $(pwd)/public:/src/public -p 1313:1313 raffaeldutra/docker-docs /gohugo.sh -s
```
