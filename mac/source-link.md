---
title: Ladění do balíčků NuGet pomocí odkazu na zdroj
description: Tento článek popisuje funkci odkaz na zdroj v Visual Studio pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583915"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Ladění do balíčků NuGet pomocí odkazu na zdroj

Technologie zdrojového propojení umožňuje ladění zdrojového kódu ze sestavení .NET ze sady NuGet, která je dodávána. Soubory PDB s odkazy na zdrojové soubory. Zdrojový odkaz se spustí, když vývojáři vytvoří svůj balíček NuGet a vloží metadata správy zdrojového kódu do sestavení a balíčku. Když je v Visual Studio pro Mac povoleno zdrojové propojení, IDE detekuje, jestli jsou zdrojové soubory k dispozici pro nainstalované balíčky. Visual Studio pro Mac se pak nabídne stažení, což vám umožní krokovat kód balíčku. Odkaz na zdroj funguje také s kódem knihovny mono základní třídy pro projekty Xamarin, což vám umožňuje Krokovat s .NET Framework kódu také. Odkaz na zdroj poskytuje metadata správy zdrojového kódu pro vytvoření skvělého prostředí ladění.

> [!NOTE]
> Visual Studio pro Mac aktuálně nepodporuje servery symbolů. Z tohoto důvodu není podporováno zdrojové propojení s metadaty hostovanými na serverech symbolů.

## <a name="enable-source-link"></a>Povolit zdrojový odkaz

Pokud chcete povolit odkaz na zdroj v Visual Studio pro Mac, přejděte do sady **Visual Studio > předvolby... > projekty > ladicí program** a ujistěte se, že je zaškrtnuté políčko **Krokovat s externím kódem** .

![Snímek obrazovky s dialogovým oknem předvolby zobrazující krok do externího kódu](media/source-link1.png)

Můžete změnit nastavení **Stažení externího kódu** tak, aby vyhovovalo vašim potřebám:
* Dotaz: Visual Studio pro Mac vás vyzve ke stažení externího kódu
* Always: Visual Studio pro Mac stáhne externí kód automaticky
* Nikdy: Visual Studio pro Mac nestáhne související externí kód

Ve výchozím nastavení je vybrána možnost **dotaz** . Při nalezení externího kódu pro balíček NuGet se zobrazí následující výzva:

![Snímek obrazovky s výzvou, která se zobrazí, když se pro balíček NuGet najde externí kód](media/source-link2.png)


## <a name="see-also"></a>Viz také

- [Úložiště GitHub na zdrojovém odkazu](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Dokumentace rozhraní .NET](/dotnet/standard/library-guidance/sourcelink) na zdrojovém odkazu a další informace o tom, jak přidat podporu zdrojového odkazu do balíčků