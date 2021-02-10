---
title: azurecli-login
description: devinit Tool Azure CLI – přihlášení.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 94f713ed972e93b761cf7dcdafcfd92e5498d982
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944969"
---
# <a name="azurecli-login"></a>azurecli-login

Tento `azurecli-login` nástroj slouží k přihlášení k Azure Active Directory prostřednictvím rozhraní příkazového [řádku Azure CLI](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest). Tento nástroj používá příkaz Azure CLI: `az login --use-device-code` k dokončení přihlášení budete muset postupovat podle pokynů, které se tisknou do konzoly.

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

Výchozím chováním `azurecli-login` nástroje je nainstalovat nejnovější verzi rozhraní příkazového řádku Azure a přidat ho do služby `PATH` .

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `azurecli-login` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-trigger-azure-login"></a>.devinit.js, který spustí přihlášení Azure:

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "azurecli-login"
        }
    ]
}
```