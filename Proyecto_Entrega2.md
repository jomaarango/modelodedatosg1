## SEGURIDAD EN BASES DE DATOS ## 

## Entrega 2: Protect_B y Detect. ##   
 
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

**MAYO 12 DE 2019**

## Tabla de Contenido ## 

- [Introducción](#introducción)  
- [Objetivos](#objetivos)
- [Objetivos Específicos](#objetivos)
- [Alcance](#alcance)


## Introducción ##

Como parte de la continuidad de la implementación de los controles del framework NIST, en esta parte se da cobertura a los controles orientados a la protección y algunos de identificación faltantes. En total se abordarán 12 controles que se describirán y mostrara su implementación de acuerdo con el contexto de la organización elegido para el proyecto en la etapa 1 ya desarrollada.  
  
  
## Objetivos ##  
  
Dar continuidad a la implementación de los controles abordados en el modulo de seguridad de bases de datos, para que sean implementados dentro del contexto seleccionado para el proyecto. Se abordarán los faltantes a la identificación y protección.  
  
## Objetivos Específicos ##  
  
•	Identificar y determinar los sistemas, activos, datos y competencias de la organización, su contexto de negocio, los recursos que soportan las funciones críticas y los riesgos de ciberseguridad que afectan este entorno.  

•	Proteger e implementar las contramedidas y salvaguardas necesarias para limitar o contener el impacto de un evento potencial de ciberseguridad.  
  
  
## Alcance ##  

Esta parte del proyecto se centra en implementar el Framework NIST y los siguientes controles:  
* ID.RA1 
* ID.RA2 
* ID.RA3 
* ID.RA4 
* PR.AC1 
* PR.AC4 
* PR.DS1 
* PR.DS2 
* PR.DS3 
* PR.DS4 
* PR.IP1 

## ID.RA1 ## 
**Se realiza la identificación de la version base de datos con el fin de encontrar vulnerabilidades asociadas a este activo de informacion con el fin de mitigar riesgos asociados  

**Comando utilizado** *SELECT @@VERSION AS 'SQL Server Version'  

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Version%20de%20la%20base%20de%20datos.png)  

**Se realiza la validación de las vulnerabilidades asociadas a Microsoft SQL Azure (RTM) - 12.0.2000.8**    

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Vulnerabilidades%20BD.png)

**Escaneo con Exchange Xforce IBM**    
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/EXCHANGE-XFORCE-IBM.png)

**Escaneo con Qualys con una buena clasificacion general pero se identifica e informa que el recurso publiacado accepta peticiones de cifrados debiles de TLS 1.1 Y TLS 1.0**  

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/QUALYS.png)  

**TLS 1.1 Y TLS 1.0 habilitados**   
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/acepta%20negociacioncon%20TLS%201.1%20Y%201.0.png)


##Desarrollar e implementar las salvaguardas apropiadas para garantizar la entrega de servicios de infraestructura críticos.La función de protección admite la capacidad de limitar o contener el impacto de un posible evento de ciberseguridad.  


**ID.RA-4: POTENCIAL BUSINESS IMPACTS AND LIKELIHOODS ARE IDENTIFIED**

**LA PRESENTE GUÍA ESTABLECE A LA ORGANIZACIÓN DE CONTRATACIÓN LOS CRITERIOS DE IMPACTO (BIA) DURANTE UNA INTERRUPCIÓN DE LA DISPONIBILIDAD DE LA BASES DATOS DE CONTRATACIÓN.** 

Una interrupción de la disponibilidad de la Bases datos de contratación es aquella que afecta la publicación de los Documentos del Proceso como los contratos y documentos previos; los pliegos de condiciones del contrato; el informe de evaluación de los contratos y cualquier otro documento expedido durante el Proceso de Contratación, así como la consulta de los mismos por parte de los interesados y el público en general.


**CRITERIO DE IMPACTO RIESGO DE UNA INTERRUPCIÓN DE LA DISPONIBILIDAD DE LA BASES DATOS DE CONTRATACIÓN**  

