---
blogpost: true
date: Apr 11, 2024
author: gnrfan
location: Lima, Perú
category: Tutorial
tags: tutorial, criptografia, seguridad, principiantes
language: Español
---

# Introducción a la criptografía con Python

## Motivación de este artículo

Para poder implementar correctamente las medidas mínimas de seguridad en tus proyectos con Python,
en particular las aplicaciones web, iremos desarrollando una serie de artículos en donde el objetivo
no es simplemente decirte que paquetes utilizar y que te vueltas un experto en copiar y pegar sino
que, por el contrario, entiendas los conceptos más básicos que te permitan apreciar y evaluar de
forma más efectiva y ¿porque no decirlo? profesional el nivel de seguridad de tu código.

## Algunos conceptos básicos y un poco de contexto

### ¿Qué es la criptografía? (versión para desarrolladores apurados)

Es la disciplina que estudia las técnicas para transformar la información desde su formato original
a otro que permita protegerla del acceso por parte de usuarios no autorizados de forma que se pueda
prevenir cualquier adulteración y certificar su procedencia.

### ¿Qué objetivos buscamos con el uso de la criptografía?

Por lo general buscamos lograr 3 cosas con la criptografía:

* **Confidencialidad:** Asegurar que la información sea consultada y utilizada solo por aquellas
personas que deban poder hacerlo según la voluntad del propietario o creador de la misma.
* **Integridad:** Garantizar que la información no sea alterada sin autorización.
* **Irrenunciabilidad:** Comprobar que las partes que participan en una trasacción son efectivamente
aquellas que dicen serlo y al mismo tiempo evitar que puedan negarlo.

### Principales aplicaciones

