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

**Se realizo escaneo con Exchange Xforce IBM en busqueda de vulnerabilidades **      
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/EXCHANGE-XFORCE-IBM.png)  

Sobre la infraestructura cloud de azure existe un servicio que nos permite identificar riesgo a nivel de seguridad en nuestra base de datos se encontraron 7 riesgos asociados de los cuales 3 son de riesgo altos 2 de riesgo medio y 2 de riesgo alto los cuales son respectivamente:      
	
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Vulnerabilidades%20BD.png)    

-Database owners are as expected  *con un nivel de riesgo catalogado como alto*    
-Auditing should be enabled at the server level *con un nivel de riesgo catalogado como alto*        
-Server-level firewall rules should be tracked and maintained at a strict minimum *con un nivel de reisgo catalogado como alto*      
-All memberships for user-defined roles should be intended *con un nivel de riesgo catalogado como alto*      
-Sensitive data columns should be classified *con un nivel de riesgo catalogado como alto*     
-Minimal set of principals should be granted database-scoped SELECT permission on objects or columns *con un nivel de riesgo catalogado como alto*      
-Minimal set of principals should be granted database-scoped SELECT or EXECUTE permissions on schema *con un nivel de riesgo catalogado como alto*        

De todos los encontrados se realiza planes de mejora a continuación se detalla el primer plan sobre el primer riesgo alto     

**Codigo VA1258**   
**Database owners are as expected**    

Los propietarios de Data base pueden realizar todas las actividades de configuración y mantenimiento en la base de datos y también pueden eliminar las bases de datos en SQL Server. El seguimiento de los propietarios de bases de datos es importante para evitar tener permisos excesivos para algunos directores.  Con el fin de acatar esta recomendación se crea una línea de base que define cuales son los propietarios de base de datos esperados para la base de datos. Se establece que 1 vez al mes se ejecuta esta regla que verifica si los propietarios de la base de datos están definidos en la línea de base y son los autorizados    

SELECT USER_NAME(member_principal_id) AS [Owner]    
FROM sys.database_role_members  
WHERE USER_NAME(role_principal_id) = 'db_owner'  
AND USER_NAME(member_principal_id) != 'dbo'    

Los únicos usuarios ‘db owner’ establecidos son JOAQUIN y JUAN      

Se eliminan los permisos propietarios de bases de datos innecesarios para evitar otorgar permisos excesivos para este caso el usuario Alberto     

ALTER ROLE db_owner DROP MEMBER [ALBERTO]    


**Se realizo escaneo con Qualys con una buena clasificacion general pero se identifica e informa que el recurso publiacado accepta peticiones de cifrados debiles de TLS 1.1 Y TLS 1.0 para lo cual se establecen medidas para evitar la aceptacion de estos protocolos de seguridad en trasnporte de datos debiles**      

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/QUALYS.png)  

**TLS 1.1 Y TLS 1.0 habilitados**   
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/acepta%20negociacioncon%20TLS%201.1%20Y%201.0.png)  
 

**ID.RA-4: POTENCIAL BUSINESS IMPACTS AND LIKELIHOODS ARE IDENTIFIED**

#Desarrollar e implementar las salvaguardas apropiadas para garantizar la entrega de servicios de infraestructura críticos.La función de protección admite la capacidad de limitar o contener el impacto de un posible evento de ciberseguridad. 
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
  
   
     
       
Como se evidencia en la imagen a continuación se procede a identificar vulnerabilidades sobre la base de datos y relaizar comprobación con fuentes de inteligencia de amenzas en este caso se utiliza NESSUS para alizar el descubriento y alientvault como fuente de inteligencia de amenazas:  

**RESULTADOS NESSUS**  
![Image of Yaktocat](https://raw.githubusercontent.com/jomaarango/modelodedatosg1/master/IMAGENES/Scanvulne.JPG)  
 
**RESULTADOS ALIENTVAULT**  

![Image of Yaktocat](https://raw.githubusercontent.com/jomaarango/modelodedatosg1/master/IMAGENES/AlienVault1.JPG)  

![Image of Yaktocat](https://raw.githubusercontent.com/jomaarango/modelodedatosg1/master/IMAGENES/AlienVault2.JPG)  



## ID.RA3 ##  

## ID.RA4 ##  

## PR.AC1 Identities and credentials are issued,managed, verified, revoked, and audited ##  

**Asegurimiento de autenticacion en la nube** 


**Se generan cambios a nivel de la plataforma se configuran los roles y el gestor de identidades en la nube**

**Roles habilitados sobre el gestor de identidades IAM en el cloud de Azure**

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/ROLES%20en%20gestor%20de%20identidad.png)  

**Roles habilitados sobre el gestor de identidades IAM en el cloud de Azure**  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/roles%202%20iam.png)  

**Integracion con el directorio activo AZURE AD**  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Configuracion%20de%20active%20directory.png)  

