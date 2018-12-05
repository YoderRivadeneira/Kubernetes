![alt text](https://d1.awsstatic.com/PAC/kuberneteslogo.eabc6359f48c8e30b7a138c18177f3fd39338e05.png "Loogo kubernetes")


# Proyecto de Arquitectura de aplicaciones


## Docker: 

Denominados contenedores, o también llamados “virtualización ligera”, en le que usando el mismo SO podemos hacer que las aplicaciones crean que están ellas solas porque están en su carpeta con todas las librerías para esa aplicación y así la aplicación cree que todo lo que ve es todo lo que hay, es la perspectiva que tienen desde dentro aunque desde fuera no se eso.

## Ventajas de Docker:
Se aíslan las aplicaciones.
Es muy ligero no se debe montar un SO por cada uno de los contenedores.
Homogeniza entornos (Tengo mi contenedor en mi SO en ubuntu y le cliente otro linix diferente, al tener docker en su SO le va a funcionar la aplicación).
Ofrece un repositorio: Control de versiones.


Si existe algún fallo del sistema, apagón o algún percance y se cae el SO se caen las aplicaciones. sin embargo eso no debe parar, el servicio debe seguir y para solucionar eso se ponen muchos servidores pero no deben ser réplicas, porque debe ocurrir es que se comuniquen entre ellos  (montar un clúster en el que se distribuyen todos los contenedores)





## KUBERNETES
Es un proyecto open source de Google para la gestión de aplicaciones en contenedores, en especial los contenedores Docker, permitiendo programar el despliegue, escalado, monitorización de los contenedores, etc. A pesar de estar diseñado para contenedores Docker, Kubernetes puede supervisar servidores de la competencia como Amazon o Rackspace. Permite empaquetar las aplicaciones en contenedores y trasladarlos fácil y rápidamente a cualquier equipo para ejecutarlas. Kubernetes es similar a Docker Swarm, que es la herramienta nativa de Docker para construir un clúster de máquinas. Fue diseñado para ser un entorno para la creación de aplicaciones distribuidas en contenedores. Es un sistema para la construcción, funcionamiento y gestión de sistemas distribuidos. 

## CARACTERÍSTICAS 

Las principales características de Kubernetes son:

• Distribución inteligente de contenedores en los nodos. 
• Otra característica es que tiene un fácil escalado, tanto horizontal como vertical, sólo hay que especificar con un comando la cantidad de nuevas aplicaciones. 
• Administración de cargas de trabajo ya que nos provee de balanceadores de cargas. 
• Facilita la gestión de gran cantidad de servicios y aplicaciones. 
• Provee de alta disponibilidad. 
• Muy modular, mucha flexibilidad.

## Arquitectura:

Un clúster de Kubernetes está formado por nodos o minions (kubelet) y por los componentes del Master (APIs, scheduler, etc) encima de una solución de almacenamiento distribuido.

![alt text](https://unpocodejava.files.wordpress.com/2015/12/image008.jpg "Arquitecctura de Kubernetes")


## KUBERNETES NODE 
En el nodo se ejecutan todos los componentes y servicios necesarios para correr aplicaciones y balancear el tráfico entre servicios (endpoints). Es una máquina física o virtual que ejecuta Docker, dónde pods pueden ser programados. Docker se encarga de los detalles de la descarga de imágenes y funcionamiento de los contenedores.
El nodo o minion provee los siguientes servicios: 
Docker o rkt: son los motores de contenedores que funcionan en cada nodo descargando y corriendo las imágenes docker.
Kubelet: Cada nodo corre un Kubelet, que es el responsable del registro de cada nodo y de la gestión de los pods corriendo en ese nodo.
cAdvisor: Es un agente de uso de los recursos y análisis que descubre todos los contenedores en la máquina y recoge información sobre CPU, memoria, sistema de ficheros y estadísticas de uso de la red.
Flannel: provee redes y conectividad para los nodos y contenedores en el clúster. Utiliza etcd para almacenar sus datos.
Proxy (Kube-proxy): provee servicios de proxy de red. Cada nodo también ejecuta un proxy y un balanceador de carga.
## KUBERNETES MASTER 
El servidor master va a controlar el clúster. Es el punto donde se otorga a los servicios de clúster información de todos los nodos, y corre los siguientes servicios:
etcd: es una base de datos altamente disponible (distribuida en múltiples nodos) que almacena claves-valor en el que Kubernetes almacena información (configuración y metadatos) acerca de él mismo, pods, servicios, redes, etc, para que pueda ser utilizada por cualquier nodo del clúster.
Scheduler (Kube-scheduler): se encarga de distribuir los pods entre los nodos, asigna los pods a los nodos. Lee los requisitos del pod, analiza el clúster y selecciona los nodos aceptables.
API Server (kube-apiserver): Provee la API que controla la orquestación de Kubernetes, y es el responsable de mantenerla accesible. El apiserver expone una interfaz REST que procesa operaciones como la creación/configuración de pods y servicios, actualización de los datos almacenados en etcd (es el único componente que se comunica con etcd). 
Controller manager: es un servicio usado para manejar el proceso de replicación definido en las tareas de replicación. Los detalles de estas operaciones son descritas en el etcd, dónde el controller manager observa los cambios. Cuando un cambio es detectado, el controller manager lee la nueva información y ejecuta el proceso de replicación hasta alcanzar el estado deseado.

## Pods

La unidad más pequeña de kubernetes son los Pods , con los que podemos correr contenedores. Un pod representa un conjunto de contenedores que comparten almacenamiento y una única IP.Por lo tanto parece razonable que podamos tener más de un contenedor compartiendo almacenamiento y direccionamiento, que llamamos Pod. Además existen más razones:

![alt text](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQODto-5y4ALioLQBR9BY7pnwY6twC7s8PeFR1qmvRuWAcU6QKC "pods")

## Imlementacin de kubernetes

### Instalacion :

$ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | Sudo apt-key add

$ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | Sudo apt-key add

$ sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"

$ sudo apt install kubeadm

### Iniciar el servidor maestro :
![alt text](https://linuxconfig.org/images/01-kubernetes-ubuntu-18.04-bionic.png "pods")

A continuación, como la salida de inicialización del nodo maestro de Kubernetes sugirió ejecutar los siguientes comandos como usuario regular para comenzar a usar el clúster de Kubernetes:

kubernetes-master: ~ $ mkdir -p $ HOME / .kube

kubernetes-master: ~ $ sudo cp -i /etc/kubernetes/admin.conf $ HOME / .kube / config

kubernetes-master: ~ $ sudo chown $ (id -u): $ (id -g) $ HOME / .kube / config

### Unirse a Kubernetes Cluster :

kubernetes-slave: ~ $ sudo kubeadm join 10.1.1.9:6443 --token qdjnpd.5glu39uxr92xarsj --discovery-token-ca-cert-hash sha256: ed068415pcpc1818ff425ceae6c84a56c05f7b45ccccccp118caf425ceae6c85a5c7pac

![alt text](https://linuxconfig.org/images/03-kubernetes-ubuntu-18.04-bionic.png "pods")


### Obtener Nodos :

kubernetes-master: ~ $ kubectl get nodos

![alt text](https://linuxconfig.org/images/04-kubernetes-ubuntu-18.04-bionic.png "pods")

### Deslegando Docker en Kubernetes:

kubernetes-master: ~ $ kubectl run --image = nginx nginx-server --port = 80 --env = "DOMAIN = cluster"

kubernetes-master: ~ $ kubectl expose despliegue nginx-server --port = 80 --name = nginx-http

kubernetes-slave: ~ $ sudo docker ps

![alt text](https://linuxconfig.org/images/05-kubernetes-ubuntu-18.04-bionic.png "pods")


Para confirmar que nuestro nuevo servicio Nginx está en funcionamiento, enumere todos los servicios disponibles en su nodo maestro y use el curlcomando para realizar una solicitud HTTP en su CLUSTER IP:


kubernetes-master: ~ $ kubectl get svc

kubernetes-master: ~ $ curl -I 10.101.230.239


![alt text](https://linuxconfig.org/images/06-kubernetes-ubuntu-18.04-bionic.png "pods")

## CONLUSIONES :

Podemos resumir que las funciones principales de Kubernetes son:
Programar
Iniciar
Administrar
Escalar contenedores en múltiples hosts

## IMPORTANCIA DE KUBERNETES :  
Los contenedores son una forma poderosa y flexible para implementar de manera segura y confiable aplicaciones y microservicios para extender y expandir los servicios de su compañía.
Con Kubernetes, esos contenedores pueden provenir de un número de fuentes (Docker, Windows Server Containers, etc.), lo que hace que Kubernetes sea increíblemente flexible y significativamente más complejo.


