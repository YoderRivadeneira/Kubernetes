# Kubernetes
Proyecto de Arquitectura de aplicaciones


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

![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

