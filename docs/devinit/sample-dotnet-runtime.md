---
title: .NET Core Runtime
description: Příklad přizpůsobení pomocí devinit pro úložiště dotnet/runtime.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b38490217a384e748ae97ec4b808f197b4af3b7b
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005650"
---
# <a name="net-core-runtime"></a>Modul runtime .NET Core

Tento příklad ukazuje, jak přizpůsobit prostředí .NET Core Runtime [dotnet/runtime](https://github.com/dotnet/runtime) pro automatické zřízení na [GitHubu Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Tento skript se volá z _PostCloneSetup.ps1_ a dá se spustit taky místně, aby se nastavilo úložiště. Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

_packages.config_ soubor je [čokoládový](https://chocolatey.org/) soubor, který definuje seznam čokoládových balíčků, které se mají nainstalovat. Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

Obsah [_.devinit.jsv_](devinit-json.md) souboru. Tento soubor musí být ve stejné složce jako _.devcontainer.jsv_ souboru.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "choco-install",
            "input": "packages.config"
        },
        {
            "tool": "require-vscomponent"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsna

Obsah _.devcontainer.js_ v souboru v kořenovém adresáři úložiště.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