* **Seguridad informática:** Proteger datos de usuarios almacenandándo de forma cifrada (encriptada) en
medios sistemas de archivos o bases de datos, proteger las comunicaciones en comunicaciones en línea,
como el tráfico de la web o los correo electrónicos, etc.
* **Comercio electrónico y finanzas en línea:** Protección de las transacciones en línea, en particular cuando
tienen que ver con dinero: compras, ventas, préstamos, cambio de divisas, etc. 
* **Firma digital:**  Verificación de la autenticidad de documentos electrónicos de manera digital, algo que
en el Perú ya tiene valor legal desde que entró en vigencia la [Ley 27269: Ley de Firmas y Certificados Digitales](https://www.gob.pe/institucion/congreso-de-la-republica/normas-legales/292289-27269)
* **Criptomonedas y cadenas de bloques:** Las monedas digitales que utilizan la criptografía para garantizar
la seguridad y transparencia de las transacciones pero la tecnología subyacente de [cadena de bloques](https://es.wikipedia.org/wiki/Cadena_de_bloques?useskin=vector)
se utiliza justamente para asegurar la integridad e irrenunciabilidad de información legal, industrial y
comercial, algo que [ya](https://andina.pe/agencia/noticia-minsur-utiliza-blockchain-para-hacer-trazable-toda-su-produccion-estano-955107.aspx) [empieza](https://gestion.pe/economia/empresas/minera-poderosa-incorpora-blockchain-para-abordar-conflictos-sociales-minera-poderosa-incorpora-blockchain-blockchain-noticia/)
[a](https://es.cointelegraph.com/news/peruvian-vanilla-farm-adopts-blockchain-to-improve-traceability-and-quality) [ocurrir](https://medium.com/@stamping.io/certificado-de-vacunaci%C3%B3n-covid-del-per%C3%BA-utilizastamping-io-para-evidencias-blockchain-9b57dee42228)
en el Perú, sobretodo en los sectores mineros, agroindustriales y salud soportando procesos de trazabilidad de documentos y transacciones.

### Regulaciones y normas legales que exigen el uso de la criptografía en el Perú

Como la mayoría de paises del mundo, el Perú ya tiene en vigencia regulaciones y leyes que exigen el uso
de la criptografía en las aplicaciones y por lo tanto afectan nuestro trabajo diario.

La principal es la [Ley 29733: Ley de Protección de Datos Personales](https://www.gob.pe/institucion/congreso-de-la-republica/normas-legales/243470-29733)
que ya entró en vigor hace más de 10 años y que en sus artículos 39 al 41 se ocupa de detalles como la implementación
de controles de acceso (inicio de sesión, gestión de privilegios) y el empleo de cifrado, firmas digitales y sumas de
verificación, en particular para el almacenamiento y transferencia de datos personales de ciudadanos peruanos entre
distintas organizaciones.

Esta misma ley hace referencia a la norma técnica peruana [NTP-ISO/IEC 17799](https://spij.minjus.gob.pe/Graficos/Peru/2007/agosto/25/RM-246-2007-PCM_25-08-07.pdf)
del 2007 que no solo menciona técnicas criptográficas como las que estamos buscando hacer más conocidas en este artículo
sino también buenas prácticas sobre otros aspectos de la seguridad informática y la continuidad del negocio como la 
gestión de las brechas de seguridad, el reporte de vulnerabilidades y el análisis de riesgos.

### ¿Cómo te impacta como desarrollador?

* Requiriendo que sepas implementar correctamente mecanismos de autenticación y autorización.
* Requiriendo que sepas como almacenar adecuadamente contraseñas y otros secretos en bases de datos.
* Requiriendo que sepas como inyectar secretos en tu código en tiempo de ejecución y durante el despliegue
sin que los mismos sean parte de tu código fuente y mucho menos sean incluidos en repositorios bajo
control de versiones.
* Requiriendo que puedas utilizar sumas de verificación y firmas digitales en tus procesos de IT para
garantizar la integridad y no repudio de los datos.

### Tipos de criptografía que nos interesan

* **Criptografía de clave simétrica:** Se utiliza una única clave para cifrar y descifrar la información.
Es eficiente para comunicaciones donde las partes confían entre sí.
* **Criptografía de clave asimétrica:** Se utilizan dos claves diferentes, una pública y otra privada.
La clave pública se utiliza para cifrar la información, y la clave privada para descifrarla.
Es ideal para comunicaciones donde no hay confianza previa entre las partes.
* **Funciones hash:** Se utilizan para generar un resumen digital de la información.
Este resumen permite verificar la integridad de la información sin necesidad de descifrarla.

### A ver explícamelo pero más facilito y con ejemplos

* Cuando colocas una clave en un archivo comprimido con un programa como WinZip estas utilizando una clave simétrica
porque todos los que sepan esa clave podrán revertir el proceso de cifrado y obtener los archivos originales.
* Cuando utilizas PGP o GPG en tus correos o creas una billetera crypto estas utilizando una clave asimétrica.
De hecho, en el caso de las criptomonedas la dirección de la billetera se deriva de la llave pública.
* Otro ejemplo de es criptografía de clave asimétrica nos debería resultar familiar de cuando descargamos paquetes
de Linux desde un repositorio autorizado y conocido, ya que primero hay que descargar y registrar una llave pública
que permite verificar que los paquetes provienen de una fuente oficial de la distribución o del proyecto opensource
y no de una tercera parte que podría incluir en ellos código malicioso.
* Finalmente, un ejemplo muy conocido del uso de funciones de hashes para realizar sumas de verificación que te
debería resultar familiar, consiste en descargar una imagen ISO que nos permite instalar un sistema operativo como
Windows o alguna distribución de Linux empleando una memoria USB. Como el archivo es grande y puede tener varios
gigabytes el riesgo de que la información este corrupta por problemas en la descarga aumenta y antes de perder tiempo
intentando hacer la instalación con una imagen producto de una descarga fallida calculamos la suma de verificación
[MD5](https://es.wikipedia.org/wiki/MD5) ó [SHA-256](https://es.wikipedia.org/w/index.php?title=Secure_Hash_Algorithm&useskin=vector)
y confirmamos la integridad del archivo descargado comprobando que tenemos la descarga correcta.

## Ahora si manos a la obra con un poco de Python


