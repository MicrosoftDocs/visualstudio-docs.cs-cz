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
ms.openlocfilehash: e9d2f546e99f83b4c53d0b76abfdaf8ec91868ac
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672109"
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
Níže je uveden příklad, jak spustit `require-vscomponent` pomocí `.devinit.json` . 

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.js, která importuje konfigurace dané cesty k souboru. vsconfig:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```