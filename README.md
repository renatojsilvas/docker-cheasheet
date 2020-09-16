# Docker cheatsheet

## Containers
- **docker container ls -a** ou **docker container ps -a** -> exibe todos os containers disponíveis na máquina local;
- **docker container ls** ou **docker container ps** -> exibe todos os containers em execução na máquina local;
- **docker container run --name *container-name* -it *image*** -> cria (create), inicia (start) e executa (exec) um container no modo interativo (entra dentro do container) de nome *container-name* a partir da imagem *image*;
- **docker container run --name *container-name* -d *image*** -> cria (create), inicia (start) e executa (exec) um container de nome *container-name* rodando-o em segundo plano (detached mode) a partir da imagem *image*;
- **docker container run --name *container-name* -it --rm *image*** -> cria (create), inicia (start) e executa (exec) um container de *container-name* no modo interativo (entra dentro do container) a partir da imagem *image*, porém o apaga assim que finalizá-lo;
- **docker container create *image*** -> cria um container a partir da imagem *image*;
- **docker container create --name *container-name* -p *output-port*:*container-port* *image*** -> cria um container de nome *container-name* mapeando as portas expostas ao mundo exterior *output-port* e a porta do container *container-port*. *output-port* é a porta acessível no browser;
- **docker container create -it *image* *command*** -> cria um container para ser executado no modo interativo. Use esse comando para criar um container linux, por exemplo.
- **docker container start *container-name*** -> inicia um container de nome *container-name* criado e parado;
- **docker container start -ia *container-name*** -> inicia um container de nome *container-name* no modo interativo; 
- **docker container exec -it *container-name* *command*** -> executa o comando *command* de um container de nome *container-name* em execução. Um exemplo de comando é o bash e é dado por /bin/sh;
- **docker container stop** -> para um container em execução de nome *container-name*;
- **docker container stats *container-name*** -> exibe as estatísticas relativas ao uso de CPU, de memória, de I/O etc, de um container de nome *container-name*;
- **docker container inspect *container-name*** -> inspeciona o container de nome *container-name*;
- **docker container rm *container-name*** -> remove o container de nome *container-name*, desde que o mesmo esteja parado;
- **docker container rm -f *container-name*** -> remove o container de nome *container-name*, mesmo esteja rodando;
- **docker container prune** -> remove todos os containers parados;

## Imagens
- **docker image pull** -> baixa uma imagem do dockerhub;
- **docker image ls** ou **docker images** -> exibe todas as imagens disponíveis na máquina local;
- **docker images -q** -> exibe apenas os ids das imagens;
- **docker image rm *image*** -> apaga a imagem de nome *image*;
- **docker image inspect *image*** -> inspeciona a image *image*;
- **docker images prune -a** -> apaga todas as imagens;
- **docker image build -t *source-image* .** -> cria uma imagem a partir de um arquivo Dockerfile;
- **docker built -t appnetcore:dev -f *Dockerfile-name* .** -> cria uma imagem a partir de um arquivo Dockerfile de nome *Dockerfile-name*;
- **docker image tag *source-image* *dest-image*** -> Tagueia a imagem. Deve ser feito antes de enviar ao dockerhub;
- **docker login** -> Efetua o login no dockerhub;
- **docker image push *image*** -> envia a imagem *image* ao docker hub;

## Volumes
- **docker container run --name *container-name* -d --rm -v *host-folder*:*container-folder* -p *external-port*:*internal-port* *image*** -> cria (create), inicia (start) e executa (exec) um container de *container-name* no modo segundo plano a partir da imagem *image*, apagando-o assim que finalizá-lo. Mapeia as portas externa e interna do container. Mapeia um volume na pasta *container-folder* que pode ser acessado no host na pasta *host-folder*;
- **docker volume create --name *volume-name*** -> cria um volume de nome *volume-name*;
- **docker container run --name *container-name* -d --rm -v *volume-name*:*container-volume-folder* -p *external-port*:*internal-port* *image*** -> cria (create), inicia (start) e executa (exec) um container de *container-name* no modo segundo plano a partir da imagem *image*, apagando-o assim que finalizá-lo. Mapeia as portas externa e interna do container. Mapeia um volume na pasta *container-volume-folder* que pode ser acessado no host através do volume criado;
- **docker container create --name *container-name* -v /*container-folder* *image*** -> cria um container *container-name* e cria uma pasta no container chamada *container-folder*. Essa pasta pode ser compatilhada entre vários containeres. Pode ser usado para compartilhar o mesmo volume entre vários containeres. Não depende de nenhum container;
- **docker container run --name *container-name* --volumes-from *container-name-another-volume* -it *image*** -> cria (create), inicia (start) e executa (exec) um container de *container-name* no modo interativo a partir da imagem *image*. Mapeia um volume que foi criado por outro container *container-name-another-volume*. Esse comando tem como função mapear o mesmo voexitlume para vários containeres, porém ao apagar o container onde foi criado o volume todos os outros perdem acesso ao volume;

## Networks
- **docker network create *network-name*** -> cria uma network personalizada de nome *network-name*;
- **docker network create --driver *driver-name* *network-name*** -> cria uma rede personalizada de nome *network-name* mas não mais no driver padrão bridge e sim no driver *driver-name*
- **docker container run --name *container-name* -it --network *network-name* *image*** -> cria (create), inicia (start) e executa (exec) um container de *container-name* no modo interativo a partir da imagem *image*. Conecta esse container à rede personalizada *newtork-name*
- **docker network connect *network-name* *container-name*** -> conecta a rede *network-name* ao container *container-name*
- **hostname -i** -> em um container alpine, mostra qual o ip do container. Para todo container criado é dado um ip de maneira incremental;


## Docker Compose
- **docker-compose build** -> compila o arquivo docker-compose.yml, verificando se o mesmo está correto e criando a imagem;
- **docker-compose up -d** -> cria, inicia e executa o container com base nas especificações do arquivo docker-compose.yml;
- **docker-compose ps** -> exibe os containeres em execução;
- **docker-compose logs** -> exibe os logs;
- **docker-compose start** -> inicia um container;
- **docker-compose stop** -> para um container;
- **docker-compose pause** -> pausa um container;
- **docker-compose unpause** -> desfaz uma pausa;
- **docker-compose rm** -> remove containeres parados;
- **docker-compose down** -> para e remove contêineres, redes, volumes e imagens criada pelo comando up; 