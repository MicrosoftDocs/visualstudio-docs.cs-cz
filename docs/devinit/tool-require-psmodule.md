---
title: require-psmodule
description: devinit Tool vyžaduje – psmodule.
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
ms.openlocfilehash: 4e30a333812e2c313f9e35934643bcea03cf054c
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352233"
---
# <a name="require-psmodule"></a>require-psmodule

Tento `require-psmodule` Nástroj se používá k instalaci [modulu PowerShellu](https://docs.microsoft.com/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) z [Galerie prostředí PowerShell](https://www.powershellgallery.com/) prostřednictvím [instalačního modulu](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), aby ho bylo možné použít ve skriptech PowerShellu.

> [!TIP] 
> Až se modul nainstaluje, bude dál potřeba ho importovat do skriptu pomocí [Import-Module](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                   |
| [**vstup**](#input)                              | řetězec | Yes      | Balíčky, které se mají nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .                       |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části [Další možnosti](#additional-options) .              |

### <a name="input"></a>Vstup

`input`Vlastnost by měla být `Name` modul PowerShellu, který se má nainstalovat. Seznam dostupných modulů PowerShellu najdete tak, že vyhledáte [Galerie prostředí PowerShell](https://www.powershellgallery.com/).

### <a name="additional-options"></a>Další možnosti

Další možnosti jsou předány přímo do příkazu [install-Module](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) a jsou zdokumentovány na [Microsoft docs](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-psmodule` nástroje je chyba, jak `input` je požadováno.

## <a name="builtin-options"></a>Předdefinované možnosti

`require-psmodule`Nástroj nastaví řadu `Install-Module` argumentů příkazového řádku, aby bylo zajištěno, že `Install-Module` může běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v [instalačním modulu](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Název         | Popis                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Nainstaluje modul a přepíše varovné zprávy týkající se konfliktů při instalaci modulu. Pokud v počítači již existuje modul se stejným názvem, vynutí aplikace vynutit instalaci více verzí. Přepíše modul, pokud existuje stávající modul se stejným názvem a verzí. Vynutit a AllowClobber lze použít společně v příkazu install-Module. |
| **-WhatIf**  | -Příznak WhatIf je přidán, pokud je předán suchý běh pro `devinit` příkaz.                                                                                                                                                                                                                                                                                                       |
| **– Verbose** | – Příznak verbose je přidán, pokud je předána podrobnost `devinit` příkazu pro příkaz.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the PowerShellGet module.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        },
        {
            "comments": "Installs the PowerShellGet module from a specific repository.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```
