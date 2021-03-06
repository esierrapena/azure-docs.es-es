---
title: Azure Marketplace
description: Describe de qué forma pueden usar Azure Marketplace los clientes de Contrato Enterprise
author: bandersmsft
ms.reviewer: baolcsva
ms.service: cost-management-billing
ms.topic: conceptual
ms.date: 06/01/2020
ms.author: banders
ms.openlocfilehash: 4721d8dbe5973baf2ac82124ff516a89398227cb
ms.sourcegitcommit: d118ad4fb2b66c759b70d4d8a18e6368760da3ad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84298200"
---
# <a name="azure-marketplace"></a>Azure Marketplace

En este artículo de qué forma los clientes y asociados de Contrato Enterprise pueden ver los cargos de Marketplace y habilitar las compras en Azure Marketplace.

## <a name="azure-marketplace-for-ea-customers"></a>Azure Marketplace para clientes de EA

Para los clientes directos, los cargos de Azure Marketplace se pueden ver en Azure Enterprise Portal. Las compras y los consumos de Azure Marketplace se facturan fuera del compromiso monetario, en plazos mensuales o trimestrales a pago vencido.

Los clientes indirectos pueden encontrar sus suscripciones a Azure Marketplace en la página **Administrar suscripciones** de Azure Enterprise Portal, pero no se muestran los precios. Los clientes deben ponerse en contacto con su Proveedor de soluciones de licencia (LSP) para obtener información sobre los cargos en Azure Marketplace.

Las nuevas compras periódicas mensuales o anuales de Azure Marketplace se facturan por completo durante el período en que se compran los elementos de Azure Marketplace. Estos artículos se renovarán automáticamente en el siguiente período el mismo día de la compra original.

Los cargos periódicos mensuales existentes se seguirán renovando el primero de cada mes calendario. Los cargos anuales se renovarán en el aniversario de la fecha de compra.

Algunos servicios de terceros revendedores disponibles en Azure Marketplace ahora consumen el saldo del compromiso monetario del Contrato Enterprise (EA). Antes, estos servicios se facturaban por separado, fuera del compromiso monetario de EA. El compromiso monetario de EA para estos servicios de Azure Marketplace simplifica las compras y la administración de los pagos para los clientes. Para ver una lista completa de los servicios que actualmente consumen compromiso monetario, consulte la [actualización del 6 de marzo de 2018 en el sitio web de Azure](https://azure.microsoft.com/updates/azure-marketplace-third-party-reseller-services-now-use-azure-monetary-commitment/).

### <a name="partners"></a>Asociados

Los LSP pueden descargar una lista de precios de Azure Marketplace en la página de la hoja de precios en Azure Enterprise Portal. Seleccione el vínculo **Lista de precios de Marketplace** en la esquina superior derecha. La lista de precios de Azure Marketplace muestra todos los servicios disponibles y sus precios.

Para descargar la hoja de precios:

1. En Azure Enterprise Portal, vaya a **Informes** > **Hoja de precios**.
1. En la esquina superior derecha, busque el vínculo a la lista de precios de Azure Marketplace debajo de su nombre de usuario.
1. Haga clic con el botón derecho en el vínculo y seleccione **Guardar destino como**.
1. En la ventana **Guardar**, cambie el título del documento a `AzureMarketplacePricelist.zip`, que cambiará el archivo de .xlsx a .zip.
1. Después de completada la descarga, tendrá un archivo ZIP con listas de precios específicas del país o región.
1. Los LSP deben hacer referencia al archivo individual del país para obtener los precios específicos del país o región. Los LSP pueden usar la pestaña **Notificaciones** para estar al tanto de las SKU que son nuevas o retiradas.
1. Los cambios de precio son poco frecuentes. Los LSP reciben notificaciones por correo electrónico de los aumentos de precios y las variaciones en los tipos de cambio (FX) con 30 días de antelación.
1. Los LSP reciben una factura por inscripción, por ISV y por trimestre.

### <a name="enabling-azure-marketplace-purchases"></a>Habilitación de compras en Azure Marketplace

Los administradores de empresa pueden deshabilitar o habilitar las compras de Azure Marketplace para todas las suscripciones de Azure en su inscripción. Si el administrador de empresa deshabilita las compras, y hay suscripciones de Azure que ya tienen suscripciones a Azure Marketplace, esas suscripciones a Azure Marketplace no se cancelarán ni se verán afectadas.

Aunque los clientes pueden convertir sus suscripciones de Azure directas en Azure EA si las asocian a su inscripción en Azure Enterprise Portal, esta acción no convierte automáticamente las suscripciones secundarias.

Para habilitar compras en Azure Marketplace:

1. Inicie sesión en Azure Enterprise Portal como administrador de empresa.
1. Vaya a **Administrar**.
1. En **Enrollment Detail** (Detalles de la inscripción), seleccione el icono de lápiz situado junto al elemento de línea **Azure Marketplace**.
1. Cambie entre **Habilitado/Deshabilitado** o **Solo SKU BYOL o libres**, según corresponda.
1. Seleccione **Guardar**.

> [!NOTE]
> Las opciones BYOL (traiga su propia licencia) y solo gratis limitan la compra y adquisición de SKU de Azure Marketplace a solo SKU BYOL y gratuitas.

### <a name="services-billed-hourly-for-azure-ea"></a>Servicios facturados por horas para Azure EA

Los siguientes servicios se facturan por horas en un Contrato Enterprise, en lugar de la tarifa mensual de MOSP:

- Red de entrega de aplicaciones
- Firewall de aplicaciones web

### <a name="azure-remoteapp"></a>Azure RemoteApp

Si tiene un Contrato Enterprise, paga por Azure RemoteApp según el nivel de precios del Contrato Enterprise. No existen cargos adicionales. El precio estándar incluye 40 horas iniciales. El precio ilimitado cubre 80 horas iniciales. RemoteApp deja de emitir el uso por encima de las 80 horas.

## <a name="azure-marketplace-faq"></a>P+F sobre Azure Marketplace

En esta sección se explica cómo se puede aplicar su compromiso monetario de Azure a algunos servicios de terceros revendedores en Azure Marketplace.

### <a name="what-changed-with-azure-marketplace-services-and-ea-monetary-commitment"></a>¿Qué ha cambiado con los servicios de Azure Marketplace y el compromiso monetario de EA?

A partir del 1 de marzo de 2018, algunos servicios de terceros revendedores consumen el compromiso monetario (MC) de EA. A excepción de las instancias reservadas (RI) de VM de Azure, los servicios se facturaban antes fuera del compromiso monetario de EA y se facturaban por separado.

Ampliamos el uso del compromiso monetario para incluir ahora algunos de los servicios de Azure Marketplace publicados por terceros que se compran con más frecuencia. El compromiso monetario de EA para estos servicios de Azure Marketplace simplifica las compras y la administración de los pagos.

### <a name="why-did-we-make-this-change"></a>¿Por qué hemos realizado este cambio?

Los clientes buscan continuamente otras formas de aprovechar el pago por adelantado de MC. Los clientes solicitaron este cambio a menudo, y afectó a una gran parte de los clientes de Azure Marketplace.

### <a name="how-do-you-benefit"></a>¿En qué se beneficia?

Obtiene una experiencia de facturación más sencilla y podrá gastar mejor su compromiso monetario de EA. Dado que estos servicios se incluyen en el compromiso monetario de prepago, el compromiso monetario de EA es más valioso.

### <a name="what-azure-marketplace-services-use-ea-monetary-commitment-and-how-do-i-know"></a>¿Qué servicios de Azure Marketplace usan el compromiso monetario de EA y cómo lo averiguo?

Cuando compra un servicio que usa compromiso monetario, Azure Marketplace presenta una declinación de responsabilidades. Se admiten algunos servicios publicados por Red Hat, SUSE, Autodesk y Oracle. Actualmente, los servicios con el mismo nombre publicados por otros terceros no se deducen del compromiso monetario. Al final de esta sección de preguntas frecuentes encontrará una lista completa.

### <a name="what-if-my-ea-monetary-commitment-runs-out"></a>¿Qué ocurre si se agota mi compromiso monetario de EA?

Si consume todo su compromiso monetario y pasa a uso por encima del límite, los cargos relacionados con estos servicios aparecerán en la próxima factura de uso por encima del límite, junto con cualquier otro servicio de consumo. Antes del cambio del 1 de marzo de 2018, estos cargos se facturaban con otros servicios de Azure Marketplace.

### <a name="why-dont-all-azure-marketplaces-consume-ea-monetary-commitment"></a>¿Por qué no todas las instancias de Azure Marketplace consumen compromiso monetario de EA?

Hacemos lo posible por ofrecer la mejor experiencia de cliente relacionada con el compromiso monetario de EA. Este cambio afectó un gran número de clientes y a una parte importante del gasto total en Azure Marketplace. Es posible que se agreguen otros servicios en el futuro.

### <a name="how-does-this-impact-indirect-enrollment-and-partners"></a>¿Cómo afecta esto a la inscripción indirecta y los asociados?

Nuestros asociados o clientes de inscripciones indirectas no se verán afectados. Estos servicios están sujetos a las mismas funcionalidades de marcado de asociados que otros servicios de consumo. El único cambio es que los cargos aparecen en una factura diferente, y el pago de los cargos queda fuera del compromiso monetario de EA del cliente.

### <a name="is-there-a-list-of-azure-marketplace-services-that-consume-ea-monetary-commitment"></a>¿Hay una lista de servicios de Azure Marketplace que consumen compromiso monetario de EA?

Algunas ofertas específicas de Azure Marketplace pueden usar fondos del compromiso monetario. Consulte los [servicios de terceros que usan compromiso monetario](https://azure.microsoft.com/updates/azure-marketplace-third-party-reseller-services-now-use-azure-monetary-commitment) para obtener una lista completa de productos que participan en este programa.


## <a name="next-steps"></a>Pasos siguientes

- Obtenga más información acerca de los [precios](ea-pricing-overview.md).