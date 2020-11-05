---
title: Aplikace v .NET Core
description: Příklad úložiště, které používá devinit k instalaci konkrétního .NET Core SDK.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 26386631946bd37920ba89490a6210031ef945a6
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398340"
---
# <a name="net-core-app"></a>Aplikace v .NET Core

Úplný příklad použití devinit k instalaci požadované verze .NET Core SDK v Codespaces najdete v úložišti [devinit-example-dotnet-Core](https://github.com/microsoft/devinit-example-dotnet-core) .

## <a name="devinitjson"></a>.devinit.json

Obsah _.devinit.js_ v souboru v kořenovém adresáři úložiště.

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the .NET Core SDK specified in the global.json file.",
      "tool": "require-dotnetcoresdk"
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

## <a name="globaljson"></a>global.json

Obsah _global.js_ v souboru v kořenovém adresáři úložiště.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
