---
title: Compatibilidad para la evaluación de VMware en Azure Migrate
description: Obtenga información sobre la compatibilidad de la evaluación de máquinas virtuales de VMware con la herramienta Server Assessment de Azure Migrate.
ms.topic: conceptual
ms.date: 05/04/2020
ms.openlocfilehash: 8e0b6f3babcc862e1a78effcdb1a61f430c01646
ms.sourcegitcommit: 309cf6876d906425a0d6f72deceb9ecd231d387c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2020
ms.locfileid: "84267892"
---
# <a name="support-matrix-for-vmware-assessment"></a>Matriz de compatibilidad para la evaluación de VMware 

En este artículo se resumen los requisitos previos y los requisitos de soporte técnico a la hora de evaluar máquinas virtuales de VMware para la migración a Azure con la herramienta [Azure Migrate:Server Assessment](migrate-services-overview.md#azure-migrate-server-assessment-tool). Si quiere migrar máquinas virtuales de VMware a Azure, revise la [matriz de compatibilidad para la migración](migrate-support-matrix-vmware-migration.md).

Para evaluar las máquinas virtuales de VMware, cree un proyecto de Azure Migrate y, a continuación, agregue la herramienta Server Assessment al proyecto. Después de agregarla, implemente el [dispositivo de Azure Migrate](migrate-appliance.md). El dispositivo detecta las máquinas locales de forma continuada y envía metadatos de las máquinas y datos rendimiento a Azure. Una vez completada la detección, recopile las máquinas detectadas en grupos y ejecute una evaluación de un grupo.

## <a name="limitations"></a>Limitaciones

**Soporte técnico** | **Detalles**
--- | ---
**Límites del proyecto** | Puede crear varios proyectos en una suscripción a Azure.<br/><br/> Puede detectar y evaluar hasta 35 000 máquinas virtuales de VMware en un único [proyecto](migrate-support-matrix.md#azure-migrate-projects). Un proyecto también puede incluir servidores físicos y máquinas virtuales de Hyper-V, hasta sus respectivos límites de evaluación.
**Detección** | Un dispositivo de Azure Migrate puede detectar hasta 10 000 VM de VMware en una instancia de vCenter Server.
**Valoración** | Puede agregar hasta 35 000 máquinas en un solo grupo.<br/><br/> Puede acceder hasta a 35 000 máquinas virtuales en una única evaluación.

[Más información](concepts-assessment-calculation.md) sobre las evaluaciones.


## <a name="application-discovery"></a>Detección de aplicaciones

Además de detectar máquinas, Server Assessment puede detectar aplicaciones, roles y características en ejecución en las máquinas. La detección del inventario de aplicaciones le permite identificar y planificar una ruta de migración adaptada a sus cargas de trabajo locales. 

**Soporte técnico** | **Detalles**
--- | ---
**Máquinas compatibles** | Actualmente solo se admite la detección de aplicaciones para máquinas virtuales de VMware.
**Detección** | La detección de aplicaciones es sin agente. Usa las credenciales de invitado de las máquinas y obtiene acceso a ellas de forma remota mediante llamadas WMI y SSH.
**Soporte técnico de máquina virtual** | La detección de aplicaciones se admite en todas las versiones de Windows y Linux.
**Credenciales de vCenter** | La detección de aplicaciones necesita una cuenta de vCenter Server con acceso de solo lectura, así como privilegios habilitados para Máquinas virtuales > Operaciones de invitado.
**Credenciales de máquina virtual** | Actualmente, la detección de aplicaciones admite el uso de una credencial para todos los servidores Windows y otra para todos los servidores Linux.<br/><br/> Se crea una cuenta de usuario invitado para máquinas virtuales Windows y una cuenta de usuario normal (acceso sin sudo) para todas las máquinas virtuales Linux.
**Herramientas de VMware** | Las herramientas de VMware se deben instalar y ejecutar en las máquinas virtuales que se quieren detectar. <br/> La versión de las herramientas de VMware debe ser posterior a 10.2.0.
**PowerShell** | Las máquinas virtuales deben tener instalada la versión 2.0 de PowerShell o una versión posterior.
**Acceso a puertos** | En los hosts ESXi que ejecuten las máquinas virtuales que desea detectar, Azure Migrate debería ser capaz de conectarse al puerto TCP 443.
**Límites** | Para la detección de aplicaciones, puede detectar hasta 10 000 máquinas virtuales en cada dispositivo de Azure Migrate.



## <a name="vmware-requirements"></a>Requisitos de VMware

**VMware** | **Detalles**
--- | ---
**Máquinas virtuales de VMware** | Todos los sistemas operativos se pueden evaluar para la migración. 
**vCenter Server** | Las máquinas que quiera detectar y evaluar las debe administrar vCenter Server, versión 5.5, 6.0, 6.5 o 6.7.
**Permisos (evaluación)** | Cuenta de solo lectura de vCenter Server.
**Permisos (detección de aplicaciones)** | Cuenta de vCenter Server con acceso de solo lectura, así como privilegios habilitados para **Máquinas virtuales > Operaciones de invitado**.
**Permisos (visualización de dependencias)** | vCenter Server cuenta con acceso de solo lectura, así como privilegios habilitados para **Operaciones de Invitado** > **en Máquinas virtuales**.


## <a name="azure-migrate-appliance-requirements"></a>Requisitos del dispositivo de Azure Migrate

Azure Migrate usa el [dispositivo de Azure Migrate](migrate-appliance.md) para la detección y la evaluación. Puede implementar el dispositivo como una máquina virtual de VMWare mediante una plantilla OVA, importada en vCenter Server, o bien mediante un [script de PowerShell](deploy-appliance-script.md).

- Obtenga más información sobre los [requisitos del dispositivo](migrate-appliance.md#appliance---vmware) para VMware.
- Obtenga información sobre las direcciones URL a las que el dispositivo necesita acceder en nubes [públicas](migrate-appliance.md#public-cloud-urls) y [gubernamentales](migrate-appliance.md#government-cloud-urls).
- En Azure Government, debe implementar el dispositivo [mediante el script](deploy-appliance-script-government.md).


## <a name="port-access"></a>Acceso a puertos

**Dispositivo** | **Connection**
--- | ---
Dispositivo | Conexiones entrantes en el puerto TCP 3389 para permitir las conexiones del Escritorio remoto al dispositivo.<br/><br/> Conexiones entrantes en el puerto 44368 para tener acceso de forma remota a la aplicación de administración del dispositivo mediante la dirección URL: ```https://<appliance-ip-or-name>:44368``` <br/><br/>Conexiones salientes en el puerto 443 (HTTPS) para enviar metadatos de detección y rendimiento a Azure Migrate.
Servidor vCenter | Conexiones entrantes en el puerto TCP 443 para permitir que el dispositivo recopile los metadatos de configuración y rendimiento de las evaluaciones. <br/><br/> De forma predeterminada, el dispositivo se conecta a vCenter en el puerto 443. Si el servidor vCenter escucha en un puerto diferente, puede modificar el puerto al configurar la detección.
Hosts ESXi (detección de aplicaciones/análisis de dependencia sin agentes) | Si quiere [detectar aplicaciones](how-to-discover-applications.md) o [hacer un análisis de dependencia sin agentes](concepts-dependency-visualization.md#agentless-analysis), el dispositivo se conecta a los hosts ESXi en el puerto TCP 443 para la detección de aplicaciones y para ejecutar la visualización de dependencias sin agentes en las máquinas virtuales.

## <a name="application-discovery"></a>Detección de aplicaciones

Además de detectar máquinas, Server Assessment puede detectar aplicaciones, roles y características en ejecución en las máquinas. La detección del inventario de aplicaciones le permite identificar y planificar una ruta de migración adaptada a sus cargas de trabajo locales. 

**Soporte técnico** | **Detalles**
--- | ---
**Máquinas compatibles** | Actualmente solo se admite la detección de aplicaciones para máquinas virtuales de VMware.
**Detección** | La detección de aplicaciones es sin agente. Usa las credenciales de invitado de las máquinas y obtiene acceso a ellas de forma remota mediante llamadas WMI y SSH.
**Soporte técnico de máquina virtual** | La detección de aplicaciones se admite en todas las versiones de Windows y Linux.
**Credenciales de vCenter** | La detección de aplicaciones necesita una cuenta de vCenter Server con acceso de solo lectura, así como privilegios habilitados para Máquinas virtuales > Operaciones de invitado.
**Credenciales de máquina virtual** | Actualmente, la detección de aplicaciones admite el uso de una credencial para todos los servidores Windows y otra para todos los servidores Linux.<br/><br/> Se crea una cuenta de usuario invitado para máquinas virtuales Windows y una cuenta de usuario normal (acceso sin sudo) para todas las máquinas virtuales Linux.
**Herramientas de VMware** | Las herramientas de VMware se deben instalar y ejecutar en las máquinas virtuales que se quieren detectar. <br/> La versión de las herramientas de VMware debe ser posterior a 10.2.0.
**PowerShell** | Las máquinas virtuales deben tener instalada la versión 2.0 de PowerShell o una versión posterior.
**Acceso a puertos** | En los hosts ESXi que ejecuten las máquinas virtuales que desea detectar, Azure Migrate debería ser capaz de conectarse al puerto TCP 443.
**Límites** | Para la detección de aplicaciones, puede detectar hasta 10 000 máquinas virtuales en cada dispositivo de Azure Migrate.


## <a name="agentless-dependency-analysis-requirements"></a>Requisitos para el análisis de dependencia sin agentes

El [análisis de dependencia](concepts-dependency-visualization.md) le ayuda a identificar la dependencia entre las máquinas locales que quiere evaluar y migrar a Azure. En esta tabla se resumen los requisitos para configurar el análisis de dependencia sin agentes. 

**Requisito** | **Detalles**
--- | --- 
**Antes de la implementación** | Debe tener un proyecto de Azure Migrate activo con la herramienta Server Assessment agregada.<br/><br/>  La visualización de dependencias se implementa después de configurar un dispositivo de Azure Migrate para detectar las máquinas de VMWare locales.<br/><br/> [Aprenda](create-manage-projects.md) a crear un proyecto por primera vez.<br/> [Aprenda](how-to-assess.md) a agregar una herramienta de evaluación a un proyecto existente.<br/> [Aprenda](how-to-set-up-appliance-vmware.md) a configurar un dispositivo de Azure Migrate para la evaluación de máquinas virtuales de VMware.
**Soporte técnico de máquina virtual** | Actualmente solo se admite en máquinas virtuales VMware.
**Máquinas virtuales Windows** | Windows Server 2016<br/> Windows Server 2012 R2<br/> Windows Server 2012<br/> Windows Server 2008 R2 (64 bits).
**Cuenta de Windows** |  Para el análisis de dependencias, el dispositivo de Azure Migrate necesita una cuenta de administrador local o de dominio para acceder a las máquinas virtuales Windows.
**Máquinas virtuales Linux** | Red Hat Enterprise Linux 7, 6, 5<br/> Ubuntu Linux 14.04, 16.04<br/> Debian 7, 8<br/> Oracle Linux 6, 7<br/> CentOS 5, 6, 7
**Cuenta de Linux** | Para el análisis de dependencias, el dispositivo de Azure Migrate necesita una cuenta de usuario con privilegio de usuario raíz en las máquinas Linux.<br/><br/> Como alternativa, la cuenta de usuario necesita estos permisos en los archivos/bin/netstat y /bin/ls: CAP_DAC_READ_SEARCH y CAP_SYS_PTRACE.
**Agentes necesarios** | No se requiere ningún agente en las máquinas que desea analizar.
**Herramientas de VMware** | Se debe instalar y ejecutar una versión de las herramientas de VMware posterior a 10.2 en cada máquina virtual que se quiera analizar.
**Credenciales de vCenter Server** | La visualización de dependencias necesita una cuenta de vCenter Server con acceso de solo lectura, así como privilegios habilitados para Máquinas virtuales > Operaciones de invitado. 
**PowerShell** | Las máquinas virtuales deben tener instalada la versión 2.0 de PowerShell o una versión superior.
**Acceso a puertos** | En los hosts ESXi que ejecuten las máquinas virtuales que desea analizar, Azure Migrate debería ser capaz de conectarse al puerto TCP 443.


## <a name="agent-based-dependency-analysis-requirements"></a>Requisitos para el análisis de dependencia con agentes

El [análisis de dependencias](concepts-dependency-visualization.md) le ayuda a identificar las dependencias entre las máquinas locales que quiere evaluar y migrar a Azure. En esta tabla se resumen los requisitos para configurar el análisis de dependencia con agentes. 

**Requisito** | **Detalles** 
--- | --- 
**Antes de la implementación** | Debe tener un proyecto de Azure Migrate activo, con la herramienta Azure Migrate: Server Assessment agregada al proyecto.<br/><br/>  La visualización de dependencias se implementa después de configurar un dispositivo de Azure Migrate para detectar las máquinas locales.<br/><br/> [Aprenda](create-manage-projects.md) a crear un proyecto por primera vez.<br/> [Aprenda](how-to-assess.md) a agregar una herramienta de evaluación a un proyecto existente.<br/> Aprenda a configurar un dispositivo de Azure Migrate para la evaluación de [Hyper-V](how-to-set-up-appliance-hyper-v.md), [VMware](how-to-set-up-appliance-vmware.md) o de servidores físicos.
**Azure Government** | La visualización de dependencias no está disponible en Azure Government.
**Log Analytics** | Azure Migrate utiliza la solución [Service Map](../operations-management-suite/operations-management-suite-service-map.md) de los [registros de Azure Monitor](../log-analytics/log-analytics-overview.md) para la visualización de dependencias.<br/><br/> Puede asociar un área de trabajo de Log Analytics nueva o existente con un proyecto de Azure Migrate. El área de trabajo de un proyecto de Azure Migrate no se puede modificar una vez que se ha agregado. <br/><br/> El área de trabajo debe estar en la misma suscripción que el proyecto de Azure Migrate.<br/><br/> El área de trabajo debe residir en las regiones Este de EE. UU., Sudeste Asiático u Oeste de Europa. Las áreas de trabajo de otras regiones no se pueden asociar a un proyecto.<br/><br/> El área de trabajo debe estar en una región en la que [se admita Service Map](../azure-monitor/insights/vminsights-enable-overview.md#prerequisites).<br/><br/> En Log Analytics, el área de trabajo asociada con Azure Migrate se etiqueta con la clave del proyecto de migración y el nombre del proyecto.
**Agentes necesarios** | En cada máquina que desee analizar, instale los siguientes agentes:<br/><br/> [Microsoft Monitoring agent (MMA)](https://docs.microsoft.com/azure/log-analytics/log-analytics-agent-windows).<br/> [Dependency Agent](../azure-monitor/platform/agents-overview.md#dependency-agent).<br/><br/> Si las máquinas locales no están conectadas a Internet, tiene que descargar e instalar la puerta de enlace de Log Analytics en ellas.<br/><br/> Conozca más información sobre la instalación de [Dependency Agent](how-to-create-group-machine-dependencies.md#install-the-dependency-agent) y [MMA](how-to-create-group-machine-dependencies.md#install-the-mma).
**Área de trabajo de Log Analytics** | El área de trabajo debe estar en la misma suscripción que el proyecto de Azure Migrate.<br/><br/> Azure Migrate admite áreas de trabajo que residen en las regiones Este de EE. UU., Sudeste Asiático y Oeste de Europa.<br/><br/>  El área de trabajo debe estar en una región en la que [se admita Service Map](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-overview#prerequisites).<br/><br/> El área de trabajo de un proyecto de Azure Migrate no se puede modificar una vez que se ha agregado.
**Costos** | La solución Service Map no supone ningún gasto durante los primeros 180 días (a partir del día que asocie el área de trabajo de Log Analytics con el proyecto de Azure Migrate).<br/><br/> Transcurridos los 180 días, se aplicarán las tarifas normales de Log Analytics.<br/><br/> Si se usa una solución que no sea Service Map en el área de trabajo de Log Analytics asociada generará los [gastos estándar](https://azure.microsoft.com/pricing/details/log-analytics/) de Log Analytics.<br/><br/> Al eliminar el proyecto de Azure Migrate, el área de trabajo no se elimina con él. Tras la eliminación del proyecto, el uso de Service Map no será gratuito y cada nodo se facturará conforme al nivel de pago del área de trabajo de Log Analytics.<br/><br/>Si tiene proyectos creados antes de que Azure Migrate estuviera disponible con carácter general (el 28 de febrero de 2018), puede que haya incurrido en cargos de Service Map adicionales. Para garantizar el pago solo después de 180 días, es recomendable que cree un nuevo proyecto, ya que las áreas de trabajo existentes antes de la disponibilidad general siguen siendo facturables.
**Administración** | Al registrar agentes en el área de trabajo, se usa el identificador y la clave proporcionados por el proyecto de Azure Migrate.<br/><br/> Puede usar el área de trabajo de Log Analytics fuera de Azure Migrate.<br/><br/> Si elimina el proyecto de Azure Migrate asociado, el área de trabajo no se elimina automáticamente. [Elimínela manualmente](../azure-monitor/platform/manage-access.md).<br/><br/> No elimine el área de trabajo creado por Azure Migrate, a menos que elimine el proyecto de Azure Migrate. Si lo hace, la característica de visualización de dependencias no funcionará según lo previsto.
**Conectividad de Internet** | Si las máquinas no están conectadas a Internet, necesita instalar la puerta de enlace de Log Analytics en ellas.
**Azure Government** | El análisis de dependencias basado en agente no se admite.


## <a name="next-steps"></a>Pasos siguientes

- [Revise](best-practices-assessment.md) los procedimientos recomendados para crear evaluaciones.
- [Prepárese para la evaluación de VMware](tutorial-prepare-vmware.md).
