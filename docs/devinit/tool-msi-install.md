---
title: MSI – instalace
description: devinit Tool for Msiexec.
ms.date: 10/13/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 98667c602272f22e7803647a688ee75d6c6cbd70
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402265"
---
# <a name="msi-install"></a>MSI – instalace

`msi-install`Nástroj se používá k instalaci `.msi` formátů souborů balíčku pomocí souboru [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

## <a name="usage"></a>Využití

Pokud `input` je hodnota vynechána nebo je prázdná, nástroj při výstupu zobrazí chybu.

| Název                                         | Typ   | Vyžadováno | Hodnota                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **vyjádření**                                 | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                             |
| [**vstup**](#input)                          | řetězec | Yes      | `msi`Instalace. Podrobnosti najdete níže v části o [zadání](#input) .                      |
| [**additionalOptions**](#additional-options) | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                  |

### <a name="input"></a>Vstup

Vlastnost input slouží k zadání cesty nebo adresy URL k `.msi` souboru, který bude nainstalován. Pokud cesta k `.msi` není správná nebo adresa URL neukazuje na `.msi` přímo, `msi-install` instalační balíček se nedá otevřít.

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace je možné předat jako hodnotu additionalOptions. Tyto argumenty jsou přímým průchodem argumentů používaných `msiexec` a jsou definovány v `msiexec` [dokumentaci](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

### <a name="built-in-options"></a>Předdefinované možnosti

Nástroj pro instalaci MSI nastaví řadu `msiexec` argumentů příkazového řádku, aby mohla služba MSI běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v `msiexec` [dokumentaci](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

| Název          | Popis                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Spustí normální instalaci.                                                                                                                                                                    | 
| /quiet        | Určuje tichý režim bez nutnosti zásahu uživatele.                                                                                                                                        | 
| /Qn           | Určuje, že během procesu instalace není žádné uživatelské rozhraní.                                                                                                                                           | 
| /passive      | Určuje bezobslužný režim, ve kterém se při instalaci zobrazuje indikátor průběhu.                                                                                                                    | 
| /l * V          | Zapne protokolování a protokolování všech informací, včetně podrobných informací, do `devinit.log` souboru v místní složce Temp v počítači. Pokud se nástroj nezdařil, je zobrazena cesta k souboru protokolu.      | 
| /norestart    | Zastaví restart počítače po dokončení instalace, ale vrátí ukončovací kód 3010, pokud je potřeba restartovat počítač.                                                                  | 

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "comments": "Installs the 7-Zip MSI",
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
