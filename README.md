# lasdai-ros-kinect-doc
# Repositorio de documentación - Proyecto de grado ULA Ingeniería de Sistemas - LaSDAI #

## Estudio e Implementación de una plataforma de Software que permita generar Mapas para la Navegación de un Robot Móvil

### ¿Qué es?

Este repositorio contiene la memoria escrita del desarrollo de mi proyecto de grado, como requisito final para obtener el título de Ingeniero de Sistemas, mención Sistemas Computacionales, en la Universidad de Los Andes.

### ¿Cómo se usa?

Si deseas obtener el código en LaTeX para trabajar en tu propia tesis/proyecto de grado, puedes descargar el repositorio completo usando el botón "Download ZIP" a la derecha o clonando el repositorio con tu herramienta Git favorita y utilizar el contenido de la carpeta denominada "01_propuesta_proyecto" o "02_version_preliminar" para realizar la propuesta del proyecto de grado o el proyecto de grado como tal, respectivamente.

Ahora bien, si deseas utilizar el producto investigado en el desarrollo del proyecto, sigue leyendo.

### ¿Cómo se instala?

Para instalar, es necesario contar con la misma versión del sistema operativo usado al desarrollar el proyecto; en este caso, Ubuntu 14.04 de 64 bits (los resultados podrían variar dependiendo del sistema operativo que uses). En adelante, se asume que el sistema operativo es el indicado y que está correctamente configurado.

El proceso de instalación de ROS está excelentemente documentado en su wiki oficial accesible desde http://wiki.ros.org/ROS/Installation, por lo cual seguimos los pasos tomando nota de cualquier dependencia faltante o error.

Para comenzar, en el enlace previamente mencionado, hacemos clic en "Indigo installation instructions", puesto que es la versión de soporte extendido y es la compatible con la versión instalada de Ubuntu.

Una vez allí, bajo el apartado "Supported", hacemos clic en "Ubuntu".

En adelante, solamente seguimos los siguientes pasos haciendo énfasis en la versión instalada de Ubuntu, tomados directamente del sitio:

1. Configure sus repositorios de Ubuntu

 Configure sus repositorios de Ubuntu para activar los repositorios "restricted", "universe" y "multiverse". La guía de configuración de repositorios de Ubuntu, disponible en el siguiente enlace https://help.ubuntu.com/community/Repositories/Ubuntu (en inglés) detalla adecuadamente los pasos necesarios.

2. Configure el archivo sources.list

 Configure su computador para aceptar software desde packages.ros.org. Esta distribución de ROS **sólo** soporta Saucy (Ubuntu 13.10) y Trusty (Ubuntu 14.04) para paquetes Debian.

 ```bash
 sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
 ```
3. Configure sus llaves

 ```
 sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
 ```
4. Instalación

 Primero debe asegurarse que su índice de paquetes Debian esté actualizado:
 ```bash
 sudo apt-get update
 ```

 Si está utilizando Ubuntu Trusty 14.04.2 y experimenta problemas con las dependencias durante la instalación de ROS, quizás deba instalar dependencias adicionales del sistema.  
 **Advertencia: No instale estos paquetes si está utilizando Ubuntu 14.04, ya que destruirá su servidor X (gráfico):**  
 ```bash
 sudo apt-get install xserver-xorg-dev-lts-utopic mesa-common-dev-lts-utopic libxatracker-dev-lts-utopic libopenvg1-mesa-dev-lts-utopic libgles2-mesa-dev-lts-utopic libgles1-mesa-dev-lts-utopic libgl1-mesa-dev-lts-utopic libgbm-dev-lts-utopic libegl1-mesa-dev-lts-utopic
 ```  
 **Advertencia: No instale los paquetes anteriores si está utilizando Ubuntu 14.04, ya que destruirá su servidor X (gráfico). Alternativamente, intente instalar sólo lo siguiente para corregir problemas de dependencias:**  
 ```bash
 sudo apt-get install libgl1-mesa-dev-lts-utopic
 ```
 Existen muchas bibliotecas y herramientas en ROS. Se han provisto cuatro configuraciones por defecto para iniciar. También se pueden instalar paquetes de ROS de forma individual.
 
  * Instalación de Escritorio Completa: (Recomendada): ROS, rqt, rviz, bibliotecas genéricas para robots, simuladores 2D/3D, navegación y percepción 2D/3D  
  Indigo usa Gazebo 2, la cual es la versión por defecto en Trusty y es la recomendada. Si desea actualizar a Gazebo 3 vea las instrucciones en http://wiki.gazebosim.org/wiki/Install/Gazebo_and_ROS#Gazebo_3.x_series acerca de cómo actualizar el simulador.

  ```bash
  sudo apt-get install ros-indigo-desktop-full
  ```
  * Instalación de Escritorio: ROS, rqt, rviz, y bibliotecas genéricas para robots.  
  ```bash
  sudo apt-get install ros-indigo-desktop
  ```
  * ROS-Base: (Esencial) Las bibliotecas de paquete, generación y comunicación. No incluye herramientas de entorno gráfico.  
  ```bash
  sudo apt-get install ros-indigo-ros-base
  ```
  * Paquete Individual: También puede instalar un paquete específico de ROS package (reemplace subguiones con guiones del nombre del paquete):  
  ```bash
  sudo apt-get install ros-indigo-PAQUETE
  ```  
  por ejemplo:  
  ```bash
  sudo apt-get install ros-indigo-slam-gmapping
  ```  
  Para listar paquetes disponibles, use:  
  ```bash
  apt-cache search ros-indigo
  ```
5. Inicialice rosdep  

 Antes de poder utilizar ROS, se debe inicializar rosdep. rosdep permite instalar dependencias del sistema con facilidad para código fuente que desee compilar y es requerido para poder ejecutar algunos componentes centrales en ROS.  
 ```bash
 sudo rosdep init
 rosdep update
 ```
6. Configuración de entorno  

 Es conveniente si las variables de entorno de ROS son agregadas automáticamente a su sesión Bash cada vez que se invoca un nuevo terminal:  
 ```bash
 echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc
 source ~/.bashrc
 ```  
 Si tiene más de una distribución de ROS instalada, `~/.bashrc` sólo debe tomar como fuente el `setup.bash` para la versión que esté en uso actualmente.

 Si simplemente desea cambiar el entorno del terminal actual, puede escribir:  
 ```bash
 source /opt/ros/indigo/setup.bash
 ```  
7. Obtener rosinstall  

 rosinstall es una herramienta de línea de comandos frecuentemente utilizada en ROS que es distribuida por separado. Le permite descargar con facilidad muchos árboles fuentes para paquetes ROS con un solo comando.

 Para instalar esta herramienta en Ubuntu, ejecute:  
 ```bash
 sudo apt-get install python-rosinstall
 ```
