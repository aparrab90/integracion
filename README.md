# Menú de Contenido
- [Solución de Integración de Aplicaciones](#solución-de-integración-de-aplicaciones)
  - [Tipos de Integración que se Puede Realizar entre los Sistemas y Plataformas](#tipos-de-integración-que-se-puede-realizar-entre-los-sistemas-y-plataformas)
  - [Documente sus Decisiones Utilizando el Formato ADR](#documente-sus-decisiones-utilizando-el-formato-adr)
    - [Plantilla de Registro de Decisiones de Michael Nygard](#plantilla-de-registro-de-decisiones-de-michael-nygard)
  - [Diagrama Utilizando el Modelo C4](#diagrama-utilizando-el-modelo-c4)
    - [System Context ERP Odoo](#system-context-erp-odoo)
    - [Container ERP Odoo](#container-erp-odoo)
- [Anexo](#anexo)

## Solución de Integración de Aplicaciones
La empresa XYZ ha implementado hace más de tres años una solución de ERP opensource Odoo, la cual la ha utilizado inicialmente on-premise, han tenido un crecimiento constante, paso de tener una oficina a tener 20 oficinas en todo el país, además de abrir presencia en plataformas para masificar sus productos y atraer a más clientes utilizando Facebook y WhatsApp para empresas, en donde de igual manera ha tenido una gran acogida; se empezaron a presentar problemas relacionado a la versión que tiene la empresa por lo que ha optado con migrar a la versión comercial en la nube del fabricante de Odoo, reduciendo los problemas de lentitud e intermitencia que tenían entre las diferentes oficinas, pero sin resolver los siguientes problemas:
- Facturación electrónica, provista por un proveedor local que dispone de una plataforma web, el proveedor ofrece su plataforma en la modalidad plataforma como servicio.
- Medios de pago, la empresa necesita recibir pagos por medio de transferencias bancarias, además con la finalidad de reducir los tiempos de respuesta en procesar pagos y despachar las ordenes de compra, la empresa XYZ logró conseguir que la institución financiera ABC le provee el botón de pagos para recibir pagos con tarjetas de débito y crédito, el botón de pagos tiene dos métodos para que la empresa XYZ pueda utilizarlo, ofrece una API y un plugin listo para usar en Odoo.
- Manejo de redes sociales, la empresa necesita una solución que le permita poder publicar productos y recibir pedidos por redes sociales, ya que actualmente utilizan Facebook y WhatsApp para empresas, que le permiten presentar sus productos y contactarse con los clientes para tomar sus pedidos, ya que actualmente si la empresa ofrece un nuevo producto una persona encargada de las redes realiza la publicación manual en la página de Facebook, si un cliente se contacta por medio de WhatsApp, de igual manera si la persona que maneja el dispositivo móvil con la cuenta empresarial revisa podrá ver que alguien escribió solicitando algún producto  o información, pero los clientes escriben no solo en horario laboral por lo que se necesita dar una respuesta a estos clientes.

### Tipos de Integración que se Puede Realizar entre los Sistemas y Plataformas

- Integración del sistema opensource Odoo con la plataforma de facturación electrónica:
  - Tipo de integración: API a API
- Integración del sistema opensource Odoo con el botón de pagos:
  - Tipo de integración: API a API
  - Tipo de integración: Plugin
- Integración del sistema opensource Odoo con las redes sociales:
  - Tipo de integración: Webhook


### Documente sus Decisiones Utilizando el Formato ADR
Información sobre cómo documentar decisiones de arquitectura.

#### Plantilla de Registro de Decisiones de Michael Nygard
Ejemplo o enlace a la plantilla de registro de decisiones.

### Diagrama Utilizando el Modelo C4
Explicación sobre cómo utilizar el modelo C4 para diagramación.

#### [System Context] ERP Odoo
Diagrama del contexto del sistema para ERP Odoo.

#### [Container] ERP Odoo
Diagrama de contenedor para ERP Odoo.

## Anexo
Información adicional o complementaria.
