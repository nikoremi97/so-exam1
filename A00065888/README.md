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
## PUNTO 5

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
