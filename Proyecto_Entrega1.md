## SEGURIDAD EN BASES DE DATOS ## 

## Entrega 1: Identify, Protect_A ##   
 
Arango Garcia Jorge Mario  
Chacon Prieto Jose Alberto  
Gamez Ramirez Juan Carlos  
Sierra Nieto Joaquin  

### Docente
César Iván Rodríguez Sánchez

**UNIVERSIDAD PILOTO DE COLOMBIA**  
**MAESTRÍA EN SEGURIDAD INFORMÁTICA Y DE LAS COMUNICACIONES**  
**POSTGRADOS**  
**BOGOTÁ**  

**MAYO 05 DE 2019**

## Tabla de Contenido ## 

- [Introducción](#introducción)  
- [Objetivos](#objetivos)
- [Objetivos Específicos](#objetivos)
- [Alcance](#alcance)


## Introducción ##

Las organizaciones en la actualidad reconocen que existen amenazas significativas ante la posibilidad de la ocurrencia de un incidente o desastre que afecte la operación, como también la necesidad de recuperarse en el menor tiempo posible, garantizando la continuidad de la organización.

La implementación del Framework NIST en la organización ayuda y proporcionan una base sólida para un programa de seguridad sólido proporciona un lenguaje común para comprender, gestionar y expresar el riesgo de ciberseguridad tanto internamente como externamente. Este Se puede usar para ayudar a identificar y priorizar acciones para reducir el riesgo de ciberseguridad, y es una herramienta para alinear los enfoques de políticas, negocios y tecnología para manejar dicho riesgo. Se puede usar para administrar el riesgo de ciberseguridad en todas las organizaciones o se puede enfocar en la entrega de servicios críticos dentro de una organización, El Core del Framewok NIST comprende cuatro elementos: Funciones, Categorías, Subcategorías y Referencias Informativas.


## Objetivos ##

El objetivo de este documento es definir claramente los límites Framework NIST que son comunes en todos los sectores de infraestructura críticas y determinar las brechas en su enfoque actual de riesgo de ciberseguridad y desarrollar una hoja de ruta hacia la mejora en las prácticas de ciberseguridad de una organización.


## Objetivos Específicos ##

•	Identificar y determinar los sistemas, activos, datos y competencias de la organización, su contexto de negocio, los recursos que soportan las funciones críticas y los riesgos de ciberseguridad que afectan este entorno.

•	Proteger e implementar las contramedidas y salvaguardas necesarias para limitar o contener el impacto de un evento potencial de ciberseguridad.


## Alcance ##

Este proyecto es el primer paso hacia el concepto global. En este caso. El proyecto se centra en implementar el Framework NIST y sus 2 categorías primarias. que son Identificar (Identify) y Proteger (Protect). 

• Identificar: Desarrollar la comprensión organizacional para administrar el riesgo de ciberseguridad para sistemas, activos, datos y capacidades.

• Desarrollar e implementar las salvaguardas apropiadas para garantizar la entrega de servicios de infraestructura críticos.La función de protección admite la capacidad de limitar o contener el impacto de un posible evento de ciberseguridad.

### SELECCIÓN DE REPOSITORIO DE DATOS 

Seleccionamos la base datos en  www.datos.gov.co,  El sistema genera un fichero .CSV, en este Conjunto Datos contiene 8.020 Filas y 24 Columnas, La Base de Datos escalable porque va a permitir la incorporación progresiva de nuevas funcionalidades. Concretamente, la Base de Datos simulará la posibilidad de agregar atributos a las tablas principales de forma dinámica y nuevas tablas para adaptar Framework NIST.

### CRITERIOS DE SELECCIÓN 

Con el objetivo de tener un contexto amplio que permita definir/implementar/revisar el marco de la implementación de la NIST, se definieron 4 criterios para la seleccion de la base de datos:

* La base de datos debe contener datos personales, estos hacen  relación a datos que se pueden asociar directamente a una persona y permite su identificación directa, entre ellos tenemos la dirección de residencia, dirección laboral, telefono personal. El tratamiento de los datos personales esta regulado bajo la legislación colombiana con la ley 1581 de 2012 y su decreto reglamentario 1377 de 2013. 
* La base de datos debe contener datos semiprivados, se caracterizan por interesar no sólo a su titular sino a cierto sector o grupo de personas, o a la sociedad en general, como el dato financiero y crediticio.
* La base de datos debe contener datos sensibles, son aquellos que pueden afectar la intimidad del titular y/o generar discriminación,  tales como aquellos que revelen la orientación política, las orientacion religiosa, la pertenencia a sindicatos, tambien los relativos a la salud, a la vida sexual, y los datos biométricos.
* La base de datos debe contener datos públicos, hace referencia a los datos relativos al estado civil de las personas, profesión y a su calidad de comerciante o de servidor público.

### DESCRIPCIÓN ORGANIZACIÓN DUEÑA DE LOS DATOS

En relación con la organización dueña de los datos se tiene:  

**Información de la Entidad**  

| PRINCIPAL   | DESCRIPCIÓN       |
| ---------- | ---------- |
| **Área o dependencia**    | Dirección de Sistemas de Buen Gobierno y las Tic   |
| **Nombre de la Entidad**   | Contraloría General de Antioquia     |
| **Departamento**	          | Antioquia                                        |
| **Municipio**              | Medellín                                         |
| **Orden**                  | Territorial                                      |
| **Sector**	                | Organismos de control y vigilancia               |
| **Fecha de actualización** | 18 de enero de 2019                              |
| **Descripción datos**      | Reporte Consolidado de Contratación del mes de Diciembre de AÑO 2018 de las entidades públicas que audita la Contraloría General de Antioquia |
| **URL ACCESO DATOS**       | <https://www.datos.gov.co/Organismos-de-Control/CONTRATACION-DICIEMBRE-2018/ccgi-m8az> |


### CONTEXTO ORGANIZACIÓN PROYECTO
Para nuestro proyecto estableceremos el siguiente contexto basado en los datos de origen:  
Organización de contratación que maneja bases de datos sobre sus principales contratistas, para lo cual se propone un modelo de base de datos con la siguiente estructura:  
* Datos contratistas  
     + Datos Personales  
     + Datos Sensibles  
* Datos Contratos  
Con esta estructura y los datos origen construiremos el modelo de base de datos objeto de análisis para el proyecto.    
La organización se encarga de administrar la planta de contratista de la ciudad Medellín, donde se lleva control de los avances de ejecución de los diferentes contratistas de la ciudad. Dentro de las herramientas operativas con las que cuenta para la realización de las actividades en la organización se tiene:  
*  Aplicación Interna gestión Administrativa (Esta aplicación permite a los empleados de la organización ejecutar la gestión administrativa, seguimiento y control sobre los datos de los diferentes contratistas pertenecientes a la compañía).  
* Aplicación Web (Esta aplicación permite a los contratistas la gestión de los datos de contrato, consultas de avances y seguimiento).  
* Administración TI (Consiste en las diferentes funciones que se ejecuta desde el área de TI para el aprovisionamiento, mantenimiento, soporte y configuración de la infraestructura que soporta los procesos de la organización así:  
+ Sistema Core Organización    
    +  Contratación  
+ Sistema de control de acceso  
+ Infraestructura  
    + Comunicaciones  
     + Servidores  
     + Bases de datos)  

### CREACION DE LA BASE DE DATOS Y CONFIGURACION DE MOTOR DE BASE DE DATOS

Para la creacion de la base de datos se utilizo infraestructura de CLOUD , se utilizaron los servicios de la nube de AZURE para aprovisionar los recursos necesarios para cargar una base de datos y poder utilizar la misma base de datos para el equipo de trabajo del grupo1, para esto realizamos la creacion de una cuenta en Microsoft AZURE, luego se seleccion el recuros a utilizar que para este caso fue SQL Database

**Recursos utilizados para la base de datos en AZURE**  
**Motor de base de datos  Microsoft SQL Server**  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/recursos_AZURE.png)    

**Propiedades de la base de datos**  
**Motor de base de datos  Microsoft SQL Server**  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/PropiedadesBD.png)    

**Cifrado en nube
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/CIFRADO%20DE%20DATOS%20EN%20NUBE%20.png). 

luego de que se creo la base de datos se realizo el cargue de los datos de que se bajaron de la pagina:  <https://www.datos.gov.co/Organismos-de-Control/CONTRATACION-DICIEMBRE-2018/ccgi-m8az>

este cargue nos genero una tabla a la que llamamos contratos  

**TABLA CONTRATOS**
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/TablaCONTRATO.png)  

