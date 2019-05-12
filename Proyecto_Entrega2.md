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
 
 **RESULTADO HTML**  
 
 <dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd><html xmlns="http://www.w3.org/1999/xhtml"><head><meta http-equiv="Content-Type" content="text/html; charset=utf-8"></meta><title>Tenable.io Report</title><style type="text/css" media="all">
    UL.ulist {padding: 0 10px; line-height:25px; margin-bottom:0px; margin-top:0px;};
    LI.list  {padding: 0 10px; line-height:25px; margin-bottom:0px; margin-top:0px; list-style: disc;}
    LI.list0 {padding: 0 10px; line-height:25px; margin-bottom:0px; margin-top:0px; list-style: disc; color:#357abd;}
    LI.list1 {padding: 0 10px; line-height:25px; margin-bottom:0px; margin-top:0px; list-style: disc; color:#4cae4c;}
    LI.list2 {padding: 0 10px; line-height:25px; margin-bottom:0px; margin-top:0px; list-style: disc; color:#fdc431;}
    LI.list3 {padding: 0 10px; line-height:25px; margin-bottom:0px; margin-top:0px; list-style: disc; color:#ee9336;}
    LI.list4 {padding: 0 10px; line-height:25px; margin-bottom:0px; margin-top:0px; list-style: disc; color:#d43f3a;}

    html, body, div, span, applet, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, abbr, acronym, address, big, cite, code, del, dfn, em, img, ins, kbd, q, s, samp, small, strike, strong, sub, sup, tt, var, b, u, i, center, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, canvas, details, embed, figure, figcaption, footer, header, hgroup, menu, nav, output, ruby, section, summary, time, mark, audio, video {
        margin: 0;
        padding: 0;
        border: 0;
        font-size: 100%;
        font: inherit;
        vertical-align: baseline;
        -webkit-text-size-adjust: none;
    }
    
    html, body {
        font-family: helvetica, arial, sans-serif;
        width: 100%;
        color: #263645;
        font-size: 12px;
        background: #efefef;
    }

    a, a:visited, a:active {
        color: #004a97;
    }

    a:hover {
        color: #00253d;
    }

    .container_16 {
        margin: 0 auto;
        padding: 0 14px 14px 14px;
        background: #fff;
        border-top: #425363 solid 7px;
        box-shadow: 0 2px 10px rgba(0, 0, 0, .2);
        margin-bottom: 20px;
        border-radius: 0 0 5px 5px;
    }

    #reportContent {
        width: 100%;
    }

    h1.classtitle {
        padding: 15px 0 10px 0;
        border-bottom: 1px dotted #ccc;
        margin: 0 0 15px 0;
    }

    h2.classtitle {
        color: #00a5b5;
        font-weight: normal;
        font-size: 22px;
        margin: 0;
        padding: 0;
    }
    
    h2.date {
        font-size: 14px;
        color: #768591;
        margin: 0;
        padding: 0;
        font-weight: normal;
    }
    
    .reportinfo {
        display: block;
        width: 100%;
        font-size: 16px;
        padding: 0 0 15px 0;
        margin: 0 0 5px 0;
        font-weight: normal;
        border-bottom: 1px dotted #ccc;
    }
    
    .reportpadding {
        padding: 15px 0 0 0 !important;
    }
    
    .classtoc {
        display: block;
        font-size: 18px;
        color: #777779;
        padding: 15px 0;
        margin: 15px 0 0 0;
    }

    h1.classchapter {
        background: #425363;
        color: #fff;
        font-weight: bold;
        font-size: 16px;
        padding: 6px 10px;
        margin: 10px 0 0 0;
        border-radius: 4px 4px 0 0;
    }

    h2.classsection {
        display: block;
        background: #425363;
        color: #fff;
        font-weight: bold;
        font-size: 14px;
        padding: 6px 10px;
        margin: 30px 0 0 0;
        border-radius: 4px 4px 0 0;
    }

    h2.classh1  {
        display: block;
        background: #efefef;
        font-weight: bold;
        font-size: 13px;
        padding: 6px 10px;
    }

    .classtext {
        font-size: 13px;
        line-height: 18px;
    }
    
    div#reportContent div span.classtext {
        padding: 6px 10px;
        display: inline-block;
    }

    h2.classsubsection {
        background: #768591;
        color: #fff;
        font-weight: bold;
        font-size: 13px;
        padding: 6px 10px;
    }
    
    .classheader h1 {
        color: #fff;
        font-weight: bold;
        font-size: 15px;
        padding: 0 10px;
        text-align: center;
    }
    
    .reportinfo b {
        font-weight: bold;
    }
    
    h3.classtitle  {
        color: #69737b;
        font-size: 16px;
        padding: 0 10px;
    }
    
    .classsection_sub tr, td {
        color: #053958;
        font-size: 13px;
        padding: 0 10px;
    }
    
    td {
        padding: 6px 10px;
    }
    
    h2.classsection, h2.classsection0, h2.classsection1, h2.classsection2, h2.classsection3, h2.classsection4 {
        background: #053958;
        color: #fff;
        font-weight: bold;
        font-size: 13px;
        padding: 6px 10px;
        margin-bottom: 0px;
        margin-top: 10px;
    }
    
    .classcell0, .classcell1, .classcell2, .classcell3, .classcell4 {
        vertical-align: bottom;
    }
    
    .classcell4, h2.classsection4 {
        background-color: #d43f3a;
    }

    .classcell3, h2.classsection3 {
        background-color: #ee9336;
    }

    .classcell2, h2.classsection2 {
        background-color: #fdc431;
    }

    .classcell1, h2.classsection1 {
        background-color: #4cae4c;
    }

    .classcell0, h2.classsection0 {
        background-color: #357abd;
    }

    
    #copyright {
        display: block;
        width: 100%;
        text-align: center;
        font-size: 12px;
        color: #A9A8A9;
        padding: 6px 0 20px 0;
    }
    
    #copyright a, #copyright a:visited, #copyright a:active {
        color: #A9A8A9;
    }
    
    div.icon {
        display: none;
    }
    
    .nopadding {
        padding: 0 !important;
    }
    
    body.email h2.classh1 {
        display: block;
        margin: 20px 0 0 0;
        background: #425363;
        color: #fff;
        font-weight: bold;
        font-size: 14px;
        padding: 6px 10px;
        border-radius: 4px 4px 0 0;
    }
    
    body.email div#reportContent div span.classtext {
        padding: 0;
        display: inline;
    }
    
    body.email h2.tips {
        background: #004a97 !important;
    }
    
    body.email h2.errors {
        background: #c00 !important;
    }
    
    body.email h2.classsection {
        display: none;
    }
    
    .classtoc1 a {
        font-size: 16px;
    }
                
    .classtoc2 a {
        font-size: 13px;
        padding: 0 20px;
    }
    
    h2.classh2  {
        background: #f8f8f8;
        font-weight: bold;
        font-size: 13px;
        padding: 6px 10px;
    }

    h2 span.sub {
        margin-left:2px;
        margin-right:2px;
    }

    h2 span.text {
        font-size:10px;
    }

    h2 span.label {
        font-size:12px;
        margin-left:8px;
    }   
    
    .classpre {
        display: block;
        font-size: 13px;
        font-family: Courier New, Courier, monospace;
        padding: 10px;
        color: #000;
    }
    
    .classh1_grey h2 {
        background: #eaeaea;
        color:#053958;
        font-size: 13px;
        padding: 0 10px;
        margin-top:0px;
        margin-bottom:2px;
    }

    .summaryTable {
        border: none;
        border-collapse: collapse;
    }

    .summaryTable tr:first-child {
        background-color: #efefef !important;
    }

    .multiRowSummaryTable td {
        border-right: 1px solid #efefef;
    }

    .multiRowSummaryTable td:last-child {
        border-right: none;
    }

    .multiRowSummaryTable tr:nth-child(odd) {
        background-color: #f8f8f8;
    }

    @media only screen and (max-device-width: 480px) {
        html, body {
            display: block;
            min-width: 480px;
            background: #fff;
        }
        
        table {
            table-layout: auto !important;
        }
        
        table td {
            word-wrap: break-word;
        }
        
        table.container_16 {
            width: 100%;
            padding: 0 4% 20px 4%;
            background: #fff;
            border-top: #425363 solid 7px;
            box-shadow: none !important;
            margin-bottom: 20px;
            border-radius: 0;
        }
        
        #copyright {
            display: block;
            width: 90%;
            text-align: center;
            font-size: 10px;
            color: #A9A8A9;
            padding: 5px 0 20px 0;
            border-top: 1px dotted #ccc;
            margin: 0 auto;
            line-height: 16px;
        }
        
        .classtitle img {
            display: block;
            margin: 0 auto;
        }
    }
