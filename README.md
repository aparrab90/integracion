# PATRONES DE INTEGRACIÓN EMPRESARIAL



## Getting started

To make it easy for you to get started with GitLab, here's a list of recommended next steps.

Already a pro? Just edit this README.md and make it your own. Want to make it easy? [Use the template at the bottom](#editing-this-readme)!

## Add your files

- [ ] [Create](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#create-a-file) or [upload](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#upload-a-file) files
- [ ] [Add files using the command line](https://docs.gitlab.com/ee/gitlab-basics/add-file.html#add-a-file-using-the-command-line) or push an existing Git repository with the following command:

```
cd existing_repo
git remote add origin https://gitlab.com/aparrab90/patrones-de-integracion-empresarial.git
git branch -M main
git push -uf origin main
```

## Integrate with your tools

- [ ] [Set up project integrations](https://gitlab.com/aparrab90/patrones-de-integracion-empresarial/-/settings/integrations)

## Collaborate with your team

- [ ] [Invite team members and collaborators](https://docs.gitlab.com/ee/user/project/members/)
- [ ] [Create a new merge request](https://docs.gitlab.com/ee/user/project/merge_requests/creating_merge_requests.html)
- [ ] [Automatically close issues from merge requests](https://docs.gitlab.com/ee/user/project/issues/managing_issues.html#closing-issues-automatically)
- [ ] [Enable merge request approvals](https://docs.gitlab.com/ee/user/project/merge_requests/approvals/)
- [ ] [Set auto-merge](https://docs.gitlab.com/ee/user/project/merge_requests/merge_when_pipeline_succeeds.html)

## Test and Deploy

Use the built-in continuous integration in GitLab.

- [ ] [Get started with GitLab CI/CD](https://docs.gitlab.com/ee/ci/quick_start/index.html)
- [ ] [Analyze your code for known vulnerabilities with Static Application Security Testing (SAST)](https://docs.gitlab.com/ee/user/application_security/sast/)
- [ ] [Deploy to Kubernetes, Amazon EC2, or Amazon ECS using Auto Deploy](https://docs.gitlab.com/ee/topics/autodevops/requirements.html)
- [ ] [Use pull-based deployments for improved Kubernetes management](https://docs.gitlab.com/ee/user/clusters/agent/)
- [ ] [Set up protected environments](https://docs.gitlab.com/ee/ci/environments/protected_environments.html)

***

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



