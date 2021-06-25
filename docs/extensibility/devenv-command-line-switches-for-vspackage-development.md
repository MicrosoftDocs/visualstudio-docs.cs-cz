---
title: Přepínače devenv Command-Line pro vývojové prostředí VSPackage | Microsoft Docs
description: Zjistěte, jak mohou vývojáři automatizovat úlohy z příkazového řádku při spouštění devenv.exe, souboru, který spouští integrované vývojové Visual Studio ide.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ea08b4714a79e09fce5933b67997a032532481f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904240"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Přepínače příkazového řádku Devenv pro vývoj VSPackage

Visual Studio umožňuje vývojářům automatizovat úlohy z příkazového řádku při spuštění souboru , který spouští `devenv.exe` Visual Studio IDE.

 Mezi úlohy patří:

- Nasazení aplikací v předem navržených konfiguracích mimo integrované vývojové prostředí (IDE)

- Automatické sestavování projektů s využitím přednastavených nastavení sestavení nebo konfigurací ladění

- Načtení integrovaného vývojového prostředí (IDE) v konkrétních konfiguracích, a to vše mimo integrované vývojové prostředí (IDE). Integrované vývojové prostředí můžete také přizpůsobit při spuštění.

## <a name="guidelines-for-switches"></a>Pokyny pro přepínače

Visual Studio dokumentace popisuje přepínače příkazového řádku `devenv` na úrovni uživatele. Další informace najdete v tématu Přepínače příkazového řádku [Devenv.](../ide/reference/devenv-command-line-switches.md) Nástroj také podporuje další přepínače příkazového řádku, které jsou užitečné při vývoji, nasazení a `devenv` ladění balíčku VSPackage.

| Přepínač příkazového řádku | Description |
|---------------------| - |
| `/ResetSkipPkgs` | Vymaže všechny možnosti přeskočení načítání přidané uživateli, kteří se chtějí vyhnout načítání problematických balíčky VSPackage, a pak Visual Studio. Přítomnost značky SkipLoading zakáže načítání balíčku VSPackage. Vymazáním značky se znovu povolí načítání balíčku VSPackage.<br /><br /> Tento přepínač nemá žádné argumenty. |
| `/RootSuffix` | Spustí Visual Studio pomocí alternativního umístění. Následující příkaz spustí zástupce vytvořený instalačním programem Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> V tomto případě `exp` identifikuje umístění s konkrétní příponou (například místo `10.0Exp` `10.0` ). Experimentální instance umožňuje ladit balíček VSPackage odděleně od instance Visual Studio, kterou používáte k psaní kódu.<br /><br /> Tento přepínač může převzít libovolný řetězec identifikující umístění, které jste vytvořili pomocí VSRegEx.exe. Další informace najdete v tématu [Experimentální instance](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Spustí Visual Studio v bezpečném režimu a načítá pouze výchozí integrované vývojové prostředí (IDE) a služby. Přepínač zabrání načítání všech balíčku VSPackage třetích stran při spuštění Visual Studio, aby `/SafeMode` se zajistilo stabilní spuštění.<br /><br /> Tento přepínač nemá žádné argumenty. |
| `/Setup` | Vynutí Visual Studio sloučit metadata prostředků popisující nabídky, panely nástrojů a skupiny příkazů ze všech dostupných balíčku VSPackage. Tento příkaz můžete spustit pouze jako správce. <br /><br /> Tento přepínač nemá žádné argumenty. Příkaz `devenv /Setup` je obvykle uveden jako poslední krok procesu instalace. Použití přepínače `/Setup` nespustí integrované vývojové prostředí (IDE).|
| `/Splash` | Jako obvykle Visual Studio úvodní obrazovku a pak před zobrazením hlavního integrovaného vývojového prostředí (IDE) zobrazí okno se zprávou. Okno se zprávou umožňuje prostudovat úvodní obrazovku (například zkontrolovat ikonu produktu VSPackage).<br /><br /> Tento přepínač nemá žádné argumenty. |

## <a name="see-also"></a>Viz také

- [Přidání přepínačů příkazového řádku](../extensibility/adding-command-line-switches.md)
- [Devenv – přepínače příkazového řádku](../ide/reference/devenv-command-line-switches.md)
