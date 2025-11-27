# Docker

## O que é Docker?

Docker é uma plataforma que permite criar, distribuir e executar aplicações dentro de **containers**.Pense em um container como uma "caixa" isolada que contém tudo que sua aplicação precisa para funcionar: código, bibliotecas, dependências e configurações.

**Por que usar Docker?**

- **Portabilidade**: "funciona na minha máquina" vira "funciona em qualquer máquina"
- **Isolamento**: cada container é independente e não interfere em outros
- **Consistência**: mesmo ambiente em desenvolvimento, teste e produção
- **Eficiência**: containers são mais leves que máquinas virtuais

## Conceitos Fundamentais

- **Imagem**: um "modelo" ou "receita" para criar containers (como uma classe em programação)
- **Container**: uma instância em execução de uma imagem (como um objeto)
- **Dockerfile**: arquivo de texto com instruções para construir uma imagem
- **Docker Hub**: repositório público de imagens Docker



### Docker  Info

**1. Informações do Servidor Docker (Docker Engine)**
- Versão do Docker
    
- Driver de storage (overlay2, btrfs, zfs etc.)
    
- Diretório de armazenamento das imagens
    
- Plugins instalados (network, volume, etc.)
    
- Features habilitadas
    
- Runtime usado (runc, containerd…)
    

 **2. Status do sistema**

- Número de containers:
    
    - rodando
        
    - pausados
        
    - parados
        
- Número de imagens
    
- Número de volumes
    
- Número de redes
    

 **3. Configurações do host**

- Sistema operacional
    
- Kernel
    
- Arquitetura da CPU
    
- Número de CPUs
    
- Memória disponível
    
- Cgroups habilitados
    

 **4. Configuração de rede**

- Driver padrão de rede
    
- IPv4/IPv6 ativos
    
- DNS
    
- Registry mirrors (se houver)
    

**5. Configuração de logs e eventos**

- Logging driver padrão
    
- Limites configurados (caso existam)

Resumo => diagnóstico completo do Docker Engine + ambiente da máquina

### Trabalhando com imagens no docker

Esse comando baixar uma imagem do dockerhub
-  docker pull **image**  -> Ex: docker pull ubuntu

Baixar imagem com uma versão especifica 
- docker pull **image : versão** -> Ex: docker pull node:18

Listar imagens locais
-  docker **images** 

Listar imagens com filtro
- docker **images** --filter **filtro a ser adicionado** -> Ex: [ comando --filter ] (https://medium.com/@mrdevsecops/docker-image-command-part-02-bba3d9bcf734) 

Remover uma imagem 
- docker rmi **image** -> Ex: docker rmi ubuntu

Forçar remoção de uma imagem
- docker rmi -f **image** -> Ex: docker rmi -f ubuntu

Removendo varias imagens 
- docker rmi  **image1** **image2** **image3**  -> Ex: docker rmi ubuntu nginx node

Remover todas as imagens 
- docker rmi $(docker images -q)

Comando create(cria um container a partir da imagem)
-  docker create  **image**

Comando Start(inicia o container)
- docker start **id_container**

docker run = pull(abaixa a imagem se ela não existir) + create + start
-  docker run **image** 

### inspecionar Imagens

serve para **ver informações detalhadas e completas** sobre um **container**, **imagem**, **volume**, **rede** ou qualquer objeto Docker.(a visualização é um JSON)

`docker inspect`

**1. Configurações internas de containers**

- comando que foi usado para iniciar
    
- variáveis de ambiente (`ENV`)
    
- volumes montados
    
- portas expostas
    
- users, working directory
    
- entrypoint e comandos
	
 
 **2. Status atual**

- se está rodando, parado ou reiniciando
    
- uptime
    
- PID do processo principal
    
- recursos usados
    
- restart policy
    

 **3. Rede**

- IP interno do container
    
- Gateway
    
- Rede que está conectado
    
- MAC address
    
- Links, aliases
    

 **4. Imagem**

- ID da imagem
    
- Layers
    
- Arquitetura
    
- Labels
    

**5. Volumes**

- paths mapeados
    
- origem e destino dos volumes
    
- bind mounts

ver detalhes da imagem
- docker inspect <image>  -> Ex: docker inspect ubuntu;
- docker inspect  **id_container** 
- docker inspect  **volume**
- docker inspect  **network**

|Comando|O que mostra|Nível|
|---|---|---|
|**`docker info`**|Informações gerais do **Docker Engine** e do **host**|Global|
|**`docker inspect`**|Informações detalhadas de um **objeto específico** (container, imagem, volume, rede)|Individual|

