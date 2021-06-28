---
title: Vyhledání Visual Studio | Microsoft Docs
description: Můžete nainstalovat více instancí stejné verze Visual Studio. Zjistěte, jak pomocí rozhraní API pro dotazy modelu COM najít instanci, kterou chcete.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: cd0fcd294983d6a6567676f06703b4bd1dd376c4
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990503"
---
# <a name="locate-visual-studio"></a>Vyhledání sady Visual Studio

Od Visual Studio 2017 můžete nainstalovat několik instancí stejné verze nebo dokonce edice. To je užitečné, když chcete zobrazit náhled nových funkcí na primárním vývojovém počítači při zachování předchozí instalace. Kvůli těmto změnám neexistuje žádná jediná proměnná prostředí ani hodnota registru, které byste mohli použít k vyhledání instance. Místo toho můžete pomocí rozhraní API pro [dotazy modelu COM](/dotnet/api/microsoft.visualstudio.setup.configuration) vyhledat instance na základě kritérií relevantních pro vaše rozšíření.

Jedná se o rychlé rozhraní API jen pro čtení s balíčky NuGet dostupnými pro nativní a spravovaný kód.

| Kód | Balíček |
| ---- | --- |
| Nativní | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Spravované | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Můžete vyhledat jednu instanci s danou cestou nebo aktuálním procesem nebo vytvořit výčet všech instancí. Kompletní [příklady vyhledání těchto](https://github.com/Microsoft/vs-setup-samples) Visual Studio.

## <a name="tools"></a>nástroje

K vyhledání Visual Studio a dalších nástrojů v prostředích sestavení, skriptech PowerShellu, instalačních programech a dalších scénářích existuje řada open source nástrojů, které můžete použít přímo nebo redistribuovat společně s vlastními skripty.

| Projekt | Popis |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Nativní spustitelný soubor s jedním souborem, který vyhledá instance splňující kritéria, jako je vydání nebo předběžná verze, jaký produkt je nainstalovaný a které úlohy jsou nainstalované. Podporuje také hledání Visual Studio 2010 a novějších verzí, ale pro verzi 2017 a novější Visual Studio méně informací. Příklady najdete [na wikiwebu.](https://github.com/Microsoft/vswhere/wiki) |
| [Rutiny VSSetup](https://github.com/Microsoft/vssetup.powershell) | Rutiny PowerShellu podporovaly 2.0 a novější, které vracejí bohaté informace jako objekty, které můžete použít k vyhledání instancí na základě stejných kritérií jako _vswhere_ a zjišťování dalších vlastností o instancích. Příklady najdete [na wikiwebu.](https://github.com/Microsoft/vssetup.powershell/wiki) |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Automaticky vyhledá _VSIXInstaller_ a předá příkazový řádek k instalaci souboru **.vsix.* Tato funkce může být užitečná v instalačních programech, které nemají přímou podporu rozhraní API pro dotazy. Příklady najdete [na wikiwebu.](https://github.com/Microsoft/vsixbootstrapper/wiki) |

## <a name="see-also"></a>Viz také

* [Změny nastavení Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Spuštění sady Visual Studio pomocí DTE](launch-visual-studio-dte.md)