</style><script type="text/javascript">
        function toggle(divId) {
            var divObj = document.getElementById(divId);
            if (divObj) {
                var displayType = divObj.style.display;
                if (displayType == "" || displayType == "block") {
                    divObj.style.display = "none";
                } else {
                    divObj.style.display = "block";
                }
            }
        }

        function ceall(flag) {
            var divs = document.getElementsByTagName("div");
            var i = 0;
            for (i = 0; i < divs.length; i++) {
                if (divs[i].getAttribute("id") != null && divs[i].getAttribute("id").match('btag-')) {
                    if (flag == 0) {
                        divs[i].style.display = "none";
                    } else {
                        divs[i].style.display = "block";
                    }
                }
            }
        }
        </script></head><body class=""><table cellpadding="0" cellspacing="0" border="0" width="100%"><tr><td align="center" valign="top" class="nopadding" style="vertical-align: top"><table cellpadding="0" cellspacing="0" border="0" width="80%" bgcolor="#FFFFFF" class="container_16"><tr><td><table xmlns="" cellpadding="0" cellspacing="0" border="0" width="100%">
<tr><td class="nopadding"><h1 class="classtitle"><img src="data:image/gif;base64,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" width="247" height="68" border="0" alt="Tenable.io Report" style="display: block;"></h1></td></tr>
<tr><td class="nopadding"><h2 class="classtitle">Tenable.io Report</h2></td></tr>
<tr><td class="nopadding"><h2 class="date">Fri, 10 May 2019 03:49:25 UTC</h2></td></tr>
<tr><td class="reportpadding"><div class="reportinfo"></div></td></tr>
</table>
<div id="reportContent"><span xmlns="" class="classtoc">Table Of Contents</span><table xmlns="">
<tr><td><span class="classtoc1"><a href="#idp17625728384">Assets Summary (Executive)</a></span></td></tr>
<tr><td><table><tr>
<td width="5%"><table style="table-layout: fixed;" width="10px" height="10px"><tr><td class="nopadding "></td></tr></table></td>
<td width="95%"><a href="#idp17625727744">bdserverg1.database.windows.net</a></td>
</tr></table></td></tr>
</table>
<h1 xmlns="" class="classchapter" id="idp17625728384">Assets Summary (Executive)</h1>
<h2 xmlns="" class="classsection" id="idp17625727744">bdserverg1.database.windows.net</h2>
<h2 xmlns="" class="classh1 " style="vertical-align: middle;"><!--[if mso]><img src="cid:#" width="1" height="25" border="0" style="display: block; float: left;">  
            <![endif]]]-->Summary</h2>
