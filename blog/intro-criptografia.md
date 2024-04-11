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

## ¿Qué es la criptografía? (versión para desarrolladores apurados)

Es la disciplina que estudia las técnicas para transformar la información desde su formato original
a otro que permita protegerla del acceso por parte de usuarios no autorizados de forma que se pueda
prevenir cualquier adulteración y certificar su procedencia.

## ¿Qué objetivos buscamos con el uso de la criptografía?

Por lo general buscamos lograr 3 cosas con la criptografía:

* **Confidencialidad:** Asegurar que la información sea consultada y utilizada solo por aquellas
personas que deban poder hacerlo según la voluntad del propietario o creador de la misma.
* **Integridad:** Garantizar que la información no sea alterada sin autorización.
* **Irrenunciabilidad:** Comprobar que las partes que participan en una trasacción son efectivamente
aquellas que dicen serlo y al mismo tiempo evitar que puedan negarlo.

## Principales aplicaciones

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

## Regulaciones y normas legales que exigen el uso de la criptografía en el Perú

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

## ¿Cómo te impacta como desarrollador?

* Requiriendo que sepas implementar correctamente mecanismos de autenticación y autorización.
* Requiriendo que sepas como almacenar adecuadamente contraseñas y otros secretos en bases de datos.
* Requiriendo que sepas como inyectar secretos en tu código en tiempo de ejecución y durante el despliegue
sin que los mismos sean parte de tu código fuente y mucho menos sean incluidos en repositorios bajo
control de versiones.
* Requiriendo que puedas utilizar sumas de verificación y firmas digitales en tus procesos de IT para
garantizar la integridad y no repudio de los datos.
 
 