Con el fin de llenar la tabla se crea la tabla empleados en donde se encuentran datos personales de los empleados de la compañia    
**TABLA EMPLEADOS**  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/creacion%20de%20tabla%20empleados.png)  

## CONTROL ID.AM-2: Software platforms and applications within the organization are inventoried  


**INVENTARIO DE SOFTWARE Y APLICACIONES  UTILIZADO

NOMBRE DEL RECURSO | DESCRIPCION |
| ---------- | ---------- |
|**Azure SQL Database** |Azure SQL Database es un servicio de base de datos relacional (DBaaS) de uso general basado en la última versión estable del Motor de base de datos de Microsoft SQL Server. SQL Database es una base de datos en la nube de alto rendimiento, confiable y segura que puede usar para compilar aplicaciones y sitios web controlados por datos en el lenguaje de programación que prefiera, sin necesidad de administrar la infraestructura.| 
|**Almacenamiento de datos** |  Tamaño de almacenamiento máximo 250 GB|    
|**NOMBRE DEL PROYECTO EN AZURE**|proyectobdseguridad| 
|**Plan de tarifa**|10 DTU el producto de Azure SQL Database se licenciaba mediante planes basados DTU (o eDTU). Básicamente esto significa que, según el plan que elijamos, obtendremos un dimensionamiento que nos asegura un rendimiento determinado. DTU es el acrónimo en inglés de Database Transaction Units (la “e” de eDTU, indica el término “elastic”)|
|**Estado del servicio en el cloud de azure**| Disponible|  
|**Ubicación del sitio de procesamiento y almacenamietos de los datos**|Este de EE. UU.| 
|**Tipo de Suscripción**|Evaluación gratuita|  
|**Id. de suscripción**|3eee5414-0dd6-439c-8434-86ce0788ba17|  
|**Administrador del servidor en el cluod**|jomaarango|  
|**Reglas de Firewalls y redes virtuales**|NOMBRE DE REGLA all  IP INICIAL 12.0.0.0  IP FINAL   254.0.0.0|  
|**Integracion con Active Directory**|No configurado|
|**Clientes utilizados para gestion de SQL Database**|NAVICAT FOR SQL VERSION 12.1.20|
|**Cifrado de datos**|Bases de datos en nube cifrada con cifrado de datos transparente (TDE) este control ayuda a proteger Azure SQL Database, la Instancia administrada de Azure SQL Database y Azure Data Warehouse frente a la amenaza de actividades malintencionadas. También realiza cifrado y descifrado de la base de datos en tiempo real, copias de seguridad asociadas y archivos de registro de transacciones en reposo sin necesidad de efectuar cambios en la aplicación. De forma predeterminada, TDE está habilitado para todas las bases de datos de Azure SQL| 

