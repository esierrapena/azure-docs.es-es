---
title: Supervisión de los recursos delegados a escala
description: Aprenda a usar los registros de Azure Monitor de forma eficaz y escalable en los inquilinos del cliente que está administrando.
ms.date: 02/03/2020
ms.topic: how-to
ms.openlocfilehash: bdd91cec650d6810d1d62230219f840a172141d9
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "84634122"
---
# <a name="monitor-delegated-resources-at-scale"></a>Supervisión de los recursos delegados a escala

Como proveedor de servicios, es posible que haya incorporado varios inquilinos de cliente para la administración de recursos delegados de Azure. [Azure Lighthouse](../overview.md) permite a los proveedores de servicios realizar operaciones a escala a través de varios inquilinos a la vez, lo que hace que las tareas de administración sean más eficaces.

En este tema se muestra cómo usar los [registros de Azure Monitor](../../azure-monitor/platform/data-platform-logs.md) de forma eficaz y escalable en los inquilinos del cliente que está administrando.

## <a name="create-log-analytics-workspaces"></a>Creación de áreas de trabajo de Log Analytics

Para recopilar datos, deberá crear áreas de trabajo de Log Analytics. Estas áreas de trabajo de Log Analytics son entornos únicos para los datos que recopila Azure Monitor. Cada área de trabajo tiene su propio repositorio de datos y configuración, y las soluciones y orígenes de datos están configurados para almacenar sus datos en una determinada área de trabajo.

Se recomienda crear estas áreas de trabajo directamente en los inquilinos del cliente. De esta forma, los datos permanecen en sus respectivos inquilinos en lugar de exportarse al suyo. Esto también permite la supervisión centralizada de los recursos o servicios que admite Log Analytics, lo que le proporciona más flexibilidad respecto a los tipos de datos que supervisa.

Puede crear un área de trabajo de Log Analytics mediante [Azure Portal](../../azure-monitor/learn/quick-create-workspace.md), la [CLI de Azure](../../azure-monitor/learn/quick-create-workspace-cli.md) o [Azure PowerShell](../../azure-monitor/learn/quick-create-workspace-posh.md).

## <a name="deploy-policies-that-log-data"></a>Implementación de directivas que registran datos

Después de crear sus áreas de trabajo de Log Analytics, puede implementar [Azure Policy](../../governance/policy/index.yml) en las jerarquías del cliente para que los datos de diagnóstico se envíen al área de trabajo correspondiente en cada inquilino. Las directivas exactas implementadas pueden variar en función de los tipos de recursos que quiera supervisar.

Para obtener más información acerca de la creación de directivas, vea [Tutorial: Creación y administración de directivas para aplicar el cumplimiento](../../governance/policy/tutorials/create-and-manage.md). Esta [herramienta de la comunidad](https://github.com/Azure/Azure-Lighthouse-samples/tree/master/tools/azure-diagnostics-policy-generator) proporciona un script para ayudarle a crear directivas para supervisar los tipos de recursos específicos que elija.

Cuando haya determinado las directivas que se van a implementar, puede [implementarlas en las suscripciones delegadas a escala](policy-at-scale.md).

## <a name="analyze-the-gathered-data"></a>Análisis de los datos recopilados

Una vez implementadas las directivas, los datos se registrarán en las áreas de trabajo de Log Analytics que ha creado en cada inquilino del cliente. Para obtener información sobre todos los clientes administrados, puede usar herramientas como [Libros de Azure Monitor](../../azure-monitor/platform/workbooks-overview.md) para recopilar y analizar información de varios orígenes de datos.

## <a name="next-steps"></a>Pasos siguientes

- Más información acerca de [Azure Monitor](../../azure-monitor/index.yml).
- Más información acerca de los [registros de Azure Monitor](../../azure-monitor/platform/data-platform-logs.md).
- Más información sobre las [experiencias de administración entre inquilinos](../concepts/cross-tenant-management-experience.md).