**Asignacion de roles sobre los usuarios de bases de datos**  
Permite identificar los usuarios y su funcion, dado que por la segregación de funciones se aplican roles epecificos que tienen una finalidad sobre la base de datos, en este caso un usuario operacdor que ejecuta los backup sobre las bases de datos.  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/asegurarusuarios.JPG)  


## PR.AC4 ##  

## PR.DS1 Data-at-rest is protected##  

**Cifrado de la base de datos aplicado en la infraestructura en la nube**

el servicio adquirido en AZURE SQL Database en este momento Cifra la base de datos, copias de seguridad y registros en reposo sin realizar cambios en la aplicación todo esto gracias al servicio TDE

El Cifrado de datos transparente (TDE) cifra los archivos de datos de SQL Server, Base de datos SQL de Azure y Almacenamiento de datos SQL de Azure, lo que se conoce como cifrado de datos en reposo.  

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/CIFRADO%20DE%20DATOS%20EN%20NUBE%20.png)  

TDE realiza el cifrado y descifrado de E/S en tiempo real de los datos y los archivos de registro. El cifrado utiliza una clave de cifrado de la base de datos (DEK), que está almacenada en el registro de arranque de la base de datos para que esté disponible durante la recuperación. La DEK es una clave simétrica protegida utilizando un certificado almacenado en la base de datos maestra del servidor o una clave asimétrica protegida por un módulo EKM. TDE protege los datos "en reposo", es decir, los archivos de datos y de registro. Ofrece la posibilidad de cumplir muchas leyes, normativas y directrices establecidas en diversos sectores. También permite a los desarrolladores de software cifrar los datos mediante algoritmos de cifrado AES y 3DES sin cambiar las aplicaciones existentes.

Cuando se usa TDE con SQL Database V12, SQL Database crea de forma automática el certificado de nivel de servidor almacenado en la base de datos maestra. Para mover una base de datos de TDE en SQL Database, no es necesario descifrarla para la operación de traslado.

**Jerrarquia de llaves que se utilizan en el servicio de cifrado de datos transparente TDE**    

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Cifrado-TDE.png)  

Dentro del Modelo cotrmplado por la nube actualmente se cuenta con canales de comunicación cifrados que garantizan un nivel de confidencialidad de la información superior, esto con el fin de que las comunicaciones en caso de ser comprometidas garanticen completa confidencialidad de la información que viaja hacia la nube.  

<a href="http://www.youtube.com/watch?feature=player_embedded&v=UrZNkak_DT8
" target="_blank"><img src="https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Azure.JPG" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

## PR.DS2 ##  

## PR.DS3 ##  

## PR.DS4 Adequate capacity to ensure availability is maintained##  

## PR.IP1 ##  


## PR.IP-1: A baseline configuration of information technology systems is created and maintained
Para realizar el hardening a la base de datos verificamos la versión del motor, ejecutando el comando *SELECT SERVERPROPERTY('productversion'), SERVERPROPERTY ('productlevel'), SERVERPROPERTY ('edition')*

El motor de base de datos es SQL Azure RTM version 12.0.2008. RTM (Release To Manufacturing) indica  la versión final.
Dentro de las guías de aseguramiento de CIS, se encontró un manual específico para Microsoft Azure Foundations v1.1.0 publicado el  15 de febrero de 2019. La sección 4 está dedicada a recomendaciones de seguridad para configurar en las bases de datos.  

### Definiciones de perfil
Los siguientes perfiles de configuración están definidos por las siguientes caracteristicas:  
  +	 Nivel 1    
      + sea práctico y prudente.  
      +	proporcionar un beneficio de seguridad claro.       
      +	no inhibir la utilidad de la tecnología más allá de los medios aceptables.  
 
  + Nivel 2
      + están destinados a entornos o casos de uso donde la seguridad es primordial
      + actúa como defensa en medida profunda
      + puede inhibir negativamente la utilidad o el rendimiento de la tecnología.  
      
|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.1 |'Auditing' is set to 'On' (Scored) |1|La plataforma Azure permite crear un servidor SQL como un servicio. La habilitación de la auditoría en el nivel del servidor garantiza que todas las bases de datos existentes y creadas recientemente en la instancia del servidor SQL sean auditadas.|

|VERIFICACIÓN|REMEDIACIÓN|
|-----------------------------------------|-----------------------------------------|
|![Image of Yaktocat](41a) |![Image of Yaktocat](41b)|

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.2 |'AuditActionGroups' in 'auditing' policy for a SQL server is set properly (Scored)|1|Para capturar todas las actividades críticas realizadas en servidores SQL y bases de datos dentro de servidores SQL, la auditoría debe estar configurada para capturar los 'AuditActionGroups' apropiados SUCCESSFUL DATABASE AUTHENTICATION GROUP,FAILED DATABASE AUTHENTICATION GROUP, BATCH COMPLETED GROUP.|

|VERIFICACIÓN|
|-----------------------------------------------------------------------------------|
|![Image of Yaktocat](42a) |

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.3 |'Auditing' Retention is 'greater than 90 days' (Scored)|1|Los registros de auditoría se pueden usar para detectar anomalías y dar una idea de comportamiento sospechoso o el mal uso de la información y el acceso. La retención de auditoría de SQL Server debe configurarse para que sea mayor a 90 días.|

|VERIFICACIÓN|REMEDIACIÓN|
|------------------------------------------|---------------------------------------------|
|![Image of Yaktocat](43a) |![Image of Yaktocat](43b)|

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.4|'Advanced Data Security' on a SQL server is set to 'On' (Scored)|2|SQL Server "Advanced Data Security" proporciona una nueva capa de seguridad, que permite la deteccion y respuesta a las amenazas potenciales. Los usuarios recibirán notificaciones ante actividades sospechosas, vulnerabilidades potenciales, anomalías, patrones de acceso a bases de datos y alertas de ataques de inyección SQL. La seguridad de datos avanzada es una función de pago y esta caracteristica deberia estar habilitada en servidores SQL críticos para el negocio.|

|VERIFICACIÓN|
|-----------------------------------------------------------------------------------|
|![Image of Yaktocat](44a) |

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.5 |'Threat Detection types' is set to 'All'|2|La habilitación de todos los tipos de detección de amenazas protege contra la inyección de SQL, las vulnerabilidades de la base de datos y cualquier otra actividad anómala.|

|VERIFICACIÓN|
|-----------------------------------------------------------------------------------|
|![Image of Yaktocat](45a) |

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.6 |'Send alerts to' is set (Scored)|2|Proporcionar la dirección de correo electrónico para recibir alertas garantiza que cualquier detección de anomalías se informan lo antes posible, lo que aumenta la probabilidad de mitigar cualquier riesgo potencial.|

|VERIFICACIÓN|REMEDIACIÓN|
|------------------------------------------|---------------------------------------------|
|![Image of Yaktocat](46a) |![Image of Yaktocat](46b)|

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.7 |'Email service and co-administrators' is 'Enabled' (Scored)|2|Habilitar a los coadministradores para recibir alertas de seguridad del servidor SQL ayuda a informar ante cualquier riesgo potencial|

|VERIFICACIÓN|
|-----------------------------------------------------------------------------------|
|![Image of Yaktocat](47a) |

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.8 |Ensure that Azure Active Directory Admin is configured|1|Use la autenticación de Active Directory de Azure para la autenticación con la base de datos SQL.|

|VERIFICACIÓN|
|-----------------------------------------------------------------------------------|
|![Image of Yaktocat](48a) |

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.9 |Ensure that 'Data encryption' is set to 'On' on a SQL Database (Scored)|1|El cifrado de datos transparente de la Base de datos SQL de Azure ayuda a proteger contra la amenaza de actividad maliciosa al realizar el cifrado y descifrado en tiempo real de la base de datos, las copias de seguridad asociadas y los archivos de registro de transacciones sin necesidad de cambios en la aplicación.|

|VERIFICACIÓN|
|-----------------------------------------------------------------------------------|
|![Image of Yaktocat](49a) |

|**ÍTEM** | **DESCRIPCIÓN** | **NIVEL** |**DETALLE**|
|---------|---------------------------------|-----|---------------------------------|
|4.10 |Ensure SQL server's TDE protector is encrypted with BYOK (Use your own key) (Scored) |2|Sobre la base de las necesidades empresariales o la criticidad de los datos / bases de datos alojados en un servidor SQL, se recomienda que el protector de TDE esté encriptado por una clave administrada por el propietario de los datos (BYOK).|

|VERIFICACIÓN|
|-----------------------------------------------------------------------------------|
|![Image of Yaktocat](410a) |
