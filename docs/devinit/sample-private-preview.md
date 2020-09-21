---
title: Privátní verze Preview
description: Příklady vlastních nastavení použitých v úložišti GitHub Codespaces sady Visual Studio ve verzi Preview beta.
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
ms.openlocfilehash: c240cee6595f060c5347cafc4379a7fc27c8d310
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809088"
---
# <a name="private-preview"></a>Privátní verze Preview

Tento příklad ukazuje, jak přizpůsobit codespace pro Visual Studio tak, aby měly stejné funkce jako první Codespaces privátní beta verze [GitHubu](https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.jsna

Obsah [_.devinit.jsv_](devinit-json.md) souboru. Tento soubor musí být ve stejné složce jako _.devcontainer.jsna_.

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
