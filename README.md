# docker-developer
Docker com php/nginx+ postgres ou mysql: para testes e estudo

![image](https://user-images.githubusercontent.com/1526849/146829286-0935299f-a11d-401e-89e6-a74886800940.png)


# Iniciar
Ter instalado docker/docker-compose

1º Clonar o repositório

2º Copiar o arquivo .example_env para .env

OBS * docker-compose.yml lê as configurações de banco no arquivo .env

```
$ docker-compose up -d
```
Vai baixar as imagens, e super os containers do docker separadamente e ligados por uma rede interna

# Configurações
Na pasta docker-compose, existe uma estrutura de mais duas pastas são elas:

![image](https://user-images.githubusercontent.com/1526849/146827316-46e65221-e722-4fa5-89cd-49d31e2d830b.png)

nginx: contém o arquivo app.conf, com as configurações do nginx
php: contém o arquivo php.ini, com as configurações do php

Esses arquivos são mapeados no DockerFile, os conteiners usa essas configurações

# Nginx
Está configurado para porta 80 interna e externa 8000 apontando para pasta public.

# Banco de dados (default: Postgres)
Está configurado para porta 5432 interna e externa 5434.
Seu diretório está mapeado como um volume em docker-compose/postgres

OBS* pode ser utilizado mysql ou qualquer outro, porem a configuração do arquivo docker-compose.yml já tem um exemplo usando mysql.

# PHP 7.4*
DockerFile está usando a imagem do php 7.4.
Porem a mesma pode ser alterada para utilização de uma outra versão do php se assim preferir.

* OBS Qualquer alteração do DockerFile, vai ser preciso realizar 
```
docker-compose build 
```
para que a alteração seja refletida

#DockerFile
Além da imagem do php, o Dockerfile já está com a instalação do composer.
Para rodar comandos do composer ou qualquer outro comando dentro do container:
```
docker-compose exec app composer --version
```

# Comandos
```
docker-compose build
docker-compose up -d
docker-compose exec app composer --version
docker-compose down
```
