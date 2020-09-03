---
title: Snadné spuštění, prostředí, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: abd8f8e9ee35c234a79af74199b11d5491e6fbee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851639"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Dialogové okno Snadné spuštění, Prostředí, Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Rychlé spuštění** můžete použít k rychlému vyhledávání a provádění akcí pro prostředky IDE, jako jsou například možnosti, šablony nebo nabídky. Nelze použít funkci **snadného spuštění** k hledání kódu a symbolů. Vyhledávací pole **Snadné spuštění** se nachází v pravém horním rohu řádku nabídek a je přístupné výběrem kláves CTRL + Q. Jednoduše do pole zadejte hledaný řetězec. Pokud chcete hledat řetězce, které obsahují @, použijte @ @.

 Při instalaci sady Visual Studio je **Rychlé spuštění** povoleno ve výchozím nastavení. Na panelu nabídek můžete zobrazit nebo skrýt **panel Snadné spuštění** výběrem možnosti **nástroje**, **Možnosti**. Rozbalte uzel **prostředí** a pak zvolte možnost **Snadné spuštění**. Zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit rychlé spuštění** . Na této stránce můžete také povolit nebo zakázat kategorie hledání.

## <a name="category-list"></a>Seznam kategorií
 Výsledky hledání snadného spuštění se zobrazí ve čtyřech kategoriích: **naposledy použité**, **nabídky**, **Možnosti**a **otevřené dokumenty**spolu s počtem položek v kategorii. Chcete-li procházet výsledky hledání podle kategorie, klikněte na klávesovou zkratku CTRL + Q pro zobrazení všech výsledků z další kategorie. Po zobrazení poslední kategorie vám CTRL + Q zobrazí několik výsledků z každé kategorie. Pomocí kombinace kláves CTRL + SHIFT + Q můžete procházet kategorie v opačném pořadí. Chcete-li zobrazit všechny výsledky hledání v kategorii, vyberte název kategorie.

 Pomocí následujících zástupců můžete omezit hledání na konkrétní kategorie.

|Kategorie|Zástupce|Popis zástupce|
|--------------|--------------|--------------------------|
|Naposledy použité|@mru<br /><br /> Například `@mru font`.|Zobrazí až pět položek, které jste **naposledy použili**.|
|Nabídky|@menu<br /><br /> Například `@menu font`.|Omezí hledání na položky nabídky.|
|Možnosti|@opt<br /><br /> Například `@opt font`.|Omezí hledání na nastavení v dialogovém okně **Možnosti** .|
|Dokumenty|@doc<br /><br /> Například `@doc font`.|Omezí hledání na názvy souborů a cesty k otevřeným dokumentům pro kritéria hledání, ale nehledá text v samotných souborech.|

> [!NOTE]
> Klávesové zkratky můžete změnit na stránce **Obecné**, **klávesnice** v dialogovém okně **Možnosti** .

## <a name="show-previous-results"></a>Zobrazit předchozí výsledky
 Ve výchozím nastavení se hledaný termín, který zadáte, netrval mezi vyhledávacími relacemi. Hledaný řetězec je při hledání termínu vymazán, přesuňte kurzor mimo oblast snadné **spuštění** a pak se vraťte zpět. Chcete-li zachovat výsledky hledání, otevřete dialogové okno **Možnosti** , zvolte možnost **Snadné spuštění**a pak vyberte možnost **Zobrazit výsledky hledání z předchozího hledání, když je aktivováno snadné spuštění.** . Při příštím hledání ponechte oblast snadné spuštění a vraťte se zpátky. rychlé spuštění zachová hledaný termín a také zobrazí výsledky hledání.

 Nejaktuálnější tipy a triky pro použití **panelu snadného spuštění**najdete v [blogu sady Visual Studio](https://blogs.msdn.com/b/visualstudio/).

## <a name="see-also"></a>Viz také
 Obecné možnosti prostředí pro [prvky uživatelského rozhraní (Visual Studio)](../../ide/reference/general-user-interface-elements-visual-studio.md) – [dialogové okno](../../ide/reference/environment-options-dialog-box.md)
