---
title: Ladění do balíčků NuGet se zdrojovým odkazem
description: Tento článek popisuje funkci Zdrojový odkaz ve Visual Studiu pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451487"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Ladění do balíčků NuGet se zdrojovým odkazem

Technologie Zdrojového propojení umožňuje ladění zdrojového kódu sestavení .NET z této lodi NuGet . PdB s odkazy na zdrojové soubory. Zdrojový odkaz se spustí, když vývojáři vytvořit svůj balíček NuGet a vložit metadata správy zdrojového kódu uvnitř sestavení a balíček. Pokud je v sadě Visual Studio for Mac povoleno zdrojové propojení, ide zjistí, jestli jsou pro nainstalované balíčky k dispozici zdrojové soubory. Visual Studio pro Mac pak nabídne jejich stažení, což vám umožní projít kód balíčku. Zdrojový odkaz také pracuje s mono základní třídy knihovny kód pro projekty Xamarin, což vám umožní krok do kódu rozhraní .NET Framework také. Zdrojový odkaz poskytuje metadata správy zdrojového kódu k vytvoření skvělého prostředí ladění.

> [!NOTE]
> Visual Studio pro Mac momentálně nepodporuje symbolové servery. Z tohoto důvodu není podporováno zdrojové propojení s metadaty hostovanými na symbolových serverech.

## <a name="enable-source-link"></a>Povolit zdrojový odkaz

Chcete-li povolit zdrojový odkaz v sadě Visual Studio for Mac, přejděte do **visual studia > předvolby... > projekty > debugger** a ujistěte se, že je zaškrtnuté políčko **Přejít na externí kód.**

![Snímek obrazovky s dialogovým oknem předvoleb se zaškrtávacím políčkem Krok do externího kódu](media/source-link1.png)

Nastavení v části **Stáhnout externí kód** můžete změnit tak, aby vyhovovalo vašim preferencím:
* Zeptejte se: Visual Studio pro Mac vás vyzve ke stažení externího kódu
* Vždy: Visual Studio pro Mac automaticky stáhne externí kód
* Nikdy: Visual Studio pro Mac nestáhne související externí kód.

Ve výchozím nastavení je **vybrána** možnost Zeptat se. Při nalezení externího kódu pro balíček NuGet se zobrazí následující výzva:

![Snímek obrazovky s výzvou, která se zobrazí při nalezení externího kódu pro balíček NuGet](media/source-link2.png)


## <a name="see-also"></a>Viz také

- [Úložiště GitHub zdrojového propojení](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Dokumentace rozhraní .NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) na zdrojovém odkazu a další informace o přidání podpory zdrojového odkazu do balíčků
