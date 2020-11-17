---
title: require-azurecli
description: devinit Tool vyžaduje – Azure CLI.
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
ms.openlocfilehash: da6ce656e552a7df0b02fd4a0df3a1fb78871607
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672144"
---
# <a name="require-azurecli"></a>require-azurecli

Tento `require-azurecli` nástroj slouží k instalaci [Azure CLI](/cli/azure/?view=azure-cli-latest&preserve-view=true) přes Azure CLI MSI.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                          |
| [**vstup**](#input)                              | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části o [zadání](#input) .                               |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části [Další možnosti](#additional-options) .     |

### <a name="input"></a>Vstup

Nepoužívá se.

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-azurecli` nástroje je nainstalovat nejnovější verzi rozhraní příkazového řádku Azure CLI a přidat ji do cesty (jenom Windows).

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `require-azurecli` pomocí `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>.devinit.js, na které se nainstaluje Azure CLI:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azurecli"
        }
    ]
}
```