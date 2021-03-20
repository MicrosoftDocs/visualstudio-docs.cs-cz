---
title: require-psmodule
description: devinit Tool vyžaduje – psmodule.
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
ms.openlocfilehash: cdb37bf4e714cfc25e5bf82354856fd4d3d63e87
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672698"
---
# <a name="require-psmodule"></a>require-psmodule

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.


Tento `require-psmodule` Nástroj se používá k instalaci [modulu PowerShellu](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) z [Galerie prostředí PowerShell](https://www.powershellgallery.com/) prostřednictvím [instalačního modulu](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), aby ho bylo možné použít ve skriptech PowerShellu.

> [!TIP]
> Až se modul nainstaluje, bude dál potřeba ho importovat do skriptu pomocí [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).

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

Další možnosti jsou předány přímo do příkazu [install-Module](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) a jsou zdokumentovány na [Microsoft docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7).

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-psmodule` nástroje je chyba, jak `input` je požadováno.

### <a name="built-in-options"></a>Předdefinované možnosti

`require-psmodule`Nástroj nastaví řadu `Install-Module` argumentů příkazového řádku, aby bylo zajištěno, že `Install-Module` může běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v [instalačním modulu](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Název         | Description                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Nainstaluje modul a přepíše varovné zprávy týkající se konfliktů při instalaci modulu. Pokud v počítači již existuje modul se stejným názvem, vynutí aplikace vynutit instalaci více verzí. Přepíše modul, pokud existuje stávající modul se stejným názvem a verzí. Vynutit a AllowClobber lze použít společně v příkazu Install-Module. |
| **-WhatIf**  | -Příznak WhatIf je přidán, pokud je předán suchý běh pro `devinit` příkaz.                                                                                                                                                                                                                                                                                                       |
| **– Verbose** | – Příznak verbose je přidán, pokud je předána podrobnost `devinit` příkazu pro příkaz.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `require-psmodule` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-powershellget-module"></a>.devinit.js, které budou instalovat modul PowerShellGet:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-powershellget-module-from-a-specific-repository"></a>.devinit.js, který bude instalovat modul PowerShellGet z konkrétního úložiště:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```