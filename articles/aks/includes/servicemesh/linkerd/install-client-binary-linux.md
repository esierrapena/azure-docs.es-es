---
author: paulbouwer
ms.topic: include
ms.date: 10/09/2019
ms.author: pabouwer
ms.openlocfilehash: 7a22256c88f9cee3ce62c68a2de4a5974d76f026
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "77593748"
---
## <a name="download-and-install-the-linkerd-linkerd-client-binary"></a>Descarga e instalación del binario de cliente linkerd de Linkerd

En un shell basado en Bash en Linux o en el [Subsistema de Windows para Linux][install-wsl], use `curl` para descargar la versión de Linkerd tal como se indica a continuación:

```bash
# Specify the Linkerd version that will be leveraged throughout these instructions
LINKERD_VERSION=stable-2.6.0

curl -sLO "https://github.com/linkerd/linkerd2/releases/download/$LINKERD_VERSION/linkerd2-cli-$LINKERD_VERSION-linux"
```

El binario de cliente `linkerd` se ejecuta en la máquina cliente y permite interactuar con la malla de servicio de Linkerd. Use los comandos siguientes para instalar el binario de cliente `linkerd` de Linkerd en un shell basado en Bash en Linux o en el [Subsistema de Windows para Linux][install-wsl]. Estos comandos copian el binario de cliente `linkerd` en la ubicación del programa de usuario estándar en su `PATH`.

```bash
sudo cp ./linkerd2-cli-$LINKERD_VERSION-linux /usr/local/bin/linkerd
sudo chmod +x /usr/local/bin/linkerd
```

Si desea completar la línea de comandos del binario de cliente `linkerd` de Linkerd, realice la siguiente configuración:

```bash
# Generate the bash completion file and source it in your current shell
mkdir -p ~/completions && linkerd completion bash > ~/completions/linkerd.bash
source ~/completions/linkerd.bash

# Source the bash completion file in your .bashrc so that the command-line completions
# are permanently available in your shell
echo "source ~/completions/linkerd.bash" >> ~/.bashrc
```

<!-- LINKS - external -->
[install-wsl]: https://docs.microsoft.com/windows/wsl/install-win10