---
title: Winget – instalace
description: Nástroj devinit pro Winget.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 3c236e63686d3882ed199c122fed9ebddfa8fa20
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2021
ms.locfileid: "100012362"
---
# <a name="winget-install"></a>Winget – instalace

`winget-install`Nástroj se používá k instalaci [balíčků Winget](https://docs.microsoft.com/windows/package-manager/winget/).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj při výstupu zobrazí chybu.

| Název                                         | Typ   | Vyžadováno | Hodnota                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **vyjádření**                                 | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                             |
| [**vstup**](#input)                          | řetězec | No       | Balíček, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .                    |
| [**additionalOptions**](#additional-options) | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                  |

### <a name="input"></a>Vstup

Vlastnost input slouží k zadání `Id` nebo `Name` balíčku, který má být nainstalován (například MongoDB. Server). Hodnota vstup bude připojena k `winget install` příkazu (například `winget install MongoDB.Server` ). Pokud název balíčku není jedinečný a odpovídá jiným balíčkům, můžete zadat `Id` balíček a přidat `--exact` příznak k `additionalOptions` tomu, abyste zajistili, že identita balíčku přesně odpovídá. `Id`Balíček se dá najít spuštěním `winget search` příkazu a použitím `Id` parametru pro balíček.  

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace je možné předat jako hodnotu additionalOptions. Tyto argumenty jsou přímo Passthrough na argumenty používané `winget install` a jsou definovány v `winget install` [dokumentaci](https://docs.microsoft.com/windows/package-manager/winget/install).

#### <a name="manifests"></a>Manifesty

Další volitelná `winget` Podpora je možnost poskytnutí [souboru manifestu](https://docs.microsoft.com/windows/package-manager/winget/install#local-install) , který podrobně popisuje balíček, který se má nainstalovat. Pro použití této funkce s devinit `input` by měl být parametr prázdný a `additionalOptions` vlastnost by měla obsahovat `--manifest` možnost následovanou cestou k manifestu (například `--manifest path.to.manifest.yml` ).

### <a name="built-in-options"></a>Předdefinované možnosti

Nástroj Winget-Install nastaví řadu argumentů příkazového řádku Winget, aby Winget mohl běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v `winget install` [dokumentaci](https://docs.microsoft.com/windows/package-manager/winget/install).

| Název     | Description                                                                                                                       |
|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| --tiché | Spustí instalační program v tichém režimu. Tím se potlačí všechna uživatelská rozhraní. Ve výchozím prostředí se zobrazuje průběh instalačního programu.                       | 

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "run": [
        {
            "comments": "Installs Microsoft PowerToys.",
            "tool": "winget-install",
            "input": "Microsoft.PowerToys",
            "additionalOptions": "--version 0.15.2",
        },
        {
            "comments": "Installs PostgreSQL.",
            "tool": "winget-install",
            "input": "PostgreSQL.PostgreSQL",
            "additionalOptions": "--exact"
        },
        {
            "comments": "Installs the package defined in winget-manifest.yml.",
            "tool": "winget-install",
            "additionalOptions": "--manifest winget-manifest.yml"
        }
    ]
}
```
