---
title: 'Postupy: sledování kódu přizpůsobením posuvníku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670637"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Postupy: sledování kódu přizpůsobením posuvníku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když pracujete s dlouhými soubory kódu, může být obtížné udržet si vše. Můžete přizpůsobit posuvník okna kódu, abyste vám poskytli pohled na oči, co se děje ve vašem kódu.

### <a name="to-show-annotations-on-the-scroll-bar"></a>Zobrazení poznámek na posuvníku

1. Můžete nastavit posuvník pro zobrazení změn kódu, zarážek, chyb a záložek.

     Otevřete stránku možností **posuvníku** (**nástroje, editor textu možnosti. Všechny jazyky** nebo konkrétní jazyk nebo zadejte **posuvník** v okně snadné spuštění).

2. Vyberte možnost **Zobrazit poznámky přes svislý posuvník**a pak vyberte poznámky, které chcete zobrazit. (Možnost **značky** obsahuje zarážky a záložky.)

3. Nyní to vyzkoušejte. Otevřete velký soubor kódu a nahraďte něco, co se nachází na několika místech v souboru. Posuvník zobrazuje účinek nahrazení, takže můžete zálohovat změny, pokud jste nahradili něco, co byste neměli mít.

     Tady je postup, jak posuvník vypadá po hledání řetězce. Všimněte si, že se zobrazí všechny výskyty řetězce.

     ![Posuvník po hledání řetězce](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

     Zde je posuvník po nahrazení všech instancí řetězce. Vidíte, že operace způsobila nějaké problémy.

     ![Posuvník po nahrazení řetězce chybami](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Nastavení režimu zobrazení posuvníku

1. Posuvník má dva režimy, pruhový režim (výchozí nastavení) a režim mapování. Režim pruhů pouze zobrazuje indikátory poznámek na posuvníku. V režimu mapování jsou řádky kódu znázorněny na posuvníku. Můžete zvolit, jak velký je a zda se při přesunutí ukazatele myši zobrazí podkladový kód. Po kliknutí na umístění na posuvníku se kurzor přesune do tohoto umístění v kódu. Sbalené oblasti jsou vybarvené jinak. po dvojitém kliknutí na ně budou rozbaleny.

     Na stránce možnosti **posuvníku** vyberte buď **režim čáry pro svislý posuvník** , nebo **použijte režim mapování pro svislý posuvník**. Šířku můžete zvolit v rozevíracím seznamu **Přehled zdroje** .

     Tady je postup, jak vypadá příklad hledání, když je režim mapování zapnutý a šířka je nastavená na střední:

     ![Posuvník v režimu mapy](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. V režimu mapování, chcete-li povolit náhledy kódu při přesunutí kurzoru nahoru a dolů posuvníku, vyberte možnost **Zobrazit náhled tlačítka** . Jak vypadá:

     ![Posuvník s popisem tlačítka](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

     Pokud chcete zachovat chování posouvání režimu mapy a popis tlačítka Náhled, ale nechcete zobrazit přehled zdrojového kódu, můžete nastavit **Přehled zdroje** na **vypnuto**.
