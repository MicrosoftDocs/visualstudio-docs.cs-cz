---
title: require-azureartifactscredentialprovider
description: devinit Tool vyžaduje – azureartifactscredentialprovider.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ad39bc070841dae5202abca8ca4624927a100f23
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440386"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

`require-azureartifactscredentialprovider`Nástroj nainstaluje poskytovatele pověření Azure Artifacts. Zprostředkovatel pověření Azure Artifacts automatizuje získání přihlašovacích údajů potřebných k obnovení balíčků NuGet jako součást pracovního postupu vývoje .NET. Přečtěte si další informace o Azure Artifacts poskytovateli přihlašovacích údajů [tady](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                |
| [**vstup**](#input)                              | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                     |

### <a name="input"></a>Vstup

Nepoužívá se. Pokud je uvedeno, ignoruje všechny vstupy.

### <a name="additional-options"></a>Další možnosti

Další možnosti jsou předány jako příkaz poskytovatele pověření.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-azureartifactscredentialprovider` nástroje je instalace nejnovější verze poskytovatele pověření Azure Artifacts.

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `require-azureartifactscredentialprovider` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.js, které budou instalovat poskytovatele pověření Azure Artifacts:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
