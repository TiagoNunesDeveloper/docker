# Comando **run**

Ele é a porta de entrada do Docker, nele são agrupados diversas funcionalidades básicas como:

- O download automático das imagens não encontradas: ```docker pull```
- A criação do container : ```docker create```
- A execução do container: ```docker start```
- O uso do modo interativo: ```docker exec```

Através dele sempre irá criando novos **containers**.

# Modo Interativo

Esse modo é extremamente útil para processos experimentais, estudo de ferramentas e de desenvolvimento.

### Mostrando os container ativos:
```sh 
$> docker ps
``` 
### Mostrando todos os container que foram executados ou que esteja parado:
```sh 
$> docker ps -a
``` 
### Executando um container e mostrando a versão do seu bash:
```sh 
$> docker run debian bash --version
``` 
### Executando um container e removendo a image logo após a execução:
```sh 
$> docker run --rm debian bash --version
``` 
### Executando o container em modo interativo(i) e tendo acesso ao terminal(t):
```sh 
$> docker run -it debian bash
```
Após isso ele irá entra dentro do terminal do container.

### Nomeando o container (--name "nome_do_container"):
```sh 
$> docker run --name wine_db -it debian bash
``` 
Os container tem nomes únicos

### Listando os containers que foram criados:
```sh 
$> docker ls -a
``` 
### Reutilizando um container previamente criado (a attach):
```sh 
$> docker start -ai wine_db
``` 
### Implementando mapeamento de portas
```sh 
$> docker run -p 8080:80 nginx
``` 
**-p "host:container"**

### Implementando mapeamento de volume
```sh 
$> docker run -p 8080:80 -v $(pwd)/html:/usr/share/nginx/html nginx
``` 
**-v "host:container"**

### Executando em modo *daemon*
```sh 
$> docker run -d --name wine_nginx -p 8080:80 -v $(pwd)/html:/usr/share/nginx/html nginx
``` 
**-d** Iniciando o container em background(modo daemon)

### Parando um container pelo seu nome
```sh 
$> docker stop wine_nginx
```
### Startando um container pelo seu nome:
```sh 
$> docker start wine_nginx
```

### Restartando um container pelo seu nome:
```sh 
$> docker restart wine_nginx
```

### Pegando os logs de um container
```sh 
$> docker logs wine_nginx
```

### Acessando a informação de um container:
```sh 
$> docker inspect wine_nginx
```

### Executando comandos dentro de um container:
```sh 
$> docker exec wine_nginx uname -or
```

