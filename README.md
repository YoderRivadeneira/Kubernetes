# Kubernetes
Proyecto de Arquitectura de aplicaciones


 ## Introducción:
Las máquinas virtuales [1] permiten el aprovisionamiento dinámico de recursos en centros de datos. Como consecuencia, los usuarios solo pueden pagar por los recursos asignados.
Los servicios en los centros de datos se consumen más a medida que más usuarios se conectan a Internet. Dichos servicios se denominan computación en la nube, definidos por el NIST [http://faculty.winthrop.edu/domanm/csci411/Handouts/NIST.pdf ] como "un modelo para permitir el acceso a la red ubicuo, conveniente y bajo demanda a los recursos informáticos provisionados y liberados rápidamente" (https://www.sciencedirect.com/science/article/pii/S1383762116302752 ).
Los contenedores están reemplazando rápidamente a las máquinas virtuales (VM) como la instancia de proceso de elección en las implementaciones basadas en la nube. La sobrecarga significativamente menor de la implementación de contenedores (en comparación con las máquinas virtuales) a menudo se ha citado como una de las razones para esto (https://ieeexplore.ieee.org/abstract/document/7881642 ).
Para impulsar la adopción de contenedores en la nube se creó  Cloud Native Computing Foundation (CNCF) (https://ieeexplore.ieee.org/document/7270244 . Google usó contenedores por varios años y luego lanzó Kubernetes el cual es un sistema de gestión de código abierto para contenedores y cuenta con el conocimiento de los ingenieros que crearon a Borg (https://www.researchgate.net/publication/280969746_10_Observations_on_Google_Cluster_Trace_2_Measures_for_Cluster_Utilization_Enhancement ) , un administrador de contenedores desarrollado por Google.
