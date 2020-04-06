---
title: Přepínače příkazového řádku Devenv pro vývoj balíčku VSPackage | Dokumenty společnosti Microsoft
ms.date: 12/10/2018
ms.topic: conceptual
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712197"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Přepínače příkazového řádku Devenv pro vývoj vbalíčku VSPackage

Visual Studio umožňuje vývojářům automatizovat úlohy `devenv.exe`z příkazového řádku při provádění souboru, který spustí ide sady Visual Studio.

 Mezi úkoly patří:

- Nasazení aplikací v předem navržených konfiguracích mimo ide.

- Automaticky vytvářet projekty pomocí přednastavených nastavení sestavení nebo ladění konfigurací.

- Načítání ide v konkrétních konfiguracích, všechny z mimo ide. Můžete také přizpůsobit ide při spuštění.

## <a name="guidelines-for-switches"></a>Pokyny pro přepínače

Dokumentace sady Visual Studio popisuje `devenv` přepínače příkazového řádku na úrovni uživatele. Další informace naleznete v tématu [Přepínače příkazového řádku Devenv](../ide/reference/devenv-command-line-switches.md). Nástroj `devenv` také podporuje další přepínače příkazového řádku, které jsou užitečné při vývoji, nasazení a ladění balíčku VSPackage.

| Přepínač příkazového řádku | Popis |
|---------------------| - |
| `/ResetSkipPkgs` | Vymaže všechny možnosti přeskočit načítání, které byly přidány uživateli, kteří se chtějí vyhnout načítání problematické VSPackages a spustí Visual Studio. Přítomnost SkipLoading značky zakáže načítání VSPackage. Vymazáním značky znovu povolí načítání VSPackage.<br /><br /> Tento přepínač nepřijímá žádné argumenty. |
| `/RootSuffix` | Spustí visual studio pomocí alternativního umístění. Následující příkaz je spuštěn zástupcem vytvořeným instalačním programem sady Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> V tomto `exp` případě identifikuje umístění s určitou příponou `10.0Exp` (například místo `10.0`). Experimentální instance umožňuje ladit VSPackage odděleně od instance Sady Visual Studio, které používáte k zápisu kódu.<br /><br /> Tento přepínač může trvat libovolný řetězec, který identifikuje umístění, které jste vytvořili pomocí VSRegEx.exe. Další informace naleznete [v tématu Experimentální instance](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Spustí visual studio v nouzovém režimu, načítání pouze výchozí ide a služby. Přepínač `/SafeMode` zabrání všechny třetí strany VSPackages z načítání při spuštění sady Visual Studio, zajištění stabilní ho spuštění.<br /><br /> Tento přepínač nepřijímá žádné argumenty. |
| `/Setup` | Vynutí, aby visual studio sloučilo metadata prostředků, které popisují nabídky, panely nástrojů a skupiny příkazů ze všech dostupných balíčků VSPackages. Tento příkaz lze spustit pouze jako správce. <br /><br /> Tento přepínač nepřijímá žádné argumenty. Příkaz `devenv /Setup` je obvykle uveden jako poslední krok procesu instalace. Použití přepínače `/Setup` nespustí ide.|
| `/Splash` | Zobrazí úvodní obrazovku sady Visual Studio jako obvykle a potom zobrazí okno se zprávou před zobrazením hlavního ide. Okno se zprávou umožňuje prostudovat úvodní obrazovku (například zkontrolovat ikonu produktu VSPackage).<br /><br /> Tento přepínač nepřijímá žádné argumenty. |

## <a name="see-also"></a>Viz také

- [Přidání přepínačů příkazového řádku](../extensibility/adding-command-line-switches.md)
- [Devenv – přepínače příkazového řádku](../ide/reference/devenv-command-line-switches.md)
