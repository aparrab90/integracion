# PATRONES DE INTEGRACIÓN EMPRESARIAL


## Solución de integración de aplicaciones

La empresa XYZ ha implementado hace más de tres años una solución de ERP opensource Odoo, la cual la ha utilizado inicialmente on-premise, han tenido un crecimiento constante, paso de tener una oficina a tener 20 oficinas en todo el país, además de abrir presencia en plataformas para masificar sus productos y atraer a más clientes utilizando Facebook y WhatsApp para empresas, en donde de igual manera ha tenido una gran acogida; se empezaron a presentar problemas relacionado a la versión que tiene la empresa por lo que ha optado con migrar a la versión comercial en la nube del fabricante de Odoo, reduciendo los problemas de lentitud e intermitencia que tenían entre las diferentes oficinas, pero sin resolver los siguientes problemas:

Facturación electrónica, provista por un proveedor local que dispone de una plataforma web, el proveedor ofrece su plataforma en la modalidad plataforma como servicio.
Medios de pago, la empresa necesita recibir pagos por medio de transferencias bancarias, además con la finalidad de reducir los tiempos de respuesta en procesar pagos y despachar las ordenes de compra, la empresa XYZ logró conseguir que la institución financiera ABC le provee el botón de pagos para recibir pagos con tarjetas de débito y crédito, el botón de pagos tiene dos métodos para que la empresa XYZ pueda utilizarlo, ofrece una API y un plugin listo para usar en Odoo.
Manejo de redes sociales, la empresa necesita una solución que le permita poder publicar productos y recibir pedidos por redes sociales, ya que actualmente utilizan Facebook y WhatsApp para empresas, que le permiten presentar sus productos y contactarse con los clientes para tomar sus pedidos, ya que actualmente si la empresa ofrece un nuevo producto una persona encargada de las redes realiza la publicación manual en la página de Facebook, si un cliente se contacta por medio de WhatsApp, de igual manera si la persona que maneja el dispositivo móvil con la cuenta empresarial revisa podrá ver que alguien escribió solicitando algún producto  o información, pero los clientes escriben no solo en horario laboral por lo que se necesita dar una respuesta a estos clientes.

## Structurizr DSL
```
workspace {

    model {
        usuario = person "Usuario" "Empleado de XYZ que interactúa con el ERP para operaciones internas"
        cliente = person "Cliente" "Cliente que interactúa con la empresa a través de redes sociales y el ERP para realizar pedidos y pagos"
        sistemaFacturacion = softwareSystem "Sistema de Facturación Electrónica" "Sistema externo que proporciona facturación electrónica como servicio"
        sistemaBancario = softwareSystem "Sistema Bancario" "Banco ABC que provee el botón de pago y servicios de transferencia bancaria"
        plataformasRedesSociales = softwareSystem "Plataformas de Redes Sociales" "Redes Sociales como Facebook y WhatsApp para empresas usadas para comunicación y marketing"

        erpOdoo = softwareSystem "ERP Odoo" "Sistema ERP en la nube utilizado por la empresa XYZ" {
            aplicacionERP = container "Aplicación ERP" "La instancia principal de Odoo en la nube que los empleados y clientes utilizan para interactuar con la empresa" {
                usuario -> this "Usa"
                cliente -> this "Interactúa a través de"
                
                // Definición de componentes dentro del contenedor de la Aplicación ERP
                generadorFacturas = component "Generador de Facturas" "Genera facturas y valida la información de las mismas" {
                    // Conexiones de componentes, si las hay, van aquí
                }

                procesadorPagos = component "Procesador de Pagos" "Procesa pagos con tarjeta y transferencias bancarias" {
                    // Conexiones de componentes, si las hay, van aquí
                }

                botRedesSociales = component "Bot de Redes Sociales" "Bot que publica automáticamente en Facebook y maneja respuestas automáticas en WhatsApp" {
                    // Conexiones de componentes, si las hay, van aquí
                }
            }

            moduloFacturacion = container "Módulo de Facturación" "Gestiona la facturación y se integra con el sistema de facturación electrónica" {
                aplicacionERP -> this "Incluye"
                this -> sistemaFacturacion "Se integra con"
            }

            moduloPagos = container "Módulo de Pagos" "Gestiona los pagos y se integra con el sistema bancario" {
                aplicacionERP -> this "Incluye"
                this -> sistemaBancario "Se integra con"
            }

            interfazRedesSociales = container "Interfaz de Redes Sociales" "Maneja la publicación de productos y recepción de pedidos a través de redes sociales" {
                aplicacionERP -> this "Incluye"
                this -> plataformasRedesSociales "Interactúa con"
            }
        }
    }

    views {
        systemContext erpOdoo {
            include *
            autolayout lr
        }

        container erpOdoo {
            include *
            autolayout lr
        }

        component aplicacionERP {
            include *
            autolayout lr
        }

        theme default
    }
}


```



