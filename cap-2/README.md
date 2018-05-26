# Produzindo as próprias imagens

## Comandos no gerenciamento de imagens

### Baixando a imagem soliticata:
```sh
$> docker image pull <tag>
```

### Listando todas as imagens já baixadas:
```sh
$> docker image ls
```

### Removendo uma imagem do cache local:
```sh
$> docker image rm <tag>
```

### Informações de uma imagem do cache local:
```sh
$> docker image inspect <tag>
```

### Criando uma nova tag baseada em uma tag anterior ou hash:
```sh
$> docker image build -t <tag>
```

## Construção de uma imagem apartir do `Dockerfile`

### Comando responsável por ler um `Dockerfile`
```sh
$> docker image build -t "nome_da_tag" "pasta_do_Dockerfile"
```
O `Dockerfile` é uma arquivo de instrução para o build de imagens Docker. E o comando *build* exige que o arquivo esteja no mesmo diretório aonde a instrução se encontra.

### Preparando uma imagem com `Dockerfile`:

* **FROM**: Especifica a imagem base a ser utilizada pela nova imagem.
* **LABEL**: Especifica vários metadados para a imagem como o mantenedor.
* **ENV**: Especifica variáveis de ambiente a ser utilizadas durande o *build*.
* **ARG**: Define argumentos que poderão ser informados ao *build* através do parâmetros `--build-arg`.
* **COPY**: Copia arquivos e diretórios para dentro da imagem.
* **ADD**: Similar ao anterior, mas com suporte extendido a URLS. Usado quando a instrução COPY não atenda.
* **RUN**: Executa ações ou comandos durante o *build* dentro da imagem.

### Executando um build apartir da mesma pasta do `Dockerfile`:
```sh
$> docker image build -t wine-nginx .
```

### Executando o container apartir da imagem criada *wine-nginx*:
```sh
$> docker run -p 3333:80 wine-nginx
```

### Criando ARG dentro de uma container:
```Dockerfile
FROM golang
LABEL maintainer="Tiago Nunes <tiagonunes.developer at gmail.com>"

ARG AUTOMACAO_WINE=files
ENV AUTOMACAO_WINE=${AUTOMACAO_WINE}
```
### Gerando a imagem:
```sh
$> docker image build -t auto_wine .
```

### Extraindo o arg passado:
```sh
$> docker run auto_wine bash -c 'echo $AUTOMACAO_WINE' # saída $> files
```

### Alterando o arg passando:
```sh
$> docker image build --build-arg AUTOMACAO_WINE=soma -t auto_wine . # saída $> soma
```

### Extraindo o mantenedor da imagem
```sh
$> docker image inspect --format="{{index .Config.Labels \"maintainer\"}}" auto_wine # saída $> Tiago Nunes <tiagonunes.developer at gmail.com>
```