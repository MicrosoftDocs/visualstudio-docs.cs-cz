---
title: wsl-install
description: devinit Tool WSL – Install.
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
ms.openlocfilehash: 4dff121d7866918d5c30986dc9bd4c3cab039ac5
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672423"
---
# <a name="wsl-install"></a>wsl-install

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

Tento `wsl-install` nástroj slouží k instalaci systému Linux distribuce pro [subsystém Windows pro Linux](/windows/wsl/) (WSL).

> [!IMPORTANT]
> `wsl-install`Nástroj vyžaduje, aby v systému Windows byla povolena možnost WSL 2. Pokud z nějakého důvodu nepovolíte WSL 2, můžete postupovat podle [dokumentace k instalaci WSL](https://docs.microsoft.com/windows/wsl/install-win10). K povolení všech potřebných funkcí Windows můžete použít taky Nástroj pro [Povolení WindowsFeature](tool-windowsfeature-enable.md) .

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                             |
| [**vstup**](#input)                              | řetězec | Yes      | Distribuce, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .     |
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
Níže jsou uvedeny příklady, jak spustit `wsl-install` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-ubuntu-2004"></a>.devinit.js, které budou instalovat Ubuntu 20,04:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command"></a>.devinit.js, který nainstaluje Ubuntu 20,04 a provede příkaz post Create:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command-that-configures-the-packages-listed"></a>.devinit.js, který nainstaluje Ubuntu 20,04, a provede příkaz post Create, který nakonfiguruje balíčky v seznamu:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```
