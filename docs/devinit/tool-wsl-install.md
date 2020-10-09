---
title: wsl-install
description: devinit Tool WSL – Install.
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
ms.openlocfilehash: 950ca7f1e9c43123b206893dbc6a07da7c3743ec
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862858"
---
# <a name="wsl-install"></a>wsl-install

Tento `wsl-install` nástroj slouží k instalaci systému Linux distribuce pro [subsystém Windows pro Linux](/windows/wsl/) (WSL).

`wsl-install`Nástroj vyžaduje, aby v systému Windows byla povolena možnost WSL 2. Pokud z nějakého důvodu není WSL2 povolené, můžete WSL2 povolit pomocí nástroje [WindowsFeature – Enable](tool-windowsfeature-enable.md) a názvu funkce `Microsoft-Windows-Subsystem-Linux` .

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                             |
| [**vstup**](#input)                              | řetězec | Ano      | Distribuce, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .     |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .  |

### <a name="input"></a>Vstup

Identifikátor URI balíčku pro distribuci aplikací AppX ( `.appx` ) obsahujícího distribuce pro nasazení. Identifikátor URI musí odkazovat na `.appx` archiv, který obsahuje jednu z `install.tar.gz` nich buď v kořenovém adresáři archivu, nebo uvnitř vnitřního `.appx` archivu. Mezi příklady podporovaných distribuce patří:

| Distribuce                          | Identifikátor URI                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE, přestupné 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> Distribuce platformy ARM Linux se v současnosti v Codespaces GitHubu nepodporují.

### <a name="additional-options"></a>Další možnosti

Podporuje se víc dalších možností:

| Název                      | Typ      | Vyžadováno | Hodnota                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-verze             | řetězec    | No       | Verze WSL, která se má použít Výchozí hodnota je 2.                                                                                                                                  |
| --post-Create-Command     | řetězec    | No       | Příkaz, který se má provést v rámci systému Linux distribuce po dokončení instalace. Příkaz by měl být formátován jako jedno slovo nebo zabalen v uvozovkách. Výchozí hodnota není žádný příkaz.  |

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním tohoto `wsl-install` nástroje je chyba `input` , protože vlastnost distribuce, která se má nainstalovat, je povinná.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and echo 'Hello from Ubuntu!' after installing.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```