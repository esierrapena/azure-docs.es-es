---
title: Uso de un firewall
titleSuffix: Azure Machine Learning
description: Controle el acceso a las áreas de trabajo de Azure Machine Learning con instancias de Azure Firewall. Obtenga información acerca de los hosts que debe permitir a través del firewall para que Azure Machine Learning funcione correctamente.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: how-to
ms.author: aashishb
author: aashishb
ms.reviewer: larryfr
ms.date: 04/27/2020
ms.custom: tracking-python
ms.openlocfilehash: 31daec93352c0e142075a55c61f2b8d3a6d56fab
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85080238"
---
# <a name="use-workspace-behind-azure-firewall-for-azure-machine-learning"></a>Uso de áreas de trabajo detrás de Azure Firewall para Azure Machine Learning

En este artículo, aprenderá a configurar Azure Firewall para usarlo con un área de trabajo de Azure Machine Learning.

Azure Firewall puede usarse para controlar el acceso al área de trabajo de Azure Machine Learning y a la red pública de Internet. Si no está configurado correctamente, el firewall puede provocar problemas al usar el área de trabajo. Hay una serie de nombres de host que se usan en el área de trabajo de Azure Machine Learning, que se describen en este artículo.

## <a name="network-rules"></a>Reglas de red

En el firewall, cree una regla de red que permita el tráfico entrante y saliente de las direcciones de este artículo.

> [!TIP]
> Al agregar la regla de red, establezca __Protocolo__ en cualquiera y los puertos en `*`.
>
> Para más información sobre la configuración de Azure Firewall, consulte [Implementación y configuración de Azure Firewall](../firewall/tutorial-firewall-deploy-portal.md#configure-a-network-rule).

## <a name="microsoft-hosts"></a>Hosts de Microsoft

Los hosts de esta sección son propiedad de Microsoft y proporcionan servicios necesarios para que el área de trabajo funcione correctamente.

| **Nombre de host** | **Propósito** |
| ---- | ---- |
| **\*.batchai.core.windows.net** | Clústeres de entrenamiento |
| **ml.azure.com** | Azure Machine Learning Studio |
| **default.exp-tas.com** | Se usa por Azure Machine Learning Studio. |
| **\*.azureml.ms** | Usado por las API de Azure Machine Learning |
| **\*.experiments.azureml.net** | Usado por experimentos que se ejecutan en Azure Machine Learning |
| **\*.modelmanagement.azureml.net** | Usado para registrar e implementar modelos|
| **mlworkspace.azure.ai** | Usado por Azure Portal al visualizar un área de trabajo |
| **\*.aether.ms** | Usado al ejecutar canalizaciones de Azure Machine Learning |
| **\*.instances.azureml.net** | Instancias de proceso de Azure Machine Learning |
| **\*.instances.azureml.ms** | Instancias de proceso de Azure Machine Learning cuando el área de trabajo tiene habilitado Private Link. |
| **windows.net** | Azure Blob Storage |
| **vault.azure.net** | Azure Key Vault |
| **azurecr.io** | Azure Container Registry |
| **mcr.microsoft.com** | Microsoft Container Registry para imágenes de Docker base |

## <a name="python-hosts"></a>Hosts de Python

Los hosts de esta sección se usan para instalar paquetes de Python. Son necesarios durante el desarrollo, el entrenamiento y la implementación. 

| **Nombre de host** | **Propósito** |
| ---- | ---- |
| **anaconda.com** | Usado al instalar paquetes Conda |
| **pypi.org** | Usado al instalar paquetes pip |

## <a name="r-hosts"></a>Hosts de R

Los hosts de esta sección se usan para instalar paquetes de R. Son necesarios durante el desarrollo, el entrenamiento y la implementación.

> [!IMPORTANT]
> Internamente, el SDK de R para Azure Machine Learning usa paquetes de Python. Por lo tanto, también debe permitir los hosts de Python a través del firewall.

| **Nombre de host** | **Propósito** |
| ---- | ---- |
| **cloud.r-project.org** | Usado al instalar paquetes CRAN |

Pasos siguientes

* [[Implementación y configuración de Azure Firewall](../firewall/tutorial-firewall-deploy-portal.md)]
* [Protección de los trabajos de experimentación e inferencia de ML en una instancia de Azure Virtual Network](how-to-enable-virtual-network.md)
