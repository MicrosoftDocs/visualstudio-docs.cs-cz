---
title: require-azureartifactscredentialprovider
description: devinit Tool vyžaduje – azureartifactscredentialprovider.
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
ms.openlocfilehash: c784bb25fe9abc77cfb562ae085930b275d0ef03
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400286"
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

Výchozím chováním `require-azureartifactscredentialprovider` nástroje je instalace nejnovějšího poskytovatele pověření Azure Artifacts.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file that installs Azure Artifacts Credential Provider.'",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
            "comments": "Installs Azure Artifacts Credential Provider."
        }
    ]
}
```
