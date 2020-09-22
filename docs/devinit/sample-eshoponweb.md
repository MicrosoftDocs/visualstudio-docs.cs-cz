---
title: eShopOnWeb
description: Příklad přizpůsobení pomocí devinit pro úložiště dotnet-Architecture/eShopOnWeb.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 052e89d276e122ebf44c2b541771bbb314f48ade
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809102"
---
# <a name="eshoponweb"></a>eShopOnWeb

Tento příklad ukazuje, jak přizpůsobit příklad [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) architektury dotnet pro automatické zřízení [Codespaces GitHubu](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Tento skript se volá z _PostCloneSetup.ps1_ a dá se taky místně nainstalovat, aby se úložiště nastavilo. Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

```batch
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.jsna

Obsah [_.devinit.jsv_](devinit-json.md) souboru. Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

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
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
