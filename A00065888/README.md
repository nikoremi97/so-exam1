# Parcial 1

**Nombre:** Nicolas Recalde   
**Código:** A00065888  
**Github URL:**  https://github.com/nikoremi97/so-exam1/tree/A00065888/A00065888

## Descripción

El primer parcial del curso sistemas operativos trata sobre el manejo de los comandos de Linux, virtualización y el uso de las características de CentOS7

## Desarrollo

## PUNTO 3

 * sum_all_numbers
 Creo el archivo #sum-me.txt#
  
  ![][1]  
   
  y sumo la lista de números en el archivo con el comando awk '{s+=$1} END {print s}' sum-me.txt
  
  ![][2]  
    
* replace_spaces_in_filenames  
uso el comando ls|sed 's| |\.|g'
  ![][3]  
    
* reverse_readme  
  creo un archivo con el nombre "README.txt" y lo leo
  ![][4]  
  ahora lo leo en orden de lineas al revés  con el comando tac
  ![][5]  
    
* remove_duplicated_lines  
 creo el archivo "eliminarrepetidas.txt" 
 ![][6]  
 borro las lineas repetidas con el comando cat eliminarrepetidas.txt | uniq | awk '!x[$0]++'
 ![][7]  
    
 * disp_table  
 creo el archivo "columns.txt" con la información del challenge y con el comando column -ts ',' columns.txt* hago que se vuelvan columnas
 ![][8]  
    
## PUNTO 4
Crear un script que realice una descarga de un libro de  https://www.gutenberg.org cada 5 minutos, y si ya existe un libro en el directorio, éste debe ser reemplazado.  
El formato en que se presentan las url de  https://www.gutenberg.org cambian a partir del libro #4000 es por esto que el escript solo funciona para libros entre el 0 y el 4000.
Primero creo el script llamado "downloader.sh", lo compilo y verifico si efectivamente está guardando libros. El comando wget ya reemplaza el archivo si tiene el mismo nombre.
![][9]
![][10]  
Ahora falta ordenarle al sistema ejecutar el script cada 5 minutos. Para esto usamos *crontab* . "Cron es el administrador de procesos, Cron lee en un archivo de texto plano llamado Crontab en donde se guardan una lista de comandos creados por el usuario ha ser ejecutados" (www.desarrollolibre.net, 2017).   
![][11]  
defino la actividad del crontab y el parametro "*/5*" hace que se ejecute cada 5 minutos
![][12]  
y verifico que se haya descargado el libro   
![][13]

## PUNTO 5
Explicación del código del repositorio https://github.com/jvns/kernel-module-fun/blob/master/rickroll.c  
El propósito del script, como lo muestra el video https://www.youtube.com/watch?v=efEZZZf_nTc, es reemplazar a todos los archivos .mp3 por el tema *Never gonna give you up*, algo conocido como "Rickrollear". El siguiente paso es describir como funciona este script...  
Primero hay que tener en cuenta que para instalar un nuevo driver al kernel se deben tener dos modulos, el de inicio y el de fin, que serían estos:  
![][18]  
El module_init() define que método se ejecuta cuando se inicia el driver, en este caso es el que permite hacer el *Rickrolleo*. El module_exit() define que método se ejecutará cuando se desinstale el driver, o sea, desactivar la función de *Rickrollear* cada vez que abra una canción.   
Ahora hablemos del código del driver...  

  
![][14]  
En la primera parte, simplemente se definen las librerías a utilizar, una ruta estática para el archivo de la canción Never gonna give you up, y los parámetros de los módulos del kernel, a los cuales se les cambia los permisos por los parámetro (www.linux.com, 2017).  
![][15]  
En esta parte *cr0* es un registro en el sistema que controla las llamadas al sistema, y posteriormente hará un cambio en ellas, por eso necesita cambiar el registr para hacerlo libremente. y se hacen llamados a metodos definidos posteriormente.
Lo que hace la linea "asmlinkage long rickroll_open(const char user filename, int flags, umode_t mode); es ejecutar un método que busca los archivos en formato .mp3 para dar su verdadero syscall, y que pueda ser reemplazado por el de la famosa canción. 
  
![][16]  
En esta parte es donde se hacen los cambios en la tabla de syscalls. Primero se verifica si existe el archivo con la canción para el *Rickrolleo* . La linea "sys_call_table = find_sys_call_table();" ejecuta un método que asigna la locación en memoria de syscalls. Se verifica si se encontró la dirección de la tabla en el memoria. Por último se desactiva la protección de los registros y se reemplaza la syscall original por la que abre el archivo de *Never gonna give you up* y se reactiva la protección.  
  
![][17]  
Por último, se tiene un método que restaura a la normalidad el kernel, para que la función del *Rickrolleo* sea desactivada y todo funcione como antes.


## Referencias

https://cmdchallenge.com/
https://stackoverflow.com/questions/2702564/how-can-i-quickly-sum-all-numbers-in-a-file
https://stackoverflow.com/questions/742466/how-can-i-reverse-the-order-of-lines-in-a-file
https://unix.stackexchange.com/questions/148379/delete-spaces-hyphens-and-underscores-in-filenames
https://es.wikipedia.org/wiki/Pink_Floyd
https://www.lifewire.com/file-contents-in-column-format-linux-4018107
https://stackoverflow.com/questions/16678487/wget-command-to-download-a-file-and-save-as-a-different-filename
https://stackoverflow.com/questions/8988824/generating-random-number-between-1-and-10-in-bash-shell-script
http://www.desarrollolibre.net/blog/tema/106/linux/ejecutar-script-automaticamente-con-cron-en-linux#.WdklwGj9SMp
https://www.linux.com/learn/kernel-newbie-corner-everything-you-wanted-know-about-module-parameters
https://www.kernel.org/doc/htmldocs/kernel-hacking/routines-init-again.html
https://www.fsl.cs.sunysb.edu/kernel-api/re02.html

[1]: images/sum-me.PNG
[2]: images/sum-me-sol.PNG
[3]: images/replace-spaces.JPG
[4]: images/cat-readme.JPG
[5]: images/tac-readme.JPG
[6]: images/sin-eliminar.JPG
[7]: images/elimindas.JPG
[8]: images/columns.JPG
[9]: images/guten1.JPG
[10]: images/guten2.JPG
[11]: images/crontab.JPG
[12]: images/crontab2.JPG
[13]: images/crontab3.JPG
[14]: images/rickroll1.JPG
[15]: images/rickroll2.JPG
[16]: images/rickroll3.JPG
[17]: images/rickrollclean.JPG
[18]: images/rickrollmodules.JPG
