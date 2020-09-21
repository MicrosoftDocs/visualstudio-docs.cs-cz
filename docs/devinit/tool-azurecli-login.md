---
title: Azure CLI – přihlášení
description: devinit Tool Azure CLI – přihlášení.
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
ms.openlocfilehash: e95bc70540ae73c73a17a94b4cadfc399c8557e5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810170"
---
# <a name="azurecli-login"></a>Azure CLI – přihlášení

Tento `azurecli-login` nástroj slouží k přihlášení k Azure Active Directory prostřednictvím rozhraní příkazového [řádku Azure CLI](https://docs.microsoft.com/cli/azure/authenticate-azure-cli?view=azure-cli-latest&preserve-view=true). Tento nástroj používá příkaz Azure CLI: `az login --use-device-code` k dokončení přihlášení budete muset postupovat podle pokynů, které se tisknou do konzoly.

## <a name="usage"></a>Využití

Pokud jsou obě vlastnosti vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

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

Výchozím chováním `azurecli-login` nástroje je nainstalovat nejnovější verzi rozhraní příkazového řádku Azure CLI a přidat ji do cesty (jenom Windows).

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger az login --use-device-code behavior.",
            "tool": "azurecli-login"
        }
    ]
}
```
