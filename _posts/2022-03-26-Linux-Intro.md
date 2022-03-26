---
layout: blog
title: 'Una Intro necesaria a Linux'
date: 2022-03-26 19:41:34
categories: blog
tags: Linux
image: '/images/default.jpg'
lead_text: 'In a world without walls and fences, who needs windows and gates?.'
---

# Linux
Que es Linux

## El Kernel.

**Linux Torval**, de  21 años en abril de 1991, empezó a escribir el primer kernel de Linux, intentando hacer un Minix (un Unix pequeño) desde cero, escribe su intención en un foro y pronto se suman muchos entusiastas.  

El 14 de marzo de 1994, salió Linux 1.0.0, que constaba de 176.250 líneas de código, hoy tiene 25.5 M de líneas de código en el linux 5.12

Hoy es esponsoreado por las grandes corporaciones

La pieza de código que controla periféricos, controla los recursos, alrededor de esto se montan los otros programas, con una declaración de principios.  Cada programa hace una sola cosa, pero la hace bien y de documenta todo.

---
## En principio fue la línea de comandos.

El escritor de Ciencia Ficción Neal Stephenson escribió este ensayo interesante, 
[Link para En Principio fue la línea de Comandos](https://www.holaebook.com/book/neal-stephenson-en-el-principio-fue-la-linea-de-comandos.html)

La metáfora de la tienda de Deportivos italianos, frente a la de bicicletas con motor y la comunidad de hippies que arma tanques de última generación, que tienen la estética de los deportivos italianos (de hecho ultimamente los deportivos copian a Linux), gastan menos que la bicicleta y son **gratis**.

Lo que comienza como una religión de hippies fundamentalistas termina el 9 de julio del 2019 cuando **IBM** anuncia la compra de **RedHat** en 34 mil millones de dólares. [IBM compró RedHat](https://www.redhat.com/en/about/press-releases/ibm-closes-landmark-acquisition-red-hat-34-billion-defines-open-hybrid-cloud-future)

---
## Porqué Linux
* Porque muchos servers a los que accedemos, corren **apache**, o **nginx**, y entramos por SSH a hacer cualquier tipo de tareas administrativas o de gestión.  Ver logs puede ser muy tedioso.  Con un par de combinaciones de comandos se simplifica mucho. Todas esas tareas vamos a tener que hacerlas desde la línea de comando.
* Pueden borrarse cientos de miles de archivos con un comando que cabe en una línea y luego dejarlo como tarea programada.
* Cuando se rompe un windows, podes bootear una llave USB con una distribución live y arreglar gran parte de los problemas.
* La filosofía de Linux es hacer programas muy **simples**, muy **específicos**, consumiendo muy **pocos recursos**, que hacen una **sola cosa**, pero **bien**.  
* Esto nos da combinaciones de programas que tienen como entradas la salida de otro.  
* Programas que corren en serie (vía pipe) la salida del primer programa, es la entrada del siguiente y así sucesivamente.
* Programas que corren en paralelo (vía segundo plano)
* Dentro de Bash tenemos cientos de programas instalados por defecto en todas las distribuciones [Li|U]nix, dejamos un listado de apenas algunas.
* La analogía que me gusta mostrar siempre es intentar ver el contenido de un archivo .csv ***-grande-*** en la línea de comando y en Excel.  
* Aparece nuevo Hard diariamente, micro computadoras como raspberry, o tvbox que utilizan microprocesadores de la familia ARM con menor consumo.
* Market share distinto para Desktop `3%`, mobile, servers, supercomputadoras. [Nota wikipedia](https://en.wikipedia.org/wiki/Usage_share_of_operating_systems)
* Licencias, no solo por costos, en linux la licencia GNU permite copiar, usar, distribuir y mejorar un programa, con la sola obligación de seguir el trace de los colaboradores.  Y **costos**
* Customización, no solo estética, que para usuarios de escritorio es muy importante, sino por hacer puntualemente una cosa bien.  Las imágenes para servers no incluyen configuraciones de sonido, ni impresoras, ni entornos gráficos.  Son mas eficientes.
* Encendes una pc con linux instalado hace 3 años y arranca como el primer día.
* Seguridad, la cuota de mercado de virus para linux es casi inexistente.
* El FBI, la NASA, la bolsa de NYC, Facebook, twitter, usan la mayoría red hat enterprise.  Google usa una versión de ubuntu.  El CERN Comisión Europea para la Investigación Nuclear, donde está el mayor colisionador de hadrones del mundo, usa tambien Red Hat Enterprise.

---

## Listado de Archivos
Cuando listamos, podemos agregar parámetros al comando `ls` archivos vemos algo parecido a esto, `-a` agrega la posibilidad de ver ficheros ocultos.

```
[marco@marcocenturion Linux]$ ls -lsa
total 356
  4 drwxr-xr-x  8 marco marco   4096 mar 25 23:42 .git
  4 drwxr-xr-x  2 marco marco   4096 mar 25 20:20 images
296 -rw-r--r--  1 marco marco 302548 mar 25 23:23 index.html
 36 -rw-r--r--  1 marco marco  35149 mar 25 19:42 LICENSE
  8 -rw-r--r--  1 marco marco   8179 mar 26 08:49 README.md
```

    d = directorio
     rwx = Permisos de lectura (r) escritura (w) y ejecución (x) del usuario marco
        rwx = Permisos de lectura (r) escritura (w) y ejecución (x) del grupo marco
            rwx = Permisos del resto de los usuarios

`chmod o+wx README.md` va a permitir que otros puedan leer y "ejecutar" README.md si fuera ejecutable

`chmod g+rx` Permite leer y escribir a este grupo

`chmod g-r` Quita permisos de lectura a este grupo

`chmod g+r,o-rwx` Agrega permiso de lectura al grupo y elimina todos al resto de los usuarios. 

 
`chgrp juan README.md` va a permitir que usuarios del grupo llamado juan puedan leer

---

## find 
Cuando listamos con `find` podemos indicar que solo sean `-file` o tipos puntuales de archivos como ejecutables.  `-name` indica el nombre.  La lógica es la siguiente:

find <directorio> <opciones> <parametros>
    Directorio actual `.` Todo el sistema `/` Desde el home `~`

`find . -name archivo.txt` SI en lugar de -name ponemos -iname para omitir case sensitive.

`find . -type d` (d=directorio f=archivo i=enlace)

`find . -atime 1` (un día desde la última lectura o escritura -mtime desde la    última modificación)

`find . -f -mmin -10` Encontrar un archvio que fue modificado hace menos de 10 minutos. 

`find . -size 10M` exactamente 10 megabites `+1G` mas de un gigabite

`find ~ -type f -size +1G` todos los archivos de mas de 1G (para eliminar)

`finde ~ -executable` buscar ejecutables

La **salida** del comando **find** se la pasamos en este caso a **cat** como **argumento** y le pedimos que numere los renglones.

```
find . -name READ*| xargs cat | grep archivos -n
```


---

## Arbol de carpetas linux
En el árbol de directorios de linux, existen directorios a los que puede acceder un usuario sin privilegios y otros a los que solo puede acceder el super usuario **root**

Usuarios sin permisos
/home/usuario
/var/logs
/var/html
/opt

Solo accede el superusuario o dándole permisos de superusuario a un usuario
/etc
/boot
/root

Directorio Raiz
/

Directorio de arranque, donde se almacenan los ejecutables para que arranque el sistema, la imagen del kernel
/boot

Directorio donde se archivan los ejecutables de sistema
/bin (ejecutables de todos los usuarios)
/sbin (ejecutables solo por root)

Directorio de los dispositivos, ya que todos los dispositivos de linux, son tratados como un archivo, dependiendo de la distribución, estos archivos están dentro de 
/dev

Directorio de configuración del sistema
/etc

Directorio del usuario, por lo general, al crearse un usuario, Linux crea un entorno para ese usuario dentro del cual crea un directorio en 
/home/usuario

Directorio de las librerías (por ejemplo java)
/lib

Directorio de programas que no vienen por defecto en linux
/opt

Directorio de los procesos que están corriendo
/proc

Directorio de los logs
/var/logs

Directorio de temporales
/tmp

Directorio de los programas, los ejecutables, librerías, fuentes, man pages
/usr

Directorio recuperado
/lost+found

---

## stderr stdin stdout pipe y atajos de teclado
|Comando|Utilidad|
|---|---|
|fsc `Tab`|Completa predictivamente el comando fsck y muestra un listado de posibles comandos|
|ls > `archivos.txt`|Envía la salida del comando 'ls' a 'archivos.txt'|
|ls >> `archivos.txt`|Agrega a archivos.txt el resultado de ls|
|cat `archivos.txt` \| grep linux|La salida de 'cat' es la entrada de 'grep'|
|apt update `&&` apt upgrade |Hace un update del sistema y luego upgrade|
|rm * \|| ls |Borra todos los archivos y si falla lista los archivos| 
|Ctrl + 1|Cambia a la TTS 1 de las 7 que tiene|
|Ctrl + c|Termina comando que se está ejecutando|
|Ctrl + z|Suspende un proceso|
|Ctrl + d|Muestra el final de un archivo|
|Ctrl + Alt + t|Abre una nueva terminal|
|&|Al final del comando lo hace correr en segundo plano|

## System
|Comando|Utilidad|
|---|---|
|date|Despliega día y hora|
|uname `-a`|Toda la info del sistema|
|screenfetch|descripción del sistema 2.0|
|ls `-argumentos`|Listado de archivos y directorios|
|cd|Cambia de directorio, `~` es el home|
|pwd|Muestra el directorio actual|
|man `cd`|Manual del comando|
|cd `--help`|Ayuda rápida del comando cd|
|mkdir|Crea un directorio|
|mv `-argumentos`|Mueve archivos y directorios o renombra|
|cp `-argumentos`|Copia archivos y directorios|
|rm|Borra|
|cal|Calendario|
|file `archivo.txt`|Muestra que tipo de archivo|
|history|Historial de comandos en Bash `-n` agrega el número de línea|
|alias|Genera un enlace a un comando con un nombre distinto, puede agregar parámetros|
|set|Información del entorno de usuario|
|halt|Detiene el sistema|
|reboot|Reinicia el sistema|
|exit|Salida de la sesión de usuario|
|free|Muestra la memoria libre de sistema|
|env|Muestra las variables de entorno del usuario|
|bc|Calculadora en línea de comando|
|mc|Midnight Commander clone de Norton Commander|
|tree|Muestra el Arbol de directorio desde donde está parado el usuario|
|clear|Limpia la pantalla|
|echo 'Hola mundo'|Saca por pantalla hola mundo|

## Hardware
|Comando|Utilidad|
|---|---|
|lscpu|Muestra info del Hard y Soft|
|lsblk|Muestra los dispositivos y el punto de montaje|
|lspci|Muestra periféricos conectados a la máquina|
|lsusb|Muestra puertos usb|

## Sistema de paquetes
|Comando|Utilidad|
|---|---|
|yum rpm|Sistema de paquetes de Red hat, Suse, Centos|
|apt deb|Sistema de paquetes Debian, Ubuntu y derivados|
|slapt txz|Sistema de paquetes Slackware|
|pacman|Sistema de paquetes de ArchLinux|
|tar|Empaquedador de archivos sin comprimir|
|gzip|Empaquetador y compresor de archivos|
|7z|Compresor de archivos universal|

## Permisos
|Comando|Utilidad|
|---|---|
|chmod o+x `archivo`|Da permisos de ejecución a otros a este archivo|
|chmod g-r `archivo`|Elminia permisos de lectura al grupo para este archivo|
|chown `usuario archivo`|Cambia el usuario de un archivo|
|chgrp|Cambia el grupo `marco`|
|sha256sum|Algoritmo sha-2 de hash seguro de 256 bits|

## Red
|Comando|Utilidad|
|---|---|
|netstat|Muestra el estado de la red|
|ifconfig|Muestra la configuración de la placa de ethernet|
|iwconfig|Muestra la configuración de la placa de wifi|
|nmap|Muestra los puertos|
|netconf|Muestra la configuración de red|
|ping `host`|Envía una señal a google y espera el regreso|
|ip addr show|Muestra todas las interfaces direcciones IP|
|ip address add xxx.xxx.xxx.xxx dev etc0|Asinga una ip a una tarjeta de red|
|wget file|Baja un archivo|
|dig domino|Obtiene el DNS del dominio|

## Usuarios
|Comando|Utilidad|
|---|---|
|whoami|Que usuario estoy usando|
|adduser o useradd|Agrega un nuevo usuario|
|userdel|Borra usuario|
|su|Cambia de usuario|
|passwd|Cambia la contraseña|
|who|Muestra los usuarios en el sistema|
|id|Datos de identificación del usuario|
|groupadd -|Agrega un grupo de usuario|
|addgroup|Agrega un grupo|

## Gestión de archivos, búsquedas, flags
|Comando|Utilidad|
|---|---|
|*|Todos los archivos|
|*.txt|Todos los archivos con extension txt|
|cat `archivo.txt`|Muestra todo el contenido de archivo.txt|
|more `archivo.txt`|Muestra el contenido de archivo.txt por página|
|head `archivo.txt`|Muestra los 10 primeros renglones de archivo.txt|
|tail `archivo.txt`|Muestra los 10 últimos renglones de archivo.txt|
|wc|Cuenta el contenido de un fichero `-l` líneas `-c` caracteres `-w` palabras|
|locale `file`|Localizar un archivo en el sistema|
|find `parámetros`|Encontrar un archivo según los parámetros|
|grep |Encontrar un patrón dentro de un archivo|
|grep -E 'rojo|negro' | Expresiones regulares|
|tr `'.' '\t'` `archivo.txt`|Cambiar todos los puntos del archivo.txt por tabulados|
|cut `-d, -f4`|Cortar el archivo segun las comas y mostrar el campo 4|
|which `python`|Muestra la versión de Python|
|column|Encolumna los resultados|
|sed 's/esto/aquello/g'|Cambia una cadena por otra|
|sort `Parámetros`|Ordena una lista de archivos sergún parámetros|
|uniq|En un listado ordenado elimina las cadenas repetidas|
|diff `archivo.txt` `archivo1.txt`|Muestra las diferencias entre dos archivos|
|xargs|Ejecuta un comando tomando como entrada la salida de un comando anterior|
|wget|Bajar el contenido de un sitio|
|curl|Traer el codigo html de un sitio|

## Tareas programadas
|Comando|Utilidad|
|---|---|
|cron|Se ejecuta un comando periodicamente un comando|
|at|A determinado momento se ejecuta una sola vez este comando|

## accesos remotos
|Comando|Utilidad|
|---|---|
|ssh `usuario@host -p`|Entra a otra pc por SSH, como Putty en windows|
|ftp|Entra a una pc por protocolo ftp|
|rdesktop|Acceso a otra computadora por Remote Desktop de Windows|
|vnc|Acceso por VNC|

## Procesos
|Comando|Utilidad|
|---|---|
|htop|Listado 'Friendly' de procesos|
|top|Listado de procesos por default en todas las distribuciones|
|time|Mide el tiempo que tarda un proceso en ejecutarse|
|kill|Mata un proceso|
|killall|Mata al proceso por su nombre|
|ps|procesos del usuario|

## Disco
|Comando|Utilidad|
|---|---|
|lsblk|Listado de dispositivos montados|
|fdisk|Formatea particiones|
|df `-h`|Espacio en Disco '-h human readable'|
|dd `if of`|Copia todo el disco completo como imagen|
|mount|Monta un sistema de archivos|
|fsck `.fat .ext3`|Estado y corrección del sistema de archivos|

## Editores: vi, emacs, nano, joe
|Comando|Utilidad|
|---|---|
|touch|Crea un archivo|
|vi `archivo.txt`|Abre archivo.txt con vi, sale con `esc` +wq|


## awk
> Awk es todo un lenguaje que se ejecuta línea por línea

|Comando|Utilidad|
|---|---|


## Scripting
