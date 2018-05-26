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
