---
title: eShopOnWeb
description: Příklad přizpůsobení pomocí devinit pro úložiště dotnet-Architecture/eShopOnWeb.
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
ms.openlocfilehash: b981b9bb066057228fed07aa7ea26aeab4670ae4
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438213"
---
# <a name="eshoponweb"></a>eShopOnWeb

Tento příklad ukazuje, jak přizpůsobit příklad [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) architektury dotnet pro automatické zřízení [Codespaces GitHubu](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Tento skript se volá z _PostCloneSetup.ps1_ a dá se taky místně nainstalovat, aby se úložiště nastavilo. Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

```console
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.json

Obsah [`.devinit.json`](devinit-json.md) souboru Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsna

Obsah _.devcontainer.js_ v souboru v kořenovém adresáři úložiště.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
