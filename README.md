# Análisis de Casos Positivos de Viruela Símica en Colombia
El Proyecto Opcional con [Datos Abiertos](https://www.datos.gov.co/) es una actividad optativa del curso de [Fundamentos en Analítica de Datos](https://www.correlation-one.com/es-co/data-science-for-all-colombia) dictado por [Correlation One](https://www.correlation-one.com/) en alianza con [MinTIC](https://www.mintic.gov.co/portal/inicio/Sala-de-prensa/Noticias/273757:Ministerio-TIC-abre-7-000-cupos-para-formacion-TIC-de-calidad-para-todas-las-regiones-del-pais), que busca promover el trabajo en equipo en un proyecto de análisis de datos reales y disponibles públicamente.
<br/>
<br/>
Este proyecto está diseñado para complementar el aprendizaje de los estudiantes para que se conviertan en parte de su portafolio de experiencia como Analistas de Datos en el ámbito laboral y la participación se recompensa con la posibilidad de obtener la certificación del curso con la distinción de honores.
<br/>
<br/>

## 0. Información Básica del Proyecto
- Equipo de proyecto: Grupo 68.
- Tema del Proyecto: [Casos positivos de Viruela símica en Colombia](https://www.datos.gov.co/Salud-y-Protecci-n-Social/Casos-positivos-de-Viruela-s-mica-en-Colombia/tmet-yeek)

<br/>

## 1. Descripción del Proyecto

### 1.1. Impacto del análisis con el conjunto de datos
Actualmente, Colombia se encuentra enfrentado la epidemia de Viruela símica también conocida como viruela del mono. Si bien, las autoridades competentes se encuentran en las gestiones requeridas, como ciudadanos es necesario estar informados en cuanto a su evolución, identificar los puntos de mayor contagio, personas a las que más afecta, sintomatología y demás información que nos permita poder estar alerta en el cuidado de nuestra salud.  
<br/>
Así como en lo discutido en el grupo, algunos tienen la percepción de que esta epidemia no es relevante en su día a día, sin embargo, no es una opinión unánime. Por lo anterior, es necesario hacer visible, mediante el uso de datos, que a pesar de que es una enfermedad que no tiene tanta discusión como la del coronavirus, está presente entre nosotros y es necesario tener precauciones en la cotidianidad.

### 1.2. Problema Especifico 
Basado en la información recolectada hasta la fecha en Colombia:
- ¿Cuántas personas se han contagiado?
- ¿Dónde están ubicados los casos?
- ¿Es posible saber cuál es la mayor fuente de contagio?
- ¿Cuánto dura la hospitalización promedio? 

### 1.3.  Restricciones del análisis  
De acuerdo con la información encontrada en la página de datos, se tomará como fecha de corte de información la última actualización (5 de diciembre de 2022), en caso de que se agreguen nuevos datos, no se tendrán en cuenta. Adicionalmente, dado que la Viruela en Colombia es relativamente nueva, es factible que no se encuentren tantas fuentes adicionales a la hora de citar.

### 1.4.  Información complementaria  
Si bien ninguno de los integrantes del equipo tiene conocimiento en salud o epidemiología, como información complementaria es importante saber la [información básica acerca de MPOX](https://medlineplus.gov/spanish/mpox.html) (viruela del simio, mono o símica): síntomas, forma de contagio, diagnóstico, tratamiento, etc. 

<br/>

## 2. Unificación y Limpieza del Conjunto de Datos

### 2.1. Unificación y Limpieza
De acuerdo a la base de datos y la [descripción en la documentación](https://www.ins.gov.co/BibliotecaDigital/catalogo-variables-viruela-simica.pdf) dada por el [Instituto Nacional de Salud](https://www.datos.gov.co/browse?Informaci%C3%B3n-de-la-Entidad_Nombre-de-la-Entidad=Instituto+Nacional+de+Salud) como entidad proveedora de datos se tomaron la siguiente tabla que identifica las variables del dataset conformado por *3.908 Filas y 24 Columnas*:

| Nombre de la columna | Tipo                                                               | Categoría         |
| ----------------- | ------------------------------------------------------------------ | -------------------- |
| Semana epidemiológica	| Número | |
| Año epidemiológico | Número | |
| Código DIVIPOLA departamento | Número | |
| Código DIVIPOLA municipio	| Número | |
| Departamento | Texto simple | |	
| Municipio	| Texto simple | |	
| Fecha notificación | Texto simple | |	
| Fecha diagnóstico	| Texto simple | |	
| Sexo | Texto simple	| F - Femenino <br/> M - Masculino |
| Edad | Número | |
| Unidad de medida | Número | 1 - Años <br/> 2 - Meses <br/> 3 - Días |
| Fecha de inicio de síntomas	| Texto simple | |	
| Fecha de exantema	| Texto simple | |	
| Hospitalización	| Número | 1 - SI <br/> 2 - NO |
| Condición final	| Número | 1 - Vivo <br/> 2 - Muerto |
| ¿Viajó?	| Número | 1 - SI <br/> 2 - NO |
| País de viaje	| Texto simple | |	
| Fuente de infección	| Texto simple | EN ESTUDIO <br/> FUENTE DESCONOCIDA IMPORTADO <br/> RELACIONADO CON FUENTE DESCONOCIDA <br/> RELACIONADO CON LA IMPORTACIÓN |
| Fecha de terminación del seguimiento | Texto simple | |	
| Pertenencia étnica | Número | 1- Indígena <br/> 2- ROM-Gitano <br/> 3- Raizal <br/> 4- Palenquero <br/> 5- Negro, mulato, afro <br/> 6- Otros |
| Nombre grupo étnico	| Texto simple | |	
| Tipo de seguridad social | Texto simple | C- Contributivo <br/> P- Excepción <br/> N- No asegurado <br/> S- Subsidiado <br/> E- Especial |
| Estrato	| Número | 1 <br/> 2 <br/> 3 <br/> 4 <br/> 5 <br/> 6 |

### 2.2 Análisis Exploratorio de Datos 
Para iniciar el trabajo de análisis de información se realizaron las siguientes modificaciones en los tipos de datos correspondientes ded acuerdo al proceso de [Análisis Exploratorio de Datos (EDA)](https://www.ibm.com/co-es/cloud/learn/exploratory-data-analysis) para verificar las relaciones entre variables: 

| Nombre de la columna | Tipo  | Tratamiento       | Observaciones
| ----------------- | ------------------------------------------------------------------ | -------------------- | ------------------------------------------------------------------ |
| Semana epidemiológica | Número | Conservar | Información completa y formato correcto. |
| Año epidemiológico | Número | Conservar | Información completa y formato correcto. |
| [Código DIVIPOLA](https://geoportal.dane.gov.co/geovisores/territorio/consulta-divipola-division-politico-administrativa-de-colombia/) departamento | Número | Eliminar | La información se encuentra en la columna DEPARTAMENTO. |
| [Código DIVIPOLA](https://geoportal.dane.gov.co/geovisores/territorio/consulta-divipola-division-politico-administrativa-de-colombia/) municipio | Número | Eliminar | La información se encuentra en la columna MUNICIPIO. |
| Departamento | Texto simple | Corregir | Algunas de las capitales principales de Colombia aparecían etiquetadas como departamento, para lo cual se tomó dichas filas y se cambió al departamento correspondiente. |
| Municipio | Texto simple | Corregir | Revisión de escritura correcta de los nombres de municipios. |
| Fecha notificación | Fecha | Conservar | Información completa y formato correcto. |
| Fecha diagnóstico | Fecha | Conservar | Información completa y formato correcto. |
| Sexo | Texto simple | Conservar | Información completa y formato correcto. |
| Edad | Número | Conservar | Información completa y formato correcto. |
| Unidad de medida | Número | Eliminar | Todos los registros de edad usaron años como la misma unidad de medida. |
| Fecha de inicio de síntomas | Fecha | Conservar | Información completa y formato correcto. |
| Fecha de [exantema](https://www.lne.es/salud/guia/2022/05/30/exantema-vesicular-siente-sintoma-alarmante-66712543.html) | Fecha | Conservar | Información completa y formato correcto. |
| Hospitalización | Número | Categorizar | Convertir 1 y 2 a SI y NO según documentación. |
| Condición final | Número | Eliminar | Ninguno de los registros reportó hasta la fecha de corte alguna persona fallecida. |
| ¿Viajó? | Número | Categorizar | Convertir 1 y 2 a SI y NO según documentación. <br/><br/> Para los datos con categoría 3, del cual no aparece ninguna información en la documentación, para lo cual se decidió que, si la columna de país de viaje estaría vacía, reemplazar el dato con NO, en caso contrario reemplazar con SI. |
| País de viaje | Texto simple | Conservar | El campo no está unificado ya que tiene muchos países y ciudades, cuyo formato de escritura no puede ser legible o de fácil tratamiento estadístico. |
| Fuente de infección | Texto simple | Conservar | Información completa y formato correcto. |
| Fecha de terminación del seguimiento | Fecha | Conservar | Información completa y formato correcto. |
| Pertenencia étnica | Número | Categorizar | Convertir números a la categoría correspondiente según documentación. |
| Nombre grupo étnico | Texto simple | Eliminar | Todos los registros están vacíos. |
| Tipo de seguridad social | Texto simple | Conservar | Convertir números a la categoría correspondiente según documentación. |
| Estrato | Número | Conservar | En 2.820 filas (72% de los reportes) aparece el número 999, del cual no aparece ninguna información en la documentación sobre qué podría significar esta categoría. |

Tras terminar el proceso de EDA, el dataset para análisis y estudio está conformado por *3.908 Filas y 18 Columnas*.
<br/><br/>
Adicionalmente, para continuar con el análisis del dataset y en vista del tipo de algunos datos se crearon los siguientes campos:
| Nombre de la columna | Tipo  | Observaciones
| :----------------- | :------------------------------------------------------------------ | :------------------------------------------------------------------ |
| Continente_Viaje | Texto simple | Ya que no existe una unificación de datos completa del cómo se presenta el o los puntos exactos de viaje, al analizar la información notamos que los viajes internacionales se hacían hacia el mismo continente, para lo cual decidimos agregar este campo. |
| Coordenadas | Número | Punto de referencia del municipio de reporte del caso. |
| Latitud | Número | Latitud del municipio de reporte del caso. |
| Longitud | Número | Longitud del municipio de reporte del caso. |

Finalmente, la versión final del dataset para la creación de tablero para su posterior análisis está conformado por *__3.908 Filas y 22 Columnas__*.

<br/>

## 3. Tablero de control y visualización

<div align="center">
    <img src="https://raw.githubusercontent.com/justoneye/Analisis-MPOX-Colombia/main/An%C3%A1lisis_MPOX_Grupo68-Dashboard.png" alt="Análisis MPOX Colombia - Dashboard" width="100%"/>
</div>

### [Link de Tablero de Control - Looker Studio](https://datastudio.google.com/u/0/reporting/42163ea7-1976-4a79-8719-dc902bcb3e52/page/GZMAD)
[Link de Documento PDF](https://github.com/justoneye/Analisis-MPOX-Colombia/blob/main/An%C3%A1lisis_MPOX_Grupo68.pdf)