<table xmlns="" class="" width="100%">
<tr>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Critical</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">High</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Medium</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Low</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Info</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Total</span></td>
</tr>
<tr>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #d43f3a; font-weight: bold !important;">0</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #ee9336; font-weight: bold !important;">0</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #fdc431; font-weight: bold !important;">1</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #4cae4c; font-weight: bold !important;">0</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #357abd; font-weight: bold !important;">28</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">29</span></td>
</tr>
</table>
<h2 xmlns="" class="classh1 " style="vertical-align: middle;"><!--[if mso]><img src="cid:#" width="1" height="25" border="0" style="display: block; float: left;">  
            <![endif]]]-->Details</h2>
<table xmlns="" class="" width="100%">
<tr>
<td width="20%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Severity</span></td>
<td width="15%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Plugin Id</span></td>
<td width="65%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: bold !important;">Name</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell2"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Medium</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=42873" target="_blank"> 42873</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Medium Strength Cipher Suites Supported (SWEET32)</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=10863" target="_blank"> 10863</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Certificate Information</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=24260" target="_blank"> 24260</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">HyperText Transfer Protocol (HTTP) Information</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=46180" target="_blank"> 46180</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Additional DNS Hostnames</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=57041" target="_blank"> 57041</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Perfect Forward Secrecy Cipher Suites Supported</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=10144" target="_blank"> 10144</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Microsoft SQL Server TCP/IP Listener Detection</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=11219" target="_blank"> 11219</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Nessus SYN scanner</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=19506" target="_blank"> 19506</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Nessus Scan Information</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=70544" target="_blank"> 70544</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Cipher Block Chaining Cipher Suites Supported</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=121010" target="_blank"> 121010</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">TLS Version 1.1 Protocol Detection</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=25220" target="_blank"> 25220</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">TCP/IP Timestamps Supported</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=10107" target="_blank"> 10107</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">HTTP Server Type and Version</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=21643" target="_blank"> 21643</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Cipher Suites Supported</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=91822" target="_blank"> 91822</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Database Authentication Failure(s) for Provided Credentials</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=94761" target="_blank"> 94761</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Root Certification Authority Certificate Information</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=54615" target="_blank"> 54615</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Device Type</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=69482" target="_blank"> 69482</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Microsoft SQL Server STARTTLS Support</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=104410" target="_blank"> 104410</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Authentication Failure(s) for Provided Credentials</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=11936" target="_blank"> 11936</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">OS Identification</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=22964" target="_blank"> 22964</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Service Detection</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=11153" target="_blank"> 11153</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Service Detection (HELP Request)</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=104743" target="_blank"> 104743</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">TLS Version 1.0 Protocol Detection</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=84821" target="_blank"> 84821</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">TLS ALPN Supported Protocol Enumeration</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=10719" target="_blank"> 10719</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">MySQL Server Detection</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=56984" target="_blank"> 56984</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL / TLS Versions Supported</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=84502" target="_blank"> 84502</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">HSTS Missing From HTTPS Server</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=45590" target="_blank"> 45590</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">Common Platform Enumeration (CPE)</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=35297" target="_blank"> 35297</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Service Requests Client Certificate</span></td>
</tr>
<tr>
<td width="20%" valign="top" align="left" class="classcell0"><span class="classtext" style="color: #ffffff; font-weight: bold !important;">Info</span></td>
<td width="10%" valign="top" align="left" class="classcell"> <a href="http://www.tenable.com/plugins/index.php?view=single&amp;id=95631" target="_blank"> 95631</a>
</td>
<td width="70%" valign="top" align="left" class="classcell"><span class="classtext" style="color: #263645; font-weight: normal;">SSL Certificate Signed Using Weak Hashing Algorithm (Known CA)</span></td>
</tr>
</table></div></td></tr></table></td></tr></table><div id="copyright">
                This is a report from 
                 <a xmlns="" href="https://cloud.tenable.com/" target="_blank">Tenable.io</a>.<br xmlns="">
                Tenable.io is published by Tenable, Inc<br xmlns="">
                7021 Columbia Gateway Drive Suite 500, Columbia, MD 21046<br xmlns="">
                © 2019 Tenable, Inc. All rights reserved.
            </div></body></html> <em>tags</em>.</dd>
