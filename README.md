![alt text](https://d1.awsstatic.com/PAC/kuberneteslogo.eabc6359f48c8e30b7a138c18177f3fd39338e05.png "Loogo kubernetes")


Proyecto de Arquitectura de aplicaciones





![alt text](https://www.docker.com/sites/default/files/vertical.png "Loogo docker")





 ## Introducción:
Las máquinas virtuales [1] permiten el aprovisionamiento dinámico de recursos en centros de datos. Como consecuencia, los usuarios solo pueden pagar por los recursos asignados.
Los servicios en los centros de datos se consumen más a medida que más usuarios se conectan a Internet. Dichos servicios se denominan computación en la nube, definidos por el NIST [http://faculty.winthrop.edu/domanm/csci411/Handouts/NIST.pdf ] como "un modelo para permitir el acceso a la red ubicuo, conveniente y bajo demanda a los recursos informáticos provisionados y liberados rápidamente" (https://www.sciencedirect.com/science/article/pii/S1383762116302752 ).
Los contenedores están reemplazando rápidamente a las máquinas virtuales (VM) como la instancia de proceso de elección en las implementaciones basadas en la nube. La sobrecarga significativamente menor de la implementación de contenedores (en comparación con las máquinas virtuales) a menudo se ha citado como una de las razones para esto (https://ieeexplore.ieee.org/abstract/document/7881642 ).
Para impulsar la adopción de contenedores en la nube se creó  Cloud Native Computing Foundation (CNCF) (https://ieeexplore.ieee.org/document/7270244 . Google usó contenedores por varios años y luego lanzó Kubernetes el cual es un sistema de gestión de código abierto para contenedores y cuenta con el conocimiento de los ingenieros que crearon a Borg (https://www.researchgate.net/publication/280969746_10_Observations_on_Google_Cluster_Trace_2_Measures_for_Cluster_Utilization_Enhancement ) , un administrador de contenedores desarrollado por Google.

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















