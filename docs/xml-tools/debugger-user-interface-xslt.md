---
title: Okna ladicího programu XSLT
description: Přečtěte si o uživatelském rozhraní ladicího programu XSLT, které řídí chování ladění specifické pro XSLT, včetně místních hodnot, výstupů, zarážek, zásobníku volání a oken kukátka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e5d113718c2ecc73ad942dd58ddf92216fe6c83
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875117"
---
# <a name="debugger-user-interface-xslt"></a>Uživatelské rozhraní ladicího programu (XSLT)

Tento článek popisuje okna ladicího programu a dialogová okna. Popisuje pouze ty součásti uživatelského rozhraní, které mají chování ladění specifické pro jazyk XSLT.

Další informace naleznete v tématu [ladění odkazu uživatelského rozhraní](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Místní hodnoty – okno

V okně místní hodnoty se zobrazí informace o všech proměnných definovaných v šabloně stylů. Okno místní hodnoty obsahuje tři sloupce s informacemi:

**Název**

Tento sloupec obsahuje názvy všech místních proměnných v aktuálním oboru. Sady uzlů mají ovládací prvek stromu, pomocí kterého můžete přejít k podrobnostem a zobrazit jeho podsložky.

**Hodnota**

V tomto sloupci se zobrazuje hodnota obsažená v jednotlivých proměnných. V uzlech pro zpracování, instrukci, textu a CData se zobrazuje textová hodnota uzlu. Uzly oboru názvů zobrazují identifikátor URI oboru názvů.

**Typ**

Tento sloupec Určuje datový typ každé proměnné uvedené ve sloupci **název** .

V okně místní hodnoty jsou také zobrazeny předdefinované kontextové proměnné, které sledují kontext transformace XSLT. Následující tabulka popisuje předdefinované kontextové proměnné používané ladicím programem XSLT.

|Název|Description|
|-|-----------------|
|`last()`|Velikost kontextu.|
|`position()`|Pozice nebo číslo indexu kontextu uzlu vzhledem k velikosti kontextu.|
|`self::node()`|Hodnota uzlu kontextu.|

## <a name="output-window"></a>Výstup – okno

V okně výstup se zobrazí všechny chybové zprávy nebo výjimky zabezpečení, ke kterým došlo během ladění. Také ukazuje výstup ladicího programu.

## <a name="task-list"></a>Seznam úkolů

**Seznam úkolů** uvádí všechny chyby kompilace v šabloně stylů. Dvojím kliknutím na chybu se převezme kurzor na řádek s chybou.

**Seznam úkolů** obsahuje všechny chyby, ke kterým dochází ve blocích skriptu v souboru XSLT.

> [!NOTE]
> Ladicí program XSLT neobsahuje žádná upozornění, takže se nikdy nezobrazí v **seznam úkolů**.

## <a name="breakpoints-window"></a>Zarážky – okno

Okno zarážky zobrazuje všechny zarážky nastavené v aktuálním projektu. Pokud je při zobrazení okna přidána zarážka, okno se automaticky aktualizuje, aby se zobrazila Nová zarážka.

Okno zarážky by se mělo chovat stejným způsobem jako ostatní ladicí programy sady Visual Studio.

## <a name="watch-window"></a>Kukátko – okno

Okno Kukátko slouží k vyhodnocení proměnných. Můžete také změnit hodnoty proměnných.

Proměnné zobrazené v okno Kukátko jsou pro aktuální kontext (nejvyšší položka v zásobníku volání). Změníte-li kontext, okno kukátko aktualizuje a zobrazí sady proměnných pro daný kontext.

## <a name="call-stack-window"></a>okno Zásobník volání

Okno **zásobník volání** slouží k zobrazení názvů funkcí v zásobníku volání, typech parametrů a hodnotách parametrů. Informace zásobníku volání se zobrazují jenom v případě, že program, který se právě ladí, je ve stavu přerušení.

Zásobník volání představuje různé kontexty, které prochází prováděním XSLT. Například pokud je volání ze šablony "a" na šablonu "b", šablona "a" a šablona "b" se zobrazí v okně **zásobník volání** s aktuálním kontextem v horní části seznamu. Uživatel může zobrazit aktuálně prováděný dotaz.

Pokud šablony nemají název v souboru XSLT, budou použity názvy generované procesorem XSLT.

Kliknutím na jinou položku, než je v horní části seznamu, se zobrazí prohlížeč, ve kterém se větev spuštění XSLT stala pomocí standardního zeleného zvýraznění a zelených šipek.

## <a name="quickwatch-dialog-box"></a>QuickWatch – dialogové okno

Dialogové okno **QuickWatch** slouží k vyhodnocení výrazů XPath 1,0. Kontextový uzel ( `self::node()` uzel z okna místní hodnoty) poskytuje kontext pro spuštění výrazu XPath. Výsledek spuštění výrazu XPath je zobrazen v okno Kukátko.

Následující seznam popisuje omezení pro vyhodnocení výrazu XPath:

- Jsou povoleny pouze předdefinované funkce XPath.

- Integrované funkce XSLT, jako `document()` jsou a, `key()` nejsou povoleny.

- Uživatelsky definované funkce nejsou povoleny.

Další informace naleznete v tématu [How to: Evaluate a XPath Expression](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>okno Zpětný překlad

Okno zpětný překlad zobrazuje kód sestavení generovaný kompilátorem XSLT. Toto okno lze použít stejným způsobem jako všechny ostatní okna aplikace sady Visual Studio pro zpětný překlad.

Další informace najdete v tématu [Postup: použití okna](../debugger/how-to-use-the-disassembly-window.md)zpětného překladu.

## <a name="see-also"></a>Viz také

- [Ladění XSLT](../xml-tools/debugging-xslt.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Kontrola proměnných v oknech automatické hodnoty a místní hodnoty v aplikaci Visual Studio](../debugger/autos-and-locals-windows.md)
