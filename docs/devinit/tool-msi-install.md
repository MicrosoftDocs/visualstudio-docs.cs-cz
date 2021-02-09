---
title: msi-install
description: devinit Tool for Msiexec.
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
ms.openlocfilehash: 9b177d63ceabd8162c5ddd77e87c68d4a820b00a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896236"
---
# <a name="msi-install"></a>msi-install

`msi-install`Nástroj se používá k instalaci `.msi` formátů souborů balíčku pomocí souboru [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

## <a name="usage"></a>Využití

Pokud `input` je hodnota vynechána nebo je prázdná, nástroj při výstupu zobrazí chybu.

| Název                                         | Typ   | Vyžadováno | Hodnota                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **vyjádření**                                 | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                             |
| [**vstup**](#input)                          | řetězec | Ano      | `msi`Instalace. Podrobnosti najdete níže v části o [zadání](#input) .                      |
| [**additionalOptions**](#additional-options) | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                  |

### <a name="input"></a>Vstup

Vlastnost input slouží k zadání cesty nebo adresy URL k `.msi` souboru, který bude nainstalován. Pokud cesta k `.msi` není správná nebo adresa URL neukazuje na `.msi` přímo, `msi-install` instalační balíček se nedá otevřít.

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace je možné předat jako hodnotu additionalOptions. Tyto argumenty jsou přímým průchodem argumentů používaných `msiexec` a jsou definovány v `msiexec` [dokumentaci](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

### <a name="built-in-options"></a>Předdefinované možnosti

Nástroj pro instalaci MSI nastaví řadu `msiexec` argumentů příkazového řádku, aby mohla služba MSI běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v `msiexec` [dokumentaci](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

| Název          | Description                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Spustí normální instalaci.                                                                                                                                                                    |
| /quiet        | Určuje tichý režim bez nutnosti zásahu uživatele.                                                                                                                                        |
| /Qn           | Určuje, že během procesu instalace není žádné uživatelské rozhraní.                                                                                                                                           |
| /passive      | Určuje bezobslužný režim, ve kterém se při instalaci zobrazuje indikátor průběhu.                                                                                                                    |
| /l * V          | Zapne protokolování a protokolování všech informací, včetně podrobných informací, do `devinit.log` souboru v místní složce Temp v počítači. Pokud se nástroj nezdařil, je zobrazena cesta k souboru protokolu.      |
| /norestart    | Zastaví restart počítače po dokončení instalace, ale vrátí ukončovací kód 3010, pokud je potřeba restartovat počítač.                                                                  |

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `msi-install` nástroje je chyba, protože `input` vlastnost je povinná.

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `msi-install` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-7-zip-msi"></a>.devinit.js, na které se nainstaluje soubor MSI pro 7-zip:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