| **ÍTEM** | **CALIFICACION** | **FINANCIERO** | **PROCESO** | **REPUTACIONAL** | **LEGAL** |
| -----|-------|-------|-------|--------|--------|
|**1**|**Insignificante**|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus operaciones normales cuya duración es mayor a 20 minutos, la organización podría perder una ganancia o dejaría de percibir Ingresos de contracción que superan más de $20.000.000|Suspende la Operación de contracción o genera reprocesos de hasta 1 hora.|al interior delproceso de la organización.|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus operaciones normales del procedimiento mayor a 20 minutos, las sanciones por el incumplimiento podrían superar los $20,000,000 y/o el periodo de tiempo dentro del cual el resultado de incumplimiento daría lugar a Penalizaciones, sanciones, multas y/o Investigación contra la organización.|
|**2**|**Menor**|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus operaciones normales cuya duración es mayor a 2 horas, la organización podría perder una ganancia o dejaría de percibir ingresos de contracción que superan más de $30.000.000.|Suspende la operación de contratación o genera reprocesos mayores a 1 horas hasta 4 horas.|A nivel de la de la organización y conocimientolimitado de las áreas internas de la organización.|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus operaciones normales del procedimiento es mayor a 2 horas, las sanciones por el incumplimiento podrían superar los $30,000,000 y/o el periodo de tiempo dentro del cual el resultado de incumplimiento daría lugar a Penalizaciones, sanciones, multas y/o Investigación contra la organización.|
|**3**|**Moderado**|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus operaciones normales cuya duración es mayor a 8 horas hasta 24 horas, la organización podría perder una ganancia o dejaría de percibir ingresos de contracción que superan más de $80.000.000.|Suspende la operación de contratación o genera reprocesos mayores a 4 horas y hasta 1 día.|El problema es
De conocimiento de un número considerado de las áreas de la organización.|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus de operaciones normales del procedimiento es mayor a 8 horas hasta 24 horas, las sanciones por el incumplimiento podrían superar los $80,000,000 y/o el periodo de tiempo dentro del cual el resultado de incumplimiento daría lugar a Penalizaciones, sanciones, multas y/o Investigación contra la organización.|
|**4**|**Importante**|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus operaciones normales cuya duración es mayor a 12 horas hasta 48 horas, la organización podría perder una ganancia o dejaría de percibir ingresos que superan más de $100.000.000|Suspende la operación o genera reprocesos mayores a un día hasta 2 días.|A nivel sectorial/Entes de control.|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus de operaciones normales del procedimiento mayor a 12 horas hasta 48 horas, las sanciones por el incumplimiento podrían superar los $100,000,000 y/o el periodo de tiempo dentro del cual el resultado de incumplimiento daría lugar a Penalizaciones, sanciones, multas y/o Investigación contra la organización.|
|**5**|**Masivo**|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus operaciones normales entre 72 horas, la organización podría perder una ganancia o dejaría de percibir ingresos de contracción que superan más de $150.000.000.|Suspende la operación o genera reprocesos mayores a 2 días.|Medios decomunicación.|Durante una interrupción de la disponibilidad de la Bases datos de contratación en sus de operaciones normales del procedimiento mayor a 72 horas, las sanciones por el incumplimiento podrían superar los $150,000,000 y/o el periodo de tiempo dentro del cual el resultado de incumplimiento daría lugar a Penalizaciones, sanciones, multas y/o Investigación contra la organización.|

**RESULTADOS DEL ANÁLISIS DE IMPACTO DE LA DISPONIBILIDAD DE LA BASES DATOS DE CONTRATACIÓN**

AREA: Tecnología De Información

FECHA: 9/05/2019 

La información contenida en este documento es exclusivamente de alta dirección y área de tecnología de la información (TI) de la organización de contratos, para llegar al nivel adecuado la disponibilidad de la base datos de contratación. 

Se obtuvieron los siguientes resultados: 

Identificación aplicaciones críticas - Calculo RTO y RPO

| **PROCESO** | **APLICACIONES CRITICAS** | **RTO (HORAS)** | **RPO (HORAS)** |
| -----|-------|-------|-------|
|Eventos|Bases de Datos de contratos|1|24|

Después de calificar cada proceso y de valorar, cuáles de estos son prioritarios, se determinó el RTO (tiempo objetivo de recuperación), para identificar este tiempo la organización de contratación estableció el máximo nivel de riesgo tolerado por la empresa en caso de alguna emergencia o fallo en los servicios, en nivel dos (2), donde un impacto máximo puede tener este nivel, la alta gerencia determinó que el nivel dos es el máximo nivel de riesgo permitido por la organización.

El cálculo del RTO se determinó de acuerdo con el riesgo máximo tolerable.

Para calcular el RPO (punto objetivo de recuperación), se clasificaron las aplicaciones a las cuales se les debe hacer mecanismos de protección de datos, tales como backups o sistemas alternos.





=======


## ID.RA2 Cyber threat intelligence is received from information sharing forums and sources ##  
En las revisiones del control se puede documentar que de acuerdo con las revisiones sobre el mismo se procede con la identificación de posibles vulnerabilidades sobre los servicios de nube para bases de datos obteniendo la vulnerabilidad:    
**CVE-2016-2183 Detail**  
**Impact**  
  
CVSS v3.0 Severity and Metrics:  
  
Base Score: 7.5 HIGH  
Vector: AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N (V3 legend)    
Impact Score: 3.6  
Exploitability Score: 3.9  
Attack Vector (AV): Network  
Attack Complexity (AC): Low  
Privileges Required (PR): None  
User Interaction (UI): None  
Scope (S): Unchanged  
Confidentiality (C): High  
Integrity (I): None  
Availability (A): None  

![Image of Yaktocat](https://raw.githubusercontent.com/jomaarango/modelodedatosg1/master/IMAGENES/Scanvulne.JPG)  
  

## ID.RA3 ##  

## ID.RA4 ##  

## PR.AC1 ##  

## PR.AC4 ##  

## PR.DS1 ##  

##* PR.DS2 ##  

## PR.DS3 ##  

## PR.DS4 ##  

## PR.IP1 ##  
