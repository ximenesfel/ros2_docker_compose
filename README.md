- [Ambiente testado](#Ambiente-testado)
- [Instalação](#Instalação)
- [Uso](#Uso)

# Ambiente testado

- Ubuntu 18.04


# Instalação

- Instalar o docker no computador:

```
sudo apt-get install curl
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

- Realizar esses passos para rodar o docker sem a necessidade do root:

```
sudo groupadd docker
sudo usermod -aG docker "usuario" (Trocar "usuario" pelo nome do seu usuário. Ex: sudo usermod -aG docker ximenes)
```

- Reiniciar o pc para validar a associação acima.

- Instalar o docker-compsoe no computador:

```
sudo apt-get install -y python3-pip
sudo python3 -m pip install docker-compose
```

- Clonar o código no seu pc:

```
sudo apt-get install -y git
git clone https://github.com/ximenesfel/ros2_docker_compose.git
cd ros2_docker_compose
```

- Rodar o docker container:

```
docker-compose up -d
```

- Verificar se o docker está rodando corretamente:

```
docker-compose ps
```

Resposta do comando se tiver rodando corretamente.

```
             Name                        Command           State   Ports
------------------------------------------------------------------------
ros2_docker_compose_listener_1   /ros_entrypoint.sh bash   Up           
ros2_docker_compose_talker_1     /ros_entrypoint.sh bash   Up 
```


# Uso

- Acessar o docker container do talker e rodar o nó do talker:

```
docker-compose exec talker bash 

root@46ef30c4b5eb:~# source /opt/ros/foxy/setup.bash
root@46ef30c4b5eb:~# ros2 run demo_nodes_cpp talker
```

**Saída**

```
root@46ef30c4b5eb:~# ros2 run demo_nodes_cpp talker
[INFO] [1594330232.048259283] [talker]: Publishing: 'Hello World: 1'
[INFO] [1594330233.048328644] [talker]: Publishing: 'Hello World: 2'
[INFO] [1594330234.047572449] [talker]: Publishing: 'Hello World: 3'
[INFO] [1594330235.047197378] [talker]: Publishing: 'Hello World: 4'
[INFO] [1594330236.047004427] [talker]: Publishing: 'Hello World: 5'
[INFO] [1594330237.046455272] [talker]: Publishing: 'Hello World: 6'
[INFO] [1594330238.046172686] [talker]: Publishing: 'Hello World: 7'
[INFO] [1594330239.045808344] [talker]: Publishing: 'Hello World: 8'
[INFO] [1594330240.045715696] [talker]: Publishing: 'Hello World: 9'
[INFO] [1594330241.045615802] [talker]: Publishing: 'Hello World: 10'
```

- Abrir outro terminal, acessar o docker container do listener e rodar o nó do listener:

```
docker-compose exec listener bash 

root@46ef30c4b5eb:~# source /opt/ros/foxy/setup.bash
root@46ef30c4b5eb:~# ros2 run demo_nodes_cpp listener
```

**Saída**

```
root@46ef30c4b5eb:~# ros2 run demo_nodes_cpp listener
[INFO] [1594330503.463405277] [listener]: I heard: [Hello World: 20]
[INFO] [1594330504.463447814] [listener]: I heard: [Hello World: 21]
[INFO] [1594330505.462871338] [listener]: I heard: [Hello World: 22]
[INFO] [1594330506.463367152] [listener]: I heard: [Hello World: 23]
[INFO] [1594330507.462590023] [listener]: I heard: [Hello World: 24]
[INFO] [1594330508.462816494] [listener]: I heard: [Hello World: 25]
[INFO] [1594330509.462714528] [listener]: I heard: [Hello World: 26]
[INFO] [1594330510.462724003] [listener]: I heard: [Hello World: 27]
[INFO] [1594330511.462095458] [listener]: I heard: [Hello World: 28]
[INFO] [1594330512.462176623] [listener]: I heard: [Hello World: 29]
[INFO] [1594330513.462319944] [listener]: I heard: [Hello World: 30]
[INFO] [1594330514.461649984] [listener]: I heard: [Hello World: 31]
[INFO] [1594330515.461729278] [listener]: I heard: [Hello World: 32]

```