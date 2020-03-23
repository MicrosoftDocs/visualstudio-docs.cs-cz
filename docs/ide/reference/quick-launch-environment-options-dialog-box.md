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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565666"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Dialogové okno Snadné spuštění, Prostředí, Možnosti

**Pomocí funkce Snadné spuštění** můžete rychle vyhledávat a provádět akce pro prostředky IDE, jako jsou možnosti, šablony, nabídky. **Pomocí funkce Snadné spuštění** nelze vyhledávat kódy a symboly. Vyhledávací pole **Snadné spuštění** se nachází v pravém horním rohu panelu nabídek a je přístupné stisknutím **klávesctrl**+**q**. Do pole zadejte hledaný řetězec. Chcete-li vyhledat řetězce obsahující @, použijte @@.

**Snadné spuštění** je ve výchozím nastavení povoleno při instalaci sady Visual Studio. Na řádku nabídek můžete zobrazit nebo skrýt **snadné spuštění** výběrem **možnosti nástroje** > **.** Rozbalte uzel **Prostředí** a pak zvolte **Snadné spuštění**. Zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit snadné spuštění.** Můžete také povolit nebo zakázat kategorie vyhledávání na této stránce.

## <a name="category-list"></a>Seznam kategorií

Výsledky hledání snadného spuštění se zobrazují ve čtyřech kategoriích: **Naposledy použité** **položky**, Nabídky , **Možnosti**a **Otevřené dokumenty**a počet položek v dané kategorii. Chcete-li procházet výsledky hledání podle kategorií, zvolte klávesy **Ctrl**+**Q,** chcete-li zobrazit všechny výsledky z další kategorie. Po zobrazení poslední kategorie vám **kombinace kláves Ctrl**+**Q** zobrazí několik výsledků z každé kategorie. Stisknutím **klávesy Ctrl**+**Shift**+**Q** procházejte kategoriemi v opačném pořadí. Chcete-li zobrazit všechny výsledky hledání v kategorii, zvolte název kategorie.

Pomocí následujících zkratek můžete hledání omezit na určité kategorie.

|Kategorie|Zástupce|Popis zástupce|
|--------------|--------------| - |
|Naposledy použité|@mru<br /><br /> Například `@mru font`.|Zobrazí až pět naposledy **použitých**položek .|
|Nabídky|@menu<br /><br /> Například `@menu project`.|Omezuje hledání na položky nabídky.|
|Možnosti|@opt<br /><br /> Například `@opt font`.|Omezí hledání na nastavení v dialogovém okně **Možnosti.**|
|Dokumenty|@doc<br /><br /> Například `@doc program.cs`.|Omezuje hledání na názvy souborů a cesty otevřených dokumentů pro kritéria hledání, ale neprohledává text uvnitř samotných souborů.|

> [!NOTE]
> Klávesové zkratky na stránce **Obecná** > **klávesnice** můžete změnit v dialogovém okně **Možnosti.**

## <a name="show-previous-results"></a>Zobrazit předchozí výsledky

Ve výchozím nastavení není hledaný termín, který zadáte, mezi relacemi hledání trvalý. Hledaný řetězec je vymazán, pokud hledáte termín, přesuňte kurzor mimo oblast **Snadné spuštění** a pak se vrátíte zpět. Chcete-li zachovat výsledky hledání, přejděte do dialogového okna **Možnosti,** zvolte **Snadné spuštění**a pak při aktivaci funkce Rychlé spuštění vyberte zobrazit výsledky hledání **z předchozího hledání.** . Při příštím vyhledávání, opuštění oblasti Snadné spuštění a návratu si rychlé spuštění zachová naposledy použitý hledaný termín a také vám zobrazí výsledky hledání.
