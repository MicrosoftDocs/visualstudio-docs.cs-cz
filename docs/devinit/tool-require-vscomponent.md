---
title: require-vscomponent
description: devinit Tool vyžaduje – vscomponent.
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
ms.openlocfilehash: 1069fce8c785fa80143f794e8ce083b7c0e86eaf
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400244"
---
# <a name="require-vscomponent"></a>require-vscomponent

Tento `require-vscomponent` nástroj slouží k importu konfigurací sady Visual Studio do existující sady Visual Studio. Další informace `.vsconfig` [najdete tady](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                     | Typ   | Vyžadováno | Hodnota                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **vyjádření**                             | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                |
| [**vstup**](#input)                      | řetězec | No       | Úplná cesta k `.vsconfig` . Podrobnosti najdete níže v části o [zadání](#input) . |
| [additionalOptions](#additional-options) | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .     |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení úplné cesty k `.vsconfig` souboru. Pokud není uvedeno, nástroj vyhledá `.vsconfig` v aktuálním adresáři a předáte hodnotu do instalační program pro Visual Studio.

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-vscomponent` nástroje je vyhledat `.vsconfig` soubor v aktuálním adresáři a spustit instalační program pro Visual Studio s těmito podrobnostmi v tichém režimu. `require-vscomponent` podporuje pouze úpravu stávající instalace sady Visual Studio.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "comments": "Imports .vsconfig file which is passed as input to Visual Studio.",
            "input": "C:\\.vsconfig"
        }
    ]
}
```