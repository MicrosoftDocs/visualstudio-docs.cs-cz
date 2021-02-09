---
title: Privátní beta verze
description: Příklady vlastních nastavení použitých v úložišti GitHub Codespaces sady Visual Studio Preview beta verze.
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
ms.openlocfilehash: 93d71449553de3b27916052ef3fd230bde57fdee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932850"
---
# <a name="private-beta"></a>Privátní beta verze

Tento příklad ukazuje, jak přizpůsobit codespace pro Visual Studio tak, aby měly stejné funkce jako první Codespaces privátní beta verze [GitHubu](https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.json

Obsah [`.devinit.json`](devinit-json.md) souboru Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

```json
{
    "run": [
        {
            "tool": "choco-install",
            "input": "python2"
        },
        {
            "tool": "choco-install",
            "input": "python3"
        },
        {
            "tool": "require-dotnetcoresdk",
            "input": "2.1.807"
        },
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-azurecli"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        },
        {
            "tool": "require-vcpkg"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsna

Obsah _.devcontainer.js_ v souboru v kořenovém adresáři úložiště.

```json
{
  "postCreateCommand": "devinit init"
}
```