### ID.GV-3: Legal and regulatory requirements
regarding cybersecurity

Dentro del contexto de la organizacion  se cuentan con regulacion para su cumplimiento como son:

**Ley 1581 de 2012**
La ley de protección de datos personales es una ley que complementa la regulación vigente para la protección del derecho fundamental que tienen todas las personas naturales a autorizar la información personal que es almacenada en bases de datos o archivos, así como su posterior actualización y rectificación. Esta ley se aplica a las bases de datos o archivos que contengan datos personales de personas naturales.



### ID.AM-6: Cybersecurity roles and responsibilities are established  

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Roles.png) 

La tabla siguiente muestra los roles fijos de base de datos y sus atribuciones. Estos roles existen en todas las bases de datos Contratos.


| NOMBRE DE ROL  | DESCRIPCIÓN       |
| ---------- | ---------- |
| **db_owner**    | Los miembros de la función de base de datos fijan db_owner pueden realizar todas las actividades de configuración y mantenimiento en la base de datos, y también pueden eliminar la base de datos en SQL Server.    |
| **db_securityadmin**   | Los miembros de la función de base de datos fijan db_securityadmin pueden modificar la membresía de la función solo para funciones personalizadas, crear usuarios sin inicios de sesión y administrar permisos.      |
| **db_denydatawriter**	 | Los miembros de la función de base de datos fijan db_denydatawriter no pueden agregar, modificar ni eliminar ningún dato en las tablas de usuario dentro de una base de datos.
| **db_backupoperator**	| Los miembros de la función de base de datos fijan db_backupoperator pueden hacer una copia de seguridad de la base de datos.
| **db_denydatareader**	| Los miembros del rol fijo de base de datos db_denydatareader no pueden leer ningún dato en las tablas de usuario dentro de una base de datos.
| **db_ddladmin**	| Los miembros de la función de base de datos fijan db_ddladmin pueden ejecutar cualquier comando de lenguaje de definición de datos (DDL) en una base de datos
| **db_accessadmin**	| Los miembros del rol fijo de base de datos db_accessadmin pueden agregar o quitar el acceso a la base de datos para inicios de sesión de Windows, grupos de Windows e inicios de sesión de SQL Server. 
| **db_datawriter**	| Los miembros del rol fijo de base de datos db_datawriter pueden agregar, eliminar o cambiar datos en todas las tablas de usuario.
| **db_datareader**	| Los miembros del rol fijo de base de datos db_datareader pueden leer todos los datos de todas las tablas de usuario.
| **público**	| Cada inicio de sesión de SQL Server pertenece a la función de servidor público. Cuando a un servidor principal no se le han otorgado o denegado permisos específicos sobre un objeto asegurable, el usuario hereda los permisos otorgados al público sobre ese objeto.  

