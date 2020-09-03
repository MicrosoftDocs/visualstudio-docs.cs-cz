---
title: Dialogové okno Snadné spuštění, Prostředí, Možnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 706b54e3ee925b1833f860da2f84c8d28af9617e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565666"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Dialogové okno Snadné spuštění, Prostředí, Možnosti

**Rychlé spuštění** můžete použít k rychlému vyhledávání a provádění akcí pro prostředky IDE, jako jsou například možnosti, šablony nebo nabídky. Nelze použít funkci **snadného spuštění** k hledání kódu a symbolů. Vyhledávací pole **Snadné spuštění** se nachází v pravém horním rohu řádku nabídek a je přístupné stisknutím **kombinace kláves CTRL** + **Q**. Do pole zadejte hledaný řetězec. Pokud chcete hledat řetězce, které obsahují @, použijte @ @.

Při instalaci sady Visual Studio je **Rychlé spuštění** povoleno ve výchozím nastavení. Na panelu nabídek můžete zobrazit nebo skrýt možnosti snadného **spuštění** výběrem **Tools**  >  **možností**nástroje. Rozbalte uzel **prostředí** a pak zvolte možnost **Snadné spuštění**. Zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit rychlé spuštění** . Na této stránce můžete také povolit nebo zakázat kategorie hledání.

## <a name="category-list"></a>Seznam kategorií

Výsledky hledání snadného spuštění se zobrazí ve čtyřech kategoriích: **naposledy použité**, **nabídky**, **Možnosti**a **otevřené dokumenty**spolu s počtem položek v kategorii. Chcete-li procházet výsledky hledání podle kategorie, klikněte na klávesy **CTRL** + **Q** , abyste zobrazili všechny výsledky z další kategorie. Po zobrazení poslední kategorie vám **CTRL** + **Q** zobrazí několik výsledků z každé kategorie. Stisknutím **kombinace kláves CTRL** + **SHIFT** + **Q** procházejte kategorie v opačném pořadí. Chcete-li zobrazit všechny výsledky hledání v kategorii, vyberte název kategorie.

Pomocí následujících zástupců můžete omezit hledání na konkrétní kategorie.

|Kategorie|Zástupce|Popis zástupce|
|--------------|--------------| - |
|Naposledy použité|@mru<br /><br /> Například `@mru font`.|Zobrazí až pět položek, které jste **naposledy použili**.|
|Nabídky|@menu<br /><br /> Například `@menu project`.|Omezí hledání na položky nabídky.|
|Možnosti|@opt<br /><br /> Například `@opt font`.|Omezí hledání na nastavení v dialogovém okně **Možnosti** .|
|Dokumenty|@doc<br /><br /> Například `@doc program.cs`.|Omezí hledání na názvy souborů a cesty k otevřeným dokumentům pro kritéria hledání, ale nehledá text v samotných souborech.|

> [!NOTE]
> Klávesové zkratky můžete změnit na stránce **Obecné**  >  **klávesnice** v dialogovém okně **Možnosti** .

## <a name="show-previous-results"></a>Zobrazit předchozí výsledky

Ve výchozím nastavení se hledaný termín, který zadáte, netrval mezi vyhledávacími relacemi. Hledaný řetězec je při hledání termínu vymazán, přesuňte kurzor mimo oblast snadné **spuštění** a pak se vraťte zpět. Chcete-li zachovat výsledky hledání, otevřete dialogové okno **Možnosti** , zvolte možnost **Snadné spuštění**a pak vyberte možnost **Zobrazit výsledky hledání z předchozího hledání, když je aktivováno snadné spuštění.** . Při příštím hledání ponechte oblast snadné spuštění a vraťte se zpátky. rychlé spuštění zachová hledaný termín a také zobrazí výsledky hledání.
