---
title: Aplikace v .NET Core
description: Příklad úložiště, které používá devinit k instalaci konkrétního .NET Core SDK.
ms.date: 10/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ce94dc9cf4b6368a96cc027e1a9fc14e0d7e0650
ms.sourcegitcommit: 7915cedf2f5988db25cb90042aa8466a1d3cee7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2020
ms.locfileid: "93028143"
---
# <a name="net-core-app"></a>Aplikace v .NET Core

Úplný příklad použití devinit k instalaci požadované verze .NET Core SDK v Codespaces najdete v úložišti [DevinitExample](https://github.com/microsoft/DevinitExample) .

## <a name="devinitjson"></a>.devinit.json

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