| NOMBRE DE ROL  | DESCRIPCIÓN       |
| ---------- | ---------- |
| **CONSULTA_CONTRATOS**    | Los miembros del rol fijo de base de datos pueden hacer diferentes consultas |






## CONTROL ID.AM-5: Resources are prioritized based on their classification, criticality, and business value

La clasificación de la información en la base de datos se realiza según la información contenida en los campos de cada tabla en función de la confidencialidad, integridad, disponibilidad, requisitos legales aplicables, criticidad, divulgación, modificación	y valor para la organización. 

* Requisitos legales aplicables; hace referencia a la aplicabilidad de leyes o normas que protegen la información (1581, 052, 042, 1273).

* Criticidad; considera la información contenida en el campo como critica cuando es personal, semiprivada o sensible(C) y cuando la información es publica es considerada como no critica(NC). 

* Divulgación; se tienen 2 escenarios posibles en el primero la divulgación no causa peligro para la organización a corto plazo (D) y en el segundo escenario la divulgación tiene un impacto serio en los objetivos estratégicos a largo plazo (ND).

* Valor para la organización se determina de acuerdo a la siguiente escala economica 
   * Bajo    (B)     0<x349.999
   * Medio (M)    350.000<x<4.499.999
   * Alto    (A)     5.500.000<x< 50.000.000

Modificación; evalúa el impacto en los objetivos estratégicos de la organización cuando se modifica la información contenida en la base de datos, se determina de acuerdo a la siguiente escala 
   * Modificable       (M)    con un  Impacto Bajo
   * No Modificable  (NM) con un Impacto Alto
