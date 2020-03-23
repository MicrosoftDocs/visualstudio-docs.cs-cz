---
title: Režim mapy posuvníku a režim pruhu
ms.date: 03/20/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c66cda1b90d11a44f744faf0012a3e41212d33dd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988565"
---
# <a name="how-to-customize-the-scroll-bar"></a>Postup: Přizpůsobení posuvníku

Při práci s dlouhými soubory kódu může být obtížné sledovat, kde je vše v souboru. Můžete přizpůsobit posuvník editoru kódu, abyste poskytli celkový obrázek o tom, co se děje ve vašem kódu.

## <a name="annotations"></a>Poznámky

Můžete vybrat, zda posuvník zobrazuje poznámky, jako jsou změny kódu, zarážky, záložky, chyby a umístění stříšky.

   1. Otevřete stránku **Možností posuvníků** tak, že zvolíte Textové**editory** > **textových** >  **editorů** > **všechny jazyky** > **.**

   2. Vyberte **Zobrazit poznámky nad svislým posuvníkem**a pak vyberte poznámky, které chcete zobrazit. Dostupné poznámky jsou:

      - změny
      - značky
      - chyby
      - poloha stříšky

      > [!TIP]
      > Možnost **Zobrazit značky** obsahuje zarážky a záložky.

Vyzkoušejte to otevřením velkého souboru kódu a nahrazením některého textu, který se vyskytuje na několika místech v souboru. Posuvník zobrazuje efekt nahrazení, takže změny můžete vyvrátit, pokud jste nahradili něco, co byste neměli mít.

Posuvník vypadá po hledání řetězce takto. Všimněte si, že všechny instance řetězce se zobrazí v posuvníku.

![Posuvník visual studia po vyhledání řetězce](../ide/media/enhancedscrollbarsearch.png)

Zde je posuvník po nahrazení všech instancí řetězce. Červené značky na posuvníku ukazují, kde nahrazení textu vyvolalo chyby.

![Posuvník visual studio po nahrazení řetězce chybami](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Režimy zobrazení

Posuvník má dva režimy: režim pruhu a režim mapy.

### <a name="bar-mode"></a>Barový režim

*Režim pruhů* zobrazuje na posuvníku indikátory poznámky. Kliknutím na posuvník posunete stránku nahoru nebo dolů, ale nepřeskočíte do tohoto umístění v souboru.

### <a name="map-mode"></a>Režim mapy

*Režim mapy* zobrazuje na posuvníku řádky kódu v miniatuře. Výběrem hodnoty v **přehledu zdroje**můžete zvolit, jak široký je sloupec mapy . Chcete-li povolit větší náhled kódu při umístění ukazatele na mapě, vyberte volbu **Zobrazit náhled v popisku.** Sbalené oblasti jsou popodvojené oblasti různě stínovány a popodvojené.

> [!TIP]
> Zobrazení miniaturního kódu můžete vypnout v režimu mapy nastavením **přehledu zdroje** na **Vypnuto**. Pokud je **vybraná možnost Zobrazit popisek náhledu,** zobrazí se při umístění náhled kódu, když na pojedete ukazatelem myši na posuvníku, a kurzor na toto místo v souboru po klepnutí stále přejde do tohoto umístění.

Následující obrázek znázorňuje příklad hledání, když je zapnutý režim mapy a šířka je **nastavena**na Střední :

![Posuvník Visual Studio v režimu mapy](../ide/media/enhancedscrollbar.png)

Následující obrázek znázorňuje volbu **Zobrazit náhled v popisku:**

![Posuvník visual studia s popiskem](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Chcete-li změnit barvy, které se zobrazují v režimu mapy, zvolte**Možnosti** >  **nástrojů** > **Písma** > **a barvy**prostředí . Dále v **části Zobrazit položky**zvolte některou z položek, které předchází "Přehled", proveďte požadované změny barev a pak zvolte **OK**.

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
