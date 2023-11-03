# Adquisición de una memoria USB con FTK, Guymager y dd

En este documento se resume brevemente el procedimiento para realizar una adquisición de una memoria USB con distintas herramientas, en esencia lo que haremos será crear una imagen de la memoria.

Estaremos trabajando con una memoria de 1 GB para facilitar y agilizar el proceso.

## FTK

Para adquirir la memoria con FTK tendremos únicamente que hacer lo siguiente:

1. Insertamos la memoria USB de la que queremos hacer la adquisición en un equipo con Windows y FTK instalados
2. Abrimos la interfaz de usuario de FTK y seleccionamos *File/Create Disk Image*
3. Seleccionamos la opción "*Physical Drive*" 
4. Elegimos nuestra memoria USB
5. Tendremos que seleccionar un directorio de destino para la imagen seleccionando "*Add...*"
	- En este punto tendremos que seleccionar si verificar la imagen creada (el doble de tiempo)
6. Seleccionamos el formato .aff (Advanced Forensic Format)
6. Seleccionamos el formato .dd
7. Le damos a *Start* y nos solicitará una serie de datos como Número de caso, de evidencia, descripción, nombre del examinador... Además de Destino de la imagen y nombre del archivo de imagen.
8. Una vez esos datos estén rellenos, le damos a "*Finish*" y ya podremos darle a "*Start*" para comenzar la adquisición.

Tras unos minutos, tendremos creada la imagen en formato .aff .dd y un archivo .txt con información sobre la adquisición.

## Guymager

Para realizar una adquisición con Guymager, tendremos que en primer lugar conectar también nuestra memoria a la máquina con la que estamos trabajando y realizamos lo siguiente:

1. Buscamos nuestra memoria USB y haciendo click derecho seleccionamos "Acquire image".
2. Tendremos un menú similar al de FTK donde tendremos que rellenar datos de interés como el número de caso, de evidencia...etc
3. En el mismo menú, podremos seleccionar la ruta destino de la imagen junto a su nombre y el nombre del archivo de información
4. Ahora nos deja calcular el hash. Lo ideal es o bien calcular solo el SHA-256 o bien calcular el MD5 y el SHA-1

Guymager comenzará el proceso de adquisición tras esto, y resultará en el archivo con extension .000 y un archivo con información del proceso.
## dd

Para hacer una adquisición utilizando el comando `dd` de linux, haremos lo siguiente:

1. Conectamos por supuesto nuestra memoria USB a un equipo con una distribución de Linux
2. Lo localizamos en nuestro equipo, en nuestro caso es el `dev/sda1` y una vez lo tengamos, primero vamos a calcular el hash  con SHA1 de la memoria a copiar con el comando `shasum /dev/sda1`
   ![[Pasted image 20231101232211.png]]
3. Una vez lo tengamos vamos a proceder a hacer la copia usando `dd` de la siguiente manera:
	`dd if=/dev/sda1 of=/home/user/adquisiciones/usb.dd bs =512 conv=noerror,sync`
	![[Pasted image 20231101232317.png]]
4. Una vez tengamos la copia hecha, comprobamos su hash para ver si coincide (Debe hacerlo)
   ![[Pasted image 20231101232414.png]]

Efectivamente coincide, y con esto habríamos realizado nuestra adquisición
