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
