# Introdução

Docker revolucionou pela simplicidade de como Software é desenvolvido, testado e adicionado em produção de forma rápida e simples.

O público dessa documentação são aquelas pessoas que já ouviram falar na tecnologia e até quem sabe já se arriscaram no mundo de containers, mas ainda estão com dúvidas de como utilizar e de que forma ela pode se encaixar no seu dia-a-dia.

Vamos no decorrer da documentação instalar Docker, rodar comandos simples, entender o que eles representam, trabalhar com Dockerfile e evoluirmos até lançarmos alguns containers de uma única vez utilizando Docker Compose.

## Docker e seus benefícios

1. Isolamento

O que estiver dentro do container, não irá afetar o restante de seu ambiente.
Utilizando containers separados, cada componente de uma determinada aplicação faz com que você evite conflito de dependências.

2. Reproducibilidade

Uma vez que você consiga rodar o seu container em Docker, você será capaz de executá-lo exatamente da mesma maneira em outro ambiente que tenha Docker, simples assim, ou seja, se você rodar sua aplicação em uma máquina X e logo depois ir para uma máquina Y, você irá rodar sem problemas sua aplicação, pois tudo está encapsulado em uma mesma unidade de "medida", Docker.

3. Gerenciamento de ambientes

Usando Docker é muito fácil você ter diferentes tipos de ambientes, como teste, desenvolvimento, qualidade e produção. Você pode versionar toda sua infraestrutura e ter todo o controle do que está entrando em seu ambiente.

4. Integração contínua

Aqui está um grande ponto do uso Docker. Temos hoje uma vasta quantidade de ferramentas para usarmos como CI (Continuous Integratation), como Jenkins, Bamboo, Travis e etc. Cada vez que seu código fonte é atualizado, essas ferramentas salvam uma nova imagem e podem ir para produção.

Em grande resumo, Docker é uma ferramenta que possibita a criação, deploy e leve gerenciamento de pacotes auto contidos que contêm tudo que é necessário para rodar uma aplicação, como códigos, bibliotecas, configurações de sistemas e dependências e é isso que chamamos de containers.

Cada container é feito deploy com sua própria CPU, memória e recursos de rede.




### Outros comandos para interagir com seu container

Quando iniciamos um container novo, podemos instalar pacotes, editar/apagar/criar arquivos e outras coisas mais, porém temos um problema ao sair do container de forma tradicional pelo terminal pois o container automaticamente será parado assim que você digitar **exit** ou der **control d**. Para resolvermos este problema, podemos utiliazar a combinação de teclas como **control p q**, isso fará com que nosso container continue rodando normalmente e ele não irá parar.

Utilizando este conjunto de teclas, nos vem a seguinte pergunta: "E se eu quero retornar ao container, como faço?".

```
docker attach <id do container> ou <nome>
```

Excelente, tudo funcionando como esperado, mas e se eu quero apenas listar algum arquivo ou quem sabe visualizar e assim por diante? ou seja, quero apenas fazer algo breve no meu container?

```
docker exec <id do container> ou <nome> ls -la /usr/share/nginx/html
```

* Como faço para visualizar o log de um container?

```
docker logs <id do container> ou <nome>
```

* Como faço para visualizar status do meu container?

```
docker stats <id do container> ou <nome>
```

* Como faço para visualizar informações detalhadas de um container?

```
docker inspect <id do container> ou <nome>
```

## Criando imagens

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
