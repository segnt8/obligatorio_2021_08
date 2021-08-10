# Obligatorio - Taller de Servidores Linux

### Cambios realizados

## Playbook main.yml de rol common

#Se añadieron los módulos "hosts", "gather_facts" y "become".
#Se añadió el módulo "include_vars" para cargar una lista de variables según la distribución.
#Se utilizó el módulo "package" para la instalación del paquete chrony.
#Las dependencias para cada servidor se instalarán de acuerdo al archivo de cada distribución.
#Se configuró la ruta de la copia del archivo de configuración de chrony
#El servicio de chrony se inicia de acuerdo a la variable cargada en el archivo al principio.
#Se agregó una tarea de handler para reiniciar el servicio chrony

## Playbook bases de datos main.yml

#Se añadieron los módulos "hosts", "gather_facts" y "become".
#Se agregaron dos tareas para cargar variables de configuración y de instalación de paquetes.
#Se añade la tarea de instalación de epel-release
#Los paquetes se instalan en ambos servidores mediante el módulo "package".
#Se especificó mediante condicional la configuración de booleano de SELinux para MySQL.
#Se añadió una tarea para copiar un archivo al directorio root.
#Se especificó el parámetro no_log en la tarea de creación del usuario de base de datos.

## Playbook install_httpd.yml

#Se añadieron los módulos "hosts", "gather_facts" y "become".
#Se incluyeron dos archivos de variables que contienen puerto de apache y de paquetes a instalar.
#El servicio web se iniciará de acuerdo a la distribución mediante una variable.
#Se especificó mediante condicional la configuración de booleano de SELinux para apache.

## Playbook copy_code.yml

#Se añadieron los módulos "hosts", "gather_facts" y "become".
#Se cargan variables desde archivos para descargar desde repositorio y para conectarse a la base de datos
#Se agregó uan tarea para borrar el archivo por defecto index.html

## Template index.php

#Se sustituyeron las variables requeridas para lograr la conexión a la base de datos.

### Utilización del stack

#Se tendrá que contar con una máquina que oficie de controlador.
#Se deberá añadir a los servidores en el archivo "hosts" encontrado en el directorio principal de acuerdo al rol a instalar.
#En cada playbook se deberá cambiar el parámetro del módulo "hosts" para el deseado.
#El primer playbook a instalar deberá ser el del rol common el cual contiene dependencias necesarias para el resto de los playbooks.
#El segundo playbook a correr será el del rol de db.
#El tercer rol de web podrá ser configurado mediante el playbook main.yml, o a través de los playbooks install_httpd.yml y copy_code.yml.
#Al finalizar, se podrá visualizar las bases de datos desde el host web.
