# Adquisición forense en vivo de una máquina Windows 10

## Introducción

En este documento se resume brevemente el proceso de adquisición en vivo, es decir, con la máquina encendida, de la memoria volátil y no volátil de la máquina usando **Access Data FTK Imager** , asi como la aplicación de un proceso de triaje mediante la herramienta **IR Triage**.

Durante el proceso se aplicará en la medida de lo posible, ya que en este caso tenemos un escenario muy acotado, la metodología que hemos desarrollado en grupo para realizar las adquisiciones. 

## Preparación y reconocimento

En la primera fase de nuestra metodología tratamos de tener en cuenta el escenario con el que nos encontramos y evaluar nuestro proceder en base a ello. Estamos frente a una máquina Windows encendida y en primer lugar, si queremos realizar una extracción de calidad, bajo ningún concepto podemos apagarla. 

Debemos intentar actuar con la máxima precaución alterando lo más mínimo los procesos y memoria volátil de la máquina. Tan solo haremos lo necesario, que será instalar nuestras herramientas, **FTK** y **IR Triage**, desde un dispositivo externo previamente preparado. Tan solo usaremos estas dos herramientas porque FTK nos permite además de hacer una imagen de disco, realizar una adquisición de la memoria volátil, y nos ahorra el tener que instalar una herramienta específicamente para éste propósito.

Con nuestras herramientas preparadas, procedemos con la adquisición.

## Planteamiento de la Adquisición

En primer lugar debemos de tener en cuenta qué vamos a hacer primero, en base a los criterios que recogimos en nuestra metodología de *valor probable, volatilidad y cantidad de esfuerzo requerido*. 

Con esto en mente, lo mejor es proceder a en primer lugar realizar una adquisición de la memoria volátil (RAM) mediante FTK debido a ser la memoria más volátil, a tener una sencilla extracción y tener un valor probable considerable, para luego continuar la creación de una imagen del disco de la máquina también con **FTK**, que es menos volátil que la ram, y también nos aportará datos probablemente valiosos con un esfuerzo pequeño. 

Una vez hayamos extraídos los datos, podremos aplicar el proceso de triage con la herramienta **IR Triage**, ya que considero que la herramienta podría alterar la integridad de los datos al empezar a ejecutar las operaciones necesarias.

## Adquisición

Con esta planificación procedemos a realizar la adquisición en la máquina, en primer lugar instalamos nuestras herramientas en la máquina desde una memoria USB previamente cargada con nuestras herramientas FTK e IR Triage.

Abrimos tan solo FTK para alterar lo mínimo los datos y mantener el nivel de integridad tan alto como sea posible.