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

Se realiza la validación de las vulnerabilidades asociadas a Microsoft SQL Azure (RTM) - 12.0.2000.8  


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

