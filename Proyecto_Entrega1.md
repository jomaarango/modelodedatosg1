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







