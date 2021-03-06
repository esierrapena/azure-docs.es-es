---
title: Denegación del acceso a una red pública para el servidor único de Azure Database for PostgreSQL con Azure Portal
description: Información acerca de cómo configurar la denegación del acceso a una red pública mediante el servidor único de Azure Database for PostgreSQL con Azure Portal
author: kummanish
ms.author: manishku
ms.service: postgresql
ms.topic: how-to
ms.date: 03/10/2020
ms.openlocfilehash: b51a79027ce834190a4fae5d893e47f2be16abf7
ms.sourcegitcommit: d7008edadc9993df960817ad4c5521efa69ffa9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2020
ms.locfileid: "86102198"
---
# <a name="deny-public-network-access-in-azure-database-for-postgresql-single-server-using-azure-portal"></a>Denegación del acceso a una red pública en el servidor único de Azure Database for PostgreSQL con Azure Portal

En este artículo se describe cómo puede configurar un servidor único de Azure Database for PostgreSQL para denegar todas las configuraciones públicas y permitir solo las conexiones mediante puntos de conexión privados para mejorar aún más la seguridad de la red.

## <a name="prerequisites"></a>Requisitos previos

Para completar esta guía, necesita:

* Un [servidor único de Azure Database for PostgreSQL](quickstart-create-PostgreSQL Single server-server-database-using-azure-portal.md)

## <a name="set-deny-public-network-access"></a>Establecimiento de la denegación del acceso a una red pública

Siga estos pasos para establecer la denegación del acceso a una red pública del servidor único de PostgreSQL:

1. En [Azure Portal](https://portal.azure.com/), seleccione un servidor único existente de Azure Database for PostgreSQL.

1. En la página del servidor único de PostgreSQL, en **Configuración**, haga clic en **Seguridad de la conexión** para abrir la página de configuración de seguridad de la conexión.

1. En **Denegar acceso de red pública**, seleccione **Sí** para habilitar la denegación del acceso público para el servidor único de PostgreSQL.

    ![Denegación de acceso de red del servidor único de Azure Database for PostgreSQL](./media/howto-deny-public-network-access/deny-public-network-access.PNG)

1. Haga clic en **Guardar** para guardar los cambios.

1. Se enviara una notificación para confirmar la correcta habilitación de la configuración de seguridad de la conexión.

    ![Denegación de acceso de red correcta para el servidor único de Azure Database for PostgreSQL](./media/howto-deny-public-network-access/deny-public-network-access-success.png)

## <a name="next-steps"></a>Pasos siguientes

Aprenda sobre la [creación de alertas de métricas](howto-alert-on-metric.md).