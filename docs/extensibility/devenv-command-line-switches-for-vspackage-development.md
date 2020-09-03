---
title: Přepínače příkazového řádku nástroje devenv pro vývoj VSPackage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712197"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Přepínače příkazového řádku nástroje devenv pro vývoj pro VSPackage

Visual Studio umožňuje vývojářům automatizovat úlohy z příkazového řádku při spuštění `devenv.exe` , soubor, který spouští integrované vývojové prostředí (IDE) sady Visual Studio.

 Mezi úlohy patří:

- Nasazení aplikací v předem navržených konfiguracích z vnějšku rozhraní IDE.

- Automatické vytváření projektů pomocí přednastavených nastavení sestavení nebo konfigurací ladění.

- Načítání integrovaného vývojového prostředí (IDE) v konkrétních konfiguracích, od vně rozhraní IDE. Integrované vývojové prostředí můžete také přizpůsobit při spuštění.

## <a name="guidelines-for-switches"></a>Pokyny pro přepínače

Dokumentace k sadě Visual Studio popisuje `devenv` přepínače příkazového řádku na úrovni uživatele. Další informace najdete v tématu [přepínače příkazového řádku nástroje devenv](../ide/reference/devenv-command-line-switches.md). `devenv`Nástroj podporuje také další přepínače příkazového řádku, které jsou užitečné pro vývoj, nasazení a ladění pomocí sady VSPackage.

| Přepínač příkazového řádku | Popis |
|---------------------| - |
| `/ResetSkipPkgs` | Zruší všechny možnosti pro přeskočení načítání, které byly přidány uživateli, kteří se chtějí vyhnout načítání problematických VSPackage, a pak spustí aplikaci Visual Studio. Přítomnost značky SkipLoading zakáže načítání VSPackage. Vymazání značky znovu povolí načítání VSPackage.<br /><br /> Tento přepínač nepřijímá žádné argumenty. |
| `/RootSuffix` | Spustí aplikaci Visual Studio pomocí alternativního umístění. Následující příkaz se spustí pomocí zástupce vytvořeného instalačním programem sady Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> V takovém případě `exp` identifikuje umístění s konkrétní příponou (například `10.0Exp` místo `10.0` ). Experimentální instance umožňuje ladit VSPackage odděleně od instance aplikace Visual Studio, kterou používáte k psaní kódu.<br /><br /> Tento přepínač může přijmout libovolný řetězec, který určuje umístění, které jste vytvořili pomocí VSRegEx.exe. Další informace najdete v [experimentální instanci](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Spustí aplikaci Visual Studio v bezpečném režimu a načítají pouze výchozí integrované vývojové prostředí (IDE) a služby. `/SafeMode`Přepínač brání načtení všech rozhraní VSPackage třetí strany z načítání při spuštění sady Visual Studio, což zajišťuje stabilní provádění.<br /><br /> Tento přepínač nepřijímá žádné argumenty. |
| `/Setup` | Přinutí aplikaci Visual Studio sloučit metadata prostředků, která popisují nabídky, panely nástrojů a skupiny příkazů ze všech dostupných VSPackage. Tento příkaz můžete spustit jenom jako správce. <br /><br /> Tento přepínač nepřijímá žádné argumenty. `devenv /Setup`Příkaz se obvykle předává jako poslední krok instalačního procesu. Použití `/Setup` přepínače nespustí rozhraní IDE.|
| `/Splash` | Zobrazuje úvodní obrazovku sady Visual Studio jako obvykle a pak před zobrazením hlavního integrovaného vývojového prostředí (IDE) zobrazuje okno se zprávou. Okno se zprávou vám umožní prostudovat úvodní obrazovku (například pro kontrolu ikony produktu VSPackage).<br /><br /> Tento přepínač nepřijímá žádné argumenty. |

## <a name="see-also"></a>Viz také

- [Přidat přepínače příkazového řádku](../extensibility/adding-command-line-switches.md)
- [Devenv – přepínače příkazového řádku](../ide/reference/devenv-command-line-switches.md)
