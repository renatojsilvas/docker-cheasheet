# docker-cheasheet

## Containers
- **docker container ls -a** ou **docker container ps -a** -> exibe todos os containers disponíveis na máquina local;
- **docker container ls** ou **docker container ps** -> exibe todos os containers em execução na máquina local;
- **docker container run --name *container-name* -it *image*** -> cria (create), inicia (start) e executa (exec) um container no modo interativo (entra dentro do container) de nome *container-name* a partir da imagem *image*;
- **docker container run --name *container-name* -d *image*** -> cria (create), inicia (start) e executa (exec) um container de nome *container-name* rodando-o em segundo plano (detached mode) a partir da imagem *image*;
- **docker container run --name *container-name* -it --rm *image*** -> cria (create), inicia (start) e executa (exec) um container de *container-name* no modo interativo (entra dentro do container) a partir da imagem *image*, porém o apaga assim que finalizá-lo;
- **docker container create *image*** -> cria um container a partir da imagem *image*;
- **docker container create --name *container-name* -p *output-port*:*container-port* *image*** -> cria um container de nome *container-name* mapeando as portas expostas ao mundo exterior *output-port* e a porta do container *container-port*. *output-port* é a porta acessível no browser;
- **docker container start *container-name*** -> inicia um container de nome *container-name* criado e parado; 
- **docker container exec -it *container-name* *command*** -> executa o comando *command* de um container de nome *container-name* em execução. Um exemplo de comando é o bash e é dado por /bin/sh;
- **docker container stop** -> para um container em execução de nome *container-name*;
- **docker container stats *container-name*** -> exibe as estatísticas relativas ao uso de CPU, de memória, de I/O etc, de um container de nome *container-name*;
- **docker container inspect *container-name*** -> inspeciona o container de nome *container-name*;
- **docker container rm *container-name*** -> remove o container de nome *container-name*, desde que o mesmo esteja parado;
- **docker container rm -f *container-name*** -> remove o container de nome *container-name*, mesmo esteja rodando;
- **docker container prune** -> remove todos os containers parados;

## Imagens
- **docker image ls** ou **docker images** -> exibe todas as imagens disponíveis na máquina local;

## Volumes

## Networks

## Docker Compose