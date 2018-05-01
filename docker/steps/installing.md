### Maneira 1: A maneira Linux simples de ser

```bash
curl -fsSL https://get.docker.com/ | sh
sudo usermod -aG docker <usuario>
```

### Maneira 2: Forma tradicional

Remova a versão antiga (caso tiver).

```
sudo apt-get remove docker docker-engine docker.io
```

Instale os pacotes que permitem que o *apt* possa utilizar repositórios com https

```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

Agora instale a chave GPG do Docker

> Preste atenção na sua distribuição abaixo

```
curl -fsSL https://download.docker.com/linux/$(lsb_release -is | tr '[:upper:]' '[:lower:]')/gpg | sudo apt-key add -
```

Adicione o repositório.

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/$(lsb_release -is | tr '[:upper:]' '[:lower:]') $(lsb_release -cs) stable"
```

Vamos atualizar o index dos pacotes apt

```
sudo apt-get update
```

Vamos instalar a última versão do Docker Community Edition

```
sudo apt-get install docker-ce
```

Vamos testar se está tudo funcionando

```
sudo docker run hello-world
```
