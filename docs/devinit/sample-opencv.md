---
title: OpenCV
description: Příkladem přizpůsobení pomocí devinit můžete pro úložiště OpenCV cílit na Linux i Windows.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 6524cec090f20c475724f1ae8615c5dd24cfa2d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943503"
---
# <a name="opencv"></a>OpenCV

Tento příklad ukazuje, jak přizpůsobit [Codespaces GitHubu](https://github.com/features/codespaces) , aby bylo možné vyvíjet projekty s více platformami, jako je [OpenCV/OpenCV](https://github.com/opencv/opencv).

Následující vlastní nastavení jsou již použita na rozvětvení [Microsoft/OpenCV](https://github.com/microsoft/opencv) a umožňují sestavit cílení na systém Windows a Ubuntu.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Přizpůsobení pomocí devcontainer.jsa devinit.jsna

`.devcontainer`Adresář musí obsahovat následující soubory:

* devcontainer.json
* devinit.jsna

### <a name="devcontainerjson"></a>devcontainer.json

Následuje obsah _devcontainer.jsv_ souboru.

```json
{
  "postCreateCommand": "devinit init"
}
```

`postCreateCommand`Spustí nástroj [devinit](devinit-and-codespaces.md) , který spotřebovává _devinit.js_.

### <a name="devinitjson"></a>devinit.jsna

Následuje obsah [_devinit.jsv_](devinit-json.md) souboru.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages useful for C++ development.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

_devinit.jsv_ je soubor spotřebovaný nástrojem [devinit](devinit-and-codespaces.md) a musí být ve stejném adresáři jako _devcontainer.jsv_.

V této ukázce se nástroj [WSL-Install](tool-wsl-install.md) používá k vytvoření instance WSL se systémem Ubuntu 20,04 a jejím zřízení se základními nástroji pro vývoj v jazyce C++.
## <a name="targeting-windows-or-linux"></a>Cílení na systém Windows nebo Linux

Výchozí konfigurace sestavení cílící na systém Windows je vždy vytvořena s názvem `x64-Debug` .

Přidáním výše zmíněných souborů, po vytvoření instance Codespace, Visual Studio zřídí nové připojení SSH ve [Správci připojení](/cpp/linux/connect-to-your-remote-linux-computer)a vytvoří novou konfiguraci v nástroji pro výběr konfigurace, který cílí na instanci Ubuntu prostřednictvím připojení SSH.

![Konfigurace cílící na Ubuntu](media/wsl-ssh-linux-configuration.png).

Výběrem zvýrazněné konfigurace, která cílí na WSL, je možné sestavit a ladit cíle sestavení OpenCV.
