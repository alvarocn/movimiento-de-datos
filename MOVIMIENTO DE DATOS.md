Alumno 3

1. Realiza una exportación del esquema de SCOTT usando la consola Enterprise Manager, con las siguientes condiciones:

    • Exporta tanto la estructura de las tablas como los datos de las mismas.
    • Excluye la tabla DEPT y los empleados cuyo sueldo es inferior a 1000.
    • Programa la operación para dentro de 10 minutos.
    • Genera un archivo de log en el directorio que consideres más oportuno.

Realiza ahora la operación con Oracle Data Pump.

2. Importa el fichero obtenido anteriormente usando Enterprise Manager pero en un usuario distinto de otra base de datos.

**3. Realiza una exportación de la estructura de todas las tablas de la base de datos usando el comando expdp de Oracle Data Pump en ficheros con un tamaño máximo de 200 MB. Prueba todas las posibles opciones que ofrece dicho comando y documentándolas adecuadamente.**

	La opción HELP = Y muestra los parámetros disponibles.

	C:\app\alvaro\admin\orcl\dpdump>expdp help=Y

	Export: Release 11.2.0.1.0 - Production on Vie Feb 28 22:41:06 2020

	Copyright (c) 1982, 2009, Oracle and/or its affiliates.  All rights reserved.


	La utilidad de exportaci¾n de pump de datos proporciona un mecanismo para transf
	erir objetos de datos
	entre bases de datos Oracle. La utilidad se llama con el siguiente comando:
	
	   Ejemplo: expdp scott/tiger DIRECTORY=dmpdir DUMPFILE=scott.dmp

	Puede controlar c¾mo se ejecuta la exportaci¾n introduciendo el comando 'expdp'
	seguido por varios parßmetros. Para especificar los parßmetros, utilice palabras clave:

	   Formato:  expdp KEYWORD=valor o KEYWORD=(valor1,valor2,...,valorN)
	   Ejemplo: expdp scott/tiger DUMPFILE=scott.dmp DIRECTORY=dmpdir SCHEMAS=scott o TABLES=(T1:P1,T1:P2), si T1 es una tabla particionada

		USERID debe ser el primer parßmetro de la lÝnea de comandos.

	------------------------------------------------------------------------------

	A continuaci¾n, se muestran las palabras clave disponibles con sus descripciones. Los valores por defecto se muestran entre corchetes.
	
	ATTACH
	Conectar a un trabajo existente.
	Por ejemplo, ATTACH=nombre_trabajo.

	COMPRESSION
	Reduce el tama±o de un archivo de volcado.
	Los valores de palabras clave vßlidos son: ALL, DATA_ONLY, [METADATA_ONLY] y NONE.
	CONTENT
	Especifica los datos que se van a descargar.
	Los valores de palabras clave vßlidos son: [ALL], DATA_ONLY y METADATA_ONLY.

	DATA_OPTIONS
	Indicadores de opciones de nivel de datos.
	Los valores de palabra clave vßlidos son: XML_CLOBS.
	
	DIRECTORY
	Objeto de directorio que se va a utilizar para los archivos de volcado y log.

	DUMPFILE
	Lista de nombres de archivo de volcado de destino [expdat.dmp].
	Por ejemplo, DUMPFILE=scott1.dmp, scott2.dmp, dmpdir:scott3.dmp.
	
	ENCRYPTION
	Cifra todo o parte del archivo de volcado.
	Los valores de palabras clave vßlidos son: ALL, DATA_ONLY, ENCRYPTED_COLUMNS_ONLY, METADATA_ONLY y NONE.

	ENCRYPTION_ALGORITHM
	Especifica c¾mo se debe hacer el cifrado.
	Los valores de palabras clave vßlidos son: [AES128], AES192 y AES256.

	ENCRYPTION_MODE
	MÚtodo para generar la clave de cifrado.
	Los valores de palabras clave vßlidos son: DUAL, PASSWORD y [TRANSPARENT].

	ENCRYPTION_PASSWORD
	Clave de contrase±a para crear datos cifrados en un archivo de volcado.
	
	ESTIMATE
	Calcula estimaciones de trabajo.
	Los valores de palabras clave vßlidos son: [BLOCKS] y STATISTICS.

	ESTIMATE_ONLY
	Calcula las estimaciones de trabajo sin realizar la exportaci¾n.
	
	EXCLUDE
	Excluye tipos de objeto especÝficos.
	Por ejemplo, EXCLUDE=SCHEMA:"='HR'".
	
	FILESIZE
	Especifica el tama±o de cada archivo de volcado en unidades de bytes.
	
	FLASHBACK_SCN
	SCN utilizado para restablecer la instantßnea de sesi¾n.
	
	FLASHBACK_TIME
	Tiempo utilizado para buscar el valor de SCN correspondiente mßs cercano.

	FULL
	Exporta toda la base de datos [N].

	HELP
	Muestra mensajes de ayuda [N].

	INCLUDE
	Incluye tipos de objetos especÝficos.
	Por ejemplo, INCLUDE=TABLE_DATA.

	JOB_NAME
	Nombre del trabajo de exportaci¾n que se va a crear.

	LOGFILE
	Especifica el nombre del archivo log [export.log].

	NETWORK_LINK
	Nombre del enlace de base de datos remota al sistema de origen.

	NOLOGFILE
	No se escribe el archivo log [N].

	PARALLEL
	Cambia el n·mero de workers activos para el trabajo actual.

	PARFILE
	Especifica el nombre del archivo de parßmetros.

	QUERY
	Clßusula de predicado utilizada para exportar un subjuego de una tabla.
	Por ejemplo, QUERY=employees:"WHERE identificador_departamento > 10".

	REMAP_DATA
	Especifica una funci¾n de conversi¾n de datos.
	Por ejemplo, REMAP_DATA=EMP.EMPNO:REMAPPKG.EMPNO.

	REUSE_DUMPFILES
	Sobrescribe el archivo de volcado de destino si existe (N).

	SAMPLE
	Porcentaje de datos para exportar.

	SCHEMAS
	Lista de esquemas que se van a exportar (esquema de conexi¾n).

	SOURCE_EDITION
	Edici¾n que se usarß para extraer metadatos.

	STATUS
	Estado del trabajo de frecuencia (seg) que se va a controlar donde
	el valor por defecto (0) mostrarß el nuevo estado cuando estÚ disponible.

	TABLES
	Identifica una lista de tablespaces que se van a exportar.
	Por ejemplo, TABLES=HR.EMPLOYEES,SH.SALES:SALES_1995.

	TABLESPACES
	Identifica una lista de tablespaces que se van a exportar.
	
	TRANSPORTABLE
	Especifica si el mÚtodo transportable se puede utilizar.
	Los valores de palabras clave vßlidos son: ALWAYS y [NEVER].
	
	TRANSPORT_FULL_CHECK
	Verifica segmentos de almacenamiento de todas las tablas [N].

	TRANSPORT_TABLESPACES
	Lista de tablespaces desde los que se descargarßn los metadatos.
	
	VERSION
	Versi¾n de los objetos que se van a exportar.
	Los valores de palabra cable vßlidos son: [COMPATIBLE], LATEST o cualquier versi¾n de base de datos vßlida.

	*** EJEMPLOS DE EXPORTACIÓN ***


	C:\app\alvaro\admin\orcl\dpdump>expdp system/Raul dumpfile=exportacionpractica7
	Filesize=200m include=table content=metadata_only

	Export: Release 11.2.0.1.0 - Production on Sßb Feb 29 00:41:19 2020

	Copyright (c) 1982, 2009, Oracle and/or its affiliates.  All rights reserved.


	Conectado a: Oracle Database 11g Enterprise Edition Release 11.2.0.1.0 - 64bit Production
	With the Partitioning, OLAP, Data Mining and Real Application Testing options
	Iniciando "SYSTEM"."SYS_EXPORT_SCHEMA_01":  system/******** dumpfile=exportacion
	practica7 Filesize=200m include=table content=metadata_only
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/TABLE
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/PRE_TABLE_ACTION
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/GRANT/OWNER_GRANT/OBJECT_GRANT
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/INDEX/INDEX
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/CONSTRAINT/CONSTRAINT
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/INDEX/STATISTICS/INDEX_STATISTICS
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/COMMENT
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/CONSTRAINT/REF_CONSTRAINT
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/TRIGGER
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/STATISTICS/TABLE_STATISTICS
	Procesando el tipo de objeto SCHEMA_EXPORT/TABLE/POST_TABLE_ACTION
	La tabla maestra "SYSTEM"."SYS_EXPORT_SCHEMA_01" se ha cargado/descargado correctamente
	******************************************************************************
	El juego de archivos de volcado para SYSTEM.SYS_EXPORT_SCHEMA_01 es:
	  C:\APP\ALVARO\ADMIN\ORCL\DPDUMP\EXPORTACIONPRACTICA7.DMP
	El trabajo "SYSTEM"."SYS_EXPORT_SCHEMA_01" ha terminado correctamente en 00:41:32


	C:\app\alvaro\admin\orcl\dpdump>
![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2000-43-54.png)


	- A continuación hemos optado por la opcion de compresion.

	- Podemos hacer un backup completo (FULL) y comprimido
	-   USERID => Usuario con el que se realiza el export
	-  FULL=Y => Se exportan TODOS los DATOS y METADATOs
	-   COMPRESSION=ALL => Se comprimen DATOS y METADATOS

	La tabla maestra "SYS"."SYS_EXPORT_FULL_01" se ha cargado/descargado correctamente
	******************************************************************************
	El juego de archivos de volcado para SYS.SYS_EXPORT_FULL_01 es:
	  C:\APP\ALVARO\ADMIN\ORCL\DPDUMP\EXP_P7.DMP
	El trabajo "SYS"."SYS_EXPORT_FULL_01" ha terminado correctamente en 00:10:17


	C:\app\alvaro\admin\orcl\dpdump>expdp USERID=\"/ as sysdba\" FULL=Y DIRECTORY=DATA_PUMP_DIR COMPRESSION=ALL DUMPFILE=exp_p7.dmp

	

![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2000-17-33.png)

![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2000-18-55.png)




4. Intenta realizar operaciones similares de importación y exportación con una herramienta gráfica de administración de Postgres, documentando el proceso.

	Usaremos phpPgAdmin, es un gestor web de bases de datos PostgreSQL. Desde el podremos administrar nuestras base de datos, 	esquemas, tablas, vistas... etc. Antes debemos de realizar unas configuraciones anteriormente realizadas en otras tareas para 	poder acceder.
	
	
	Se nos abrira una nueva ventana y veremos nuestro panel phpPgAdmin.
	Exportar

	Para exportar nuestra base de datos, podremos hacer click en el icono "Exportar".
	
![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2002-07-56.png)

	Se nos abrirá una ventana para determinar el formato  y las opciones que queremos exportar de nuestra base de datos.

![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2002-08-05.png)

	LO recomendable sería seleccionar para exportar: "Estructura y Datos", Formato: "SQL". En las opciones, selecciona "Bajar comprimido con gzip" y hacemos click a exportar .

![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2002-11-05.png)

![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2002-11-36.png)

	IMPORTAR
	Para poder importar una base de datos necesitaremos hacer click en el icono "SQL".
	
	Se abrirá un área de texto donde podemos pegar las consultas SQL que queramos ejecutar. Adicionalmente podemos utilizar un 	fichero para importar las consultas a la base de datos. Hacemos click sobre el botón de "seleccionar fichero" que esta bajo el área de texto, seleccionar el fichero desde nuestro ordenador y finalmente pulsar sobre el botón "Ejecutar"
	
![](https://github.com/alvarocn/movimiento-de-datos/blob/master/imagenes/Captura%20de%20pantalla%20de%202020-02-29%2002-12-07.png)



	

	
	

	

















5. Exporta todos los documentos de una colección de MongoDB que tengan más de cuatro campos e impórtalos en otra base de datos .




