# Docker no Linux Deepin

### Removendo versão antigas
```sh
$> sudo apt-get remove docker docker-engine 
```

### Instalando gerenciadores de chaves e ferramentas adicionais
```sh
$> sudo apt-get install apt-transport-https ca-certificates curl python-software-properties software-properties-common
```

### Instalando a chave
```sh
$> curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```

### Adicionando o repositório oficial do *Docker*
```sh
$> sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian wheezy stable"
```

### Atualizando os pacotes
```sh
$> sudo apt-get update
```

### Instalando Docker-ce
```sh
$> sudo apt-get install docker-ce
```

### Adicionando o usuário ao grupo docker
```sh
$> sudo usermod -aG docker $(whoami)
```

### Desligue e ligue a maquina

### Verificando se o docker foi instalado corretamente
```sh
$> sudo docker run hello-world
```