</dl>


**RESULTADOS ALIENTVAULT**  

![Image of Yaktocat](https://raw.githubusercontent.com/jomaarango/modelodedatosg1/master/IMAGENES/AlienVault1.JPG)  

![Image of Yaktocat](https://raw.githubusercontent.com/jomaarango/modelodedatosg1/master/IMAGENES/AlienVault2.JPG)  



## ID.RA3 ##  

## ID.RA4 ##  

## PR.AC1 ##  

## asegurimiento de autenticacion en la nube** 


**Se generan cambios a nivel de la plataforma se configuran los roles y el gestor de identidades en la nube 

**Roles habilitados sobre el gestor de identidades IAM en el cloud de Azure**

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/ROLES%20en%20gestor%20de%20identidad.png)  

**Roles habilitados sobre el gestor de identidades IAM en el cloud de Azure**  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/roles%202%20iam.png)  

**Integracion con el directorio activo AZURE AD**  
![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Configuracion%20de%20active%20directory.png)  

## PR.AC4 ##  

## PR.DS1 ##  

**Cifrado de la base de datos aplicado en la infraestructura en la nube**

el servicio adquirido en AZURE SQL Database en este momento Cifra la base de datos, copias de seguridad y registros en reposo sin realizar cambios en la aplicación todo esto gracias al servicio TDE

El Cifrado de datos transparente (TDE) cifra los archivos de datos de SQL Server, Base de datos SQL de Azure y Almacenamiento de datos SQL de Azure, lo que se conoce como cifrado de datos en reposo.  

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/CIFRADO%20DE%20DATOS%20EN%20NUBE%20.png)  

TDE realiza el cifrado y descifrado de E/S en tiempo real de los datos y los archivos de registro. El cifrado utiliza una clave de cifrado de la base de datos (DEK), que está almacenada en el registro de arranque de la base de datos para que esté disponible durante la recuperación. La DEK es una clave simétrica protegida utilizando un certificado almacenado en la base de datos maestra del servidor o una clave asimétrica protegida por un módulo EKM. TDE protege los datos "en reposo", es decir, los archivos de datos y de registro. Ofrece la posibilidad de cumplir muchas leyes, normativas y directrices establecidas en diversos sectores. También permite a los desarrolladores de software cifrar los datos mediante algoritmos de cifrado AES y 3DES sin cambiar las aplicaciones existentes.

Cuando se usa TDE con SQL Database V12, SQL Database crea de forma automática el certificado de nivel de servidor almacenado en la base de datos maestra. Para mover una base de datos de TDE en SQL Database, no es necesario descifrarla para la operación de traslado.

**Jerrarquia de llaves que se utilizan en el servicio de cifrado de datos transparente TDE**    

![Image of Yaktocat](https://github.com/jomaarango/modelodedatosg1/blob/master/IMAGENES/Cifrado-TDE.png)  

##* PR.DS2 ##  

## PR.DS3 ##  

## PR.DS4 ##  

## PR.IP1 ##  
