---
title: require-azurecli
description: devinit Tool vyžaduje – Azure CLI.
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
ms.openlocfilehash: d73fe7c1745ded16ca6b0c94acf117c1707c1063
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440414"
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

Výchozím chováním `require-azurecli` nástroje je nainstalovat nejnovější verzi rozhraní příkazového řádku Azure a přidat ho do služby `PATH` .

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