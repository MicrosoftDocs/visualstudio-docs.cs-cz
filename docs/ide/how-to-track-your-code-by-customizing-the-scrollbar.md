---
title: Režim mapy posuvníku a režim pruhového okna
ms.date: 09/25/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 997f44fede7b31fe44b1e2ea28186ad52d39f443
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656583"
---
# <a name="how-to-customize-the-scroll-bar"></a>Postupy: přizpůsobení posuvníku

Při práci s dlouhými soubory kódu může být obtížné sledovat, kde je vše v souboru. Můžete přizpůsobit posuvník editoru kódu a získat tak celkový přehled o tom, co se děje ve vašem kódu.

## <a name="annotations"></a>Poznámky

Můžete vybrat, zda posuvník zobrazuje poznámky, jako jsou například změny kódu, zarážky, záložky, chyby a pozice blikajícího kurzoru.

   1. Otevřete stránku možnosti **posuvníku** výběrem možnosti **nástroje**  > **Možnosti**  > **textový editor**  > **všechny jazyky**  > **posuvníky**.

   2. Vyberte možnost **Zobrazit poznámky přes svislý posuvník**a pak vyberte poznámky, které chcete zobrazit. K dispozici jsou tyto poznámky:

      - změny
      - značky
      - chyby
      - pozice blikajícího kurzoru

      > [!TIP]
      > Možnost **Zobrazit značky** obsahuje zarážky a záložky.

Vyzkoušejte si to tak, že otevřete velký soubor kódu a nahradíte nějaký text, který se nachází na několika místech v souboru. Posuvník zobrazuje účinek nahrazení, takže můžete zálohovat změny, pokud jste nahradili něco, co byste neměli mít.

Tady je postup, jak posuvník vypadá po hledání řetězce. Všimněte si, že se všechny výskyty řetězce zobrazují na posuvníku.

![Posuvník sady Visual Studio po hledání řetězce](../ide/media/enhancedscrollbarsearch.png)

Zde je posuvník po nahrazení všech instancí řetězce. Červené značky na posuvníku ukazují, kde nahrazování textu zavedlo chyby.

![Posuvník sady Visual Studio po nahrazení řetězce chybami](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Režimy zobrazení

Posuvník má dva režimy: režim pruhů a režim mapování.

### <a name="bar-mode"></a>Režim pruhů

*Režim pruhů* zobrazuje indikátory poznámek na posuvníku. Kliknutím na posuvník posunete stránku nahoru nebo dolů, ale nepřejdete do tohoto umístění v souboru.

### <a name="map-mode"></a>Režim mapování

Když v *režimu mapování*kliknete na umístění na posuvníku, přesune se kurzor na toto místo v souboru místo pouhého posouvání nahoru nebo dolů stránky. Řádky kódu jsou v miniaturním zobrazení zobrazeny na posuvníku. Můžete zvolit, jak velký má sloupec mapy výběrem hodnoty v **přehledu zdroje**. Chcete-li povolit větší náhled kódu při přesunutí ukazatele na mapu, vyberte možnost **Zobrazit náhled tlačítka** . Sbalené oblasti jsou vybarvené jinak a při jejich dvojitém kliknutí se rozbalí.

> [!TIP]
> Zobrazení miniaturního kódu můžete zapnout v režimu mapování nastavením **zdrojového přehledu** na **vypnuto**. Pokud je vybrána možnost **Zobrazit náhled náhledu** , stále se zobrazuje náhled kódu v tomto umístění, když na posuvníku najedete ukazatel myši, a když na něj kliknete, přesune se kurzor na toto umístění v souboru.

Následující obrázek znázorňuje příklad hledání v případě, že je režim mapování zapnutý a šířka je nastavená na **hodnotu Střední**:

![Posuvník sady Visual Studio v režimu mapování](../ide/media/enhancedscrollbar.png)

Následující obrázek ukazuje možnost **Zobrazit náhled popisku** :

![Posuvník sady Visual Studio s popisem tlačítka](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)