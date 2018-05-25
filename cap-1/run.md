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

### Nomeando o container (--name "nome_do_container")
```sh 
$> docker run --name wine_db -it debian bash
``` 