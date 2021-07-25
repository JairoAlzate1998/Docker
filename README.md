# Docker

## Clase del 19 de Julio del 2021

Docker es una herramienta que facilita el despliegue de aplicaciones de una forma muy rapida.
Esto permite que el tiempo entre la codificación del codigo e implementarlo, ya sea para realizar pruebas o ya para producción sea mucho mas sencillo.
Docker trabaja mediante contenedores, el cual es simplemente un tipo de almacenamiento liviano, el los cuales se puede guardar todas las dependencias que nuestra apliacion necesite para ejecutarse correctamente. Esto permite que estos no necesiten de un hipervisor, si no que  se puedan ejecutar directamente en el nucleo de la maquina host.
Esto conlleva que necesitemos muchos menos recursos de hardware que si tuvieras que utilizar maquinas virtuales, aunque estos mismos contenedores se guarden en maquinas virtuales proporcionadas por plataformas como AWS, Microsoft Azure o Google Cloud. Con ayuda de estas plataformas podemos poner a correr muchos contenedores a la vez.

Con ayuda de docker podemos realizar la entrega rapida y consistente de aplicaciones, puesto que, optimiza el ciclo de vida del desarrollo del software, esto porque nos crea entornos estandarizados y tambien nos ayuda con la integración continua de la apliaciones.

Entonces Docker nos permite que, un grupo de desarrolladores generen codigo en contenedores y lo compartan con otras personas, estas verfirican y encuentran si encuentran errores los corregien y los vuelven a subir al entorno de pruebas y validación, y pasando esto, la aplicación ya estaria lista para el usuario final.

Docker utiliza herramientas tales como: 
 * Kubernetes
 * Swarm 
 * Mesosphere Datacenter (DC/OS)
 * Google Kubernetes Engine

## Clase del 21 de Julio del 2021

### Instalación de Docker

Iniciamos con la instalación de Docker dentro de una maquina virtual Ubuntu con los siguientes comandos: 

`sudo apt-get update` - > Esto para actualizar los paquetes del Ubuntu

`sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release` -> Esto para instalar los paquetes necesarios para la instalación.
 
Añadimos la llave GPG del docker con el siguiente comando: `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`.
 
Utilizamos el siguiente comando para configurar el repositorio estable: `echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`


### Instalar Docker Engine 

Lo hacemos con el siguiente comando: `sudo apt-get install docker-ce docker-ce-cli containerd.io`

Una vez tengamos esto podemos realizar la prueba del "Hola mundo" con el siguiente comando: `sudo docker run hello-world` y obtenemos el siguiente resultado:

        ** 
        Hello from Docker!
            This message shows that your installation appears to be working correctly.

            To generate this message, Docker took the following steps:
            1. The Docker client contacted the Docker daemon.
            2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
            (amd64)
            3. The Docker daemon created a new container from that image which runs the
            executable that produces the output you are currently reading.
            4. The Docker daemon streamed that output to the Docker client, which sent it
            to your terminal.

            To try something more ambitious, you can run an Ubuntu container with:
            $ docker run -it ubuntu bash

            Share images, automate workflows, and more with a free Docker ID:
            https://hub.docker.com/

            For more examples and ideas, visit:
            https://docs.docker.com/get-started/
        **

Para saber que version de docker instalamos en nuestro sistema utilizamos el siguiente comando: `sudo docker version` y obtenemos lo siguiente: 

        ** 
        Client: Docker Engine - Community
        Version:           20.10.7
        API version:       1.41
        Go version:        go1.13.15
        Git commit:        f0df350
        Built:             Wed Jun  2 11:56:38 2021
        OS/Arch:           linux/amd64
        Context:           default
        Experimental:      true

        Server: Docker Engine - Community
        Engine:
        Version:          20.10.7
        API version:      1.41 (minimum version 1.12)
        Go version:       go1.13.15
        Git commit:       b0f5bc3
        Built:            Wed Jun  2 11:54:50 2021
        OS/Arch:          linux/amd64
        Experimental:     false
        containerd:
        Version:          1.4.8
        GitCommit:        7eba5930496d9bbe375fdf71603e610ad737d2b2
        runc:
        Version:          1.0.0
        GitCommit:        v1.0.0-0-g84113ee
        docker-init:
        Version:          0.19.0
        GitCommit:        de40ad0
        **
 
