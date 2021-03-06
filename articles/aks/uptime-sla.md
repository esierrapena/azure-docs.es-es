---
title: Azure Kubernetes Service (AKS) con acuerdo de nivel de servicio de tiempo de actividad
description: Obtenga información sobre la oferta opcional de acuerdo de nivel de servicio de tiempo de actividad para el servidor de API de Azure Kubernetes Service (AKS).
services: container-service
ms.topic: conceptual
ms.date: 05/19/2020
ms.custom: references_regions
ms.openlocfilehash: 2df0ad675f03b25363ab0f5b13dceb762a657ed7
ms.sourcegitcommit: d118ad4fb2b66c759b70d4d8a18e6368760da3ad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84299560"
---
# <a name="azure-kubernetes-service-aks-uptime-sla"></a>Acuerdo de nivel de servicio de tiempo de actividad de Azure Kubernetes Service (AKS)

El acuerdo de nivel de servicio (SLA) de tiempo de actividad es una característica opcional para habilitar un mejor acuerdo de nivel de servicio con respaldo financiero para un clúster. El acuerdo de nivel de servicio de tiempo de actividad garantiza una disponibilidad del 99,95 % del punto de conexión del servidor de API de Kubernetes para los clústeres que usan [zonas de disponibilidad][availability-zones], y una disponibilidad del 99,9 % de los clústeres que no utilizan zonas de disponibilidad. AKS usa réplicas de nodo maestro en los dominios de actualización y de error para garantizar que se cumplan los requisitos del acuerdo de nivel de servicio.

Los clientes que necesiten un acuerdo de nivel de servicio para alcanzar los requisitos de cumplimiento o que requieren extender un acuerdo de nivel de servicio a sus usuarios finales deben habilitar esta característica. Los clientes con cargas de trabajo críticas que se beneficien de un mayor acuerdo de nivel de servicio de tiempo de actividad también pueden beneficiarse. El uso de la característica de acuerdo de nivel de servicio de tiempo de actividad con zonas de disponibilidad permite una mayor disponibilidad para el tiempo de actividad del servidor de API de Kubernetes.  

Los clientes todavía pueden crear un número ilimitado de clústeres gratuitos con un objetivo de nivel de servicio (SLO) del 99,5 %, y optar por el tiempo de actividad preferido del SLO o SLA según sea necesario.

> [!Important]
> En el caso de los clústeres con bloqueo de salida, consulte la [limitación del tráfico de salida](limit-egress-traffic.md) para abrir los puertos adecuados.

## <a name="sla-terms-and-conditions"></a>Términos y condiciones del acuerdo de nivel de servicio

El acuerdo de nivel de servicio de tiempo de actividad es una característica de pago y se habilita para cada clúster. El precio del acuerdo de nivel de servicio de tiempo de actividad viene determinado por el número de clústeres discretos, no por el tamaño de los clústeres individuales. Puede ver los [Detalles de precios de los acuerdos de nivel de servicio de tiempo de actividad](https://azure.microsoft.com/pricing/details/kubernetes-service/) para obtener más información.

## <a name="before-you-begin"></a>Antes de empezar

* La CLI de Azure, versión 2.7.0 o posterior

## <a name="creating-a-cluster-with-uptime-sla"></a>Creación de un clúster con un acuerdo de nivel de servicio de tiempo de actividad

Para crear un nuevo clúster con el acuerdo de nivel de servicio de tiempo de actividad, use la CLI de Azure.

En el ejemplo siguiente, se crea un grupo de recursos denominado *myResourceGroup* en la ubicación *eastus*.

```azurecli-interactive
az group create --name myResourceGroup --location eastus
```
Use el comando [az aks create][az-aks-create] para crear un clúster de AKS. En el siguiente ejemplo se crea un clúster denominado *myAKSCluster* con un nodo. Azure Monitor para contenedores también se habilita usando el parámetro *--enable-addons monitoring*.  La operación tarda varios minutos en completarse.

```azurecli-interactive
az aks create --resource-group myResourceGroup --name myAKSCluster --uptime-sla --node-count 1 --enable-addons monitoring --generate-ssh-keys
```
Transcurridos unos minutos, el comando se completa y devuelve información en formato JSON sobre el clúster. El siguiente fragmento JSON muestra el nivel de pago de la SKU, que indica que el clúster tiene habilitado el acuerdo de nivel de servicio de tiempo de actividad.

```output
  },
  "sku": {
    "name": "Basic",
    "tier": "Paid"
  },
```

## <a name="limitations"></a>Limitaciones

* Actualmente, no se puede convertir un clúster existente para habilitar el acuerdo de nivel de servicio de tiempo de actividad.
* Actualmente, no hay ninguna manera de quitar un acuerdo de nivel de servicio de tiempo de actividad de un clúster de AKS después de crearlo con la característica habilitada.  
* Por el momento no se admiten los clústeres privados.

## <a name="next-steps"></a>Pasos siguientes

Use [Availability Zones][availability-zones] para aumentar la alta disponibilidad con las cargas de trabajo del clúster de AKS.
Configure el clúster para [limitar el tráfico de salida](limit-egress-traffic.md).

<!-- LINKS - External -->
[azure-support]: https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest
[region-availability]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service

<!-- LINKS - Internal -->
[vm-skus]: ../virtual-machines/linux/sizes.md
[nodepool-upgrade]: use-multiple-node-pools.md#upgrade-a-node-pool
[faq]: ./faq.md
[availability-zones]: ./availability-zones.md
[az-aks-create]: /cli/azure/aks?view=azure-cli-latest#az-aks-create
[limit-egress-traffic]: ./limit-egress-traffic.md
[az-extension-add]: /cli/azure/extension#az-extension-add
[az-extension-update]: /cli/azure/extension#az-extension-update
