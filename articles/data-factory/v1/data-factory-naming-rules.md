---
title: Reglas para asignar nombres a entidades de Azure Data Factory
description: Describe las reglas de nomenclatura para las entidades de Factoría de datos.
services: data-factory
documentationcenter: ''
author: djpmsft
ms.author: daperlov
manager: jroth
ms.reviewer: maghan
ms.assetid: bc5e801d-0b3b-48ec-9501-bb4146ea17f1
ms.service: data-factory
ms.workload: data-services
ms.topic: conceptual
ms.date: 01/10/2018
ms.openlocfilehash: 8fa1340b586434bf98d51437d4dc6b08594f0afa
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2020
ms.locfileid: "74931890"
---
# <a name="azure-data-factory---naming-rules"></a>Azure Data Factory: reglas de nomenclatura
> [!NOTE]
> Este artículo se aplica a la versión 1 de Data Factory. Si utiliza la versión actual del servicio Data Factory, consulte las [reglas de nomenclatura de Data Factory](../naming-rules.md).

La tabla siguiente proporciona las reglas de nomenclatura para los artefactos de Factoría de datos.

| Nombre | Exclusividad del nombre | Comprobaciones de validación |
|:--- |:--- |:--- |
| Data Factory |Único en Microsoft Azure. Los nombres no distinguen mayúsculas de minúsculas, es decir, `MyDF` y `mydf` hacen referencia a la misma factoría de datos. |<ul><li>Cada factoría de datos está asociada exactamente a una suscripción de Azure.</li><li>Los nombres de objeto deben comenzar por una letra o un número, y pueden contener solo letras, números y el carácter de guión (-).</li><li>Los caracteres de guión (-) debe estar inmediatamente precedidos y seguidos por una letra o un número. No se permiten guiones consecutivos en los nombres de contenedor.</li><li>El nombre puede tener entre 3 y 63 caracteres.</li></ul> |
| Servicios, tablas o canalizaciones vinculados |Único en una factoría de datos. Los nombres no distinguen mayúsculas de minúsculas. |<ul><li>Número máximo de caracteres incluido en un nombre de tabla: 260.</li><li>Los nombres de objeto deben empezar con una letra, un número o un carácter de subrayado (_).</li><li>No se permiten los caracteres siguientes: “.”, “+”, “?”, “/”, “<”, ”>”,”*”,”%”,”&”,”:”,”\\”</li></ul> |
| Grupo de recursos |Único en Microsoft Azure. Los nombres no distinguen mayúsculas de minúsculas. |<ul><li>Número máximo de caracteres: 1000.</li><li>El nombre puede contener letras, dígitos y los siguientes caracteres: “-”, “_”, “,” y “.”</li></ul> |

