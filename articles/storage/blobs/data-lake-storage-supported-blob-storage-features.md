---
title: Características de Blob Storage disponibles en Azure Data Lake Storage Gen2 | Microsoft Docs
description: Más información acerca de las características de Blob Storage que puede usar con Azure Data Lake Storage Gen2
author: normesta
ms.subservice: data-lake-storage-gen2
ms.service: storage
ms.topic: conceptual
ms.date: 05/10/2020
ms.author: normesta
ms.reviewer: stewu
ms.openlocfilehash: 5be7c9800076cfaf361a3e752162e14d10f22655
ms.sourcegitcommit: fdec8e8bdbddcce5b7a0c4ffc6842154220c8b90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2020
ms.locfileid: "83650746"
---
# <a name="blob-storage-features-available-in-azure-data-lake-storage-gen2"></a>Características de Blob Storage disponibles en Azure Data Lake Storage Gen2

Las características de Blob Storage, como el [registro de diagnóstico](../common/storage-analytics-logging.md), los [niveles de acceso](storage-blob-storage-tiers.md) y las  [directivas de administración del ciclo de vida de Blob Storage](storage-lifecycle-management-concepts.md), ya funcionan con las cuentas que tienen un espacio de nombres jerárquico. Por tanto, puede habilitar los espacios de nombres jerárquicos en las cuentas de Blob Storage sin perder el acceso a estas características.

En esta tabla se enumeran las características de Blob Storage que puede usar con Azure Data Lake Storage Gen2. Los elementos que aparecen en estas tablas van a cambiar con el tiempo a medida que se siga ampliando la compatibilidad. Para obtener más información sobre problemas específicos asociados con el estado de versión preliminar de una característica, consulte el artículo [problemas conocidos](data-lake-storage-known-issues.md).

## <a name="supported-blob-storage-features"></a>Características de Blob Storage compatibles

> [!NOTE]
> El nivel de compatibilidad solo se refiere al modo en que se admite la característica con Data Lake Storage Gen2. 
>
> Las [cuentas de BlockBlobStorage de rendimiento Premium](storage-blob-create-account-block-blob.md) para Data Lake Storage Gen2 están actualmente en versión preliminar pública. Los niveles de compatibilidad para estos tipos de cuentas aparecen en la columna **BlockBlobStorage (Premium)** .

|Característica de Blob Storage |Uso general v2 |BlockBlobStorage (Premium) |Artículos relacionados |
|---------------|-------------------|---|
|Nivel de acceso frecuente|Disponibilidad general|No compatible|[Azure Blob Storage: niveles de acceso frecuente, esporádico y de archivo](storage-blob-storage-tiers.md)|
|Nivel de acceso esporádico|Disponibilidad general|No compatible|[Azure Blob Storage: niveles de acceso frecuente, esporádico y de archivo](storage-blob-storage-tiers.md)|
|Eventos|Disponibilidad general|Vista previa|[Reacción a eventos de Blob Storage](storage-blob-event-overview.md)|
|Métricas (clásica)|Disponibilidad general|No compatible|[Métricas de Azure Storage Analytics (clásicas)](../common/storage-analytics-metrics.md?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)|
|Métricas en Azure Monitor|Disponibilidad general|Vista previa|[Métricas de Azure Storage en Azure Monitor](../common/storage-metrics-in-azure-monitor.md?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)|
|Comandos de PowerShell de Blob Storage|Disponibilidad general|Vista previa|[Inicio rápido: Carga, descarga y enumeración de blobs mediante PowerShell](storage-quickstart-blobs-powershell.md)|
|Comandos de la CLI de Azure de Blob Storage|Disponibilidad general|Vista previa|[Inicio rápido: Creación, descarga y enumeración de blobs mediante la CLI de Azure](storage-quickstart-blobs-cli.md)|
|API de Blob Storage|Disponibilidad general|Vista previa|[Inicio rápido: Biblioteca cliente de Azure Blob Storage v12 para .NET](storage-quickstart-blobs-dotnet.md)<br>[Inicio rápido: Administración de blobs con el SDK de Java v12](storage-quickstart-blobs-java.md)<br>[Inicio rápido: Administración de blobs con el SDK de Python v12](storage-quickstart-blobs-python.md)<br>[Inicio rápido: Administración de blobs con el SDK de JavaScript v12 en Node.js](storage-quickstart-blobs-nodejs.md)|
|Registros de diagnóstico|Disponibilidad general|Vista previa <div role="complementary" aria-labelledby="diagnostic-logging"><sup>1</sup></div> |[Registro de Azure Storage Analytics](../common/storage-analytics-logging.md?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)|
|Registro en Azure Monitor|Vista previa |Todavía no se admite|[Supervisión de Azure Storage](../common/monitor-storage.md)|
|Nivel de acceso de archivo|Vista previa|No compatible|[Azure Blob Storage: niveles de acceso frecuente, esporádico y de archivo](storage-blob-storage-tiers.md)|
|Directivas de administración del ciclo de vida|Vista previa|Todavía no se admite|[Administración del ciclo de vida de Azure Blob Storage](storage-lifecycle-management-concepts.md)|
|Fuente de cambios|Todavía no se admite|Todavía no se admite|[Compatibilidad con la fuente de cambios en Azure Blob Storage](storage-blob-change-feed.md)|
|Conmutación por error de cuenta|Todavía no se admite|Todavía no se admite|[Recuperación ante desastres y conmutación por error de la cuenta](../common/storage-disaster-recovery-guidance.md?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)|
|ACL del contenedor de blobs|Todavía no se admite|Todavía no se admite|[Establecer lista de control de acceso de contenedor](https://docs.microsoft.com/rest/api/storageservices/set-container-acl)|
|Dominios personalizados|Todavía no se admite|Todavía no se admite|[Asignación de un dominio personalizado a un punto de conexión de Azure Blob Storage](storage-custom-domain-name.md)|
|Almacenamiento inmutable|Todavía no se admite|Todavía no se admite|[Almacenamiento inmutable de los datos críticos para la empresa en Azure Blob Storage](storage-blob-immutable-storage.md)|
|Instantáneas|Todavía no se admite|Todavía no se admite|[Creación y administración de una instantánea de blob en .NET](storage-blob-snapshots.md)|
|Eliminación temporal|Todavía no se admite|Todavía no se admite|[Eliminación temporal de blobs de Azure Storage](storage-blob-soft-delete.md)|
|Sitios web estáticos|Todavía no se admite|Todavía no se admite|[Hospedaje de sitios web estáticos en Azure Storage](storage-blob-static-website.md)|

<div id="diagnostic-logging"><sup>1</sup> Para las cuentas de almacenamiento de blobs en bloques Premium, los registros de diagnóstico (versión clásica) no se pueden habilitar mediante Azure Portal. Puede habilitarlos mediante PowerShell.</div>

## <a name="see-also"></a>Consulte también

- [Problemas conocidos con Azure Data Lake Storage Gen2](data-lake-storage-known-issues.md)
- [Servicios de Azure que admiten Azure Data Lake Storage Gen2](data-lake-storage-supported-azure-services.md)
- [Plataformas de código abierto que admiten Azure Data Lake Storage Gen2](data-lake-storage-supported-open-source-platforms.md)
- [Acceso multiprotocolo en Azure Data Lake Storage](data-lake-storage-multi-protocol-access.md)