---
title: Aplikace v .NET Core
description: Příklad úložiště, které používá devinit k instalaci konkrétního .NET Core SDK.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 364b3fbb0739891d1ce0f6341bb11af7f0ff76f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943583"
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
