---
title: Uživatelské rozhraní ladicího programu (XSLT) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d35ec92a76c9ecbf933256229b64ce06a03a4fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670980"
---
# <a name="debugger-user-interface-xslt"></a>Uživatelské rozhraní ladicího programu (XSLT)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje okna ladicího programu a dialogová okna. Popisuje pouze ty součásti uživatelského rozhraní, které mají chování ladění specifické pro jazyk XSLT.

 Další informace naleznete v tématu [ladění odkazu uživatelského rozhraní](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Okno místních hodnot
 V okně místní hodnoty se zobrazí informace o všech proměnných definovaných v šabloně stylů. Okno místní hodnoty obsahuje tři sloupce s informacemi:

 **Název** Tento sloupec obsahuje názvy všech místních proměnných v aktuálním oboru. Sady uzlů mají ovládací prvek stromu, pomocí kterého můžete procházet hierarchii a zobrazit jeho podsložky.

 **Hodnota** V tomto sloupci se zobrazuje hodnota obsažená v jednotlivých proměnných. V uzlech pro zpracování, instrukci, textu a CData se zobrazuje textová hodnota uzlu. Uzly oboru názvů zobrazují identifikátor URI oboru názvů.

 **Typ** Tento sloupec Určuje datový typ každé proměnné uvedené ve sloupci **název** .

 V okně místní hodnoty jsou také zobrazeny předdefinované kontextové proměnné, které sledují kontext transformace XSLT. Následující tabulka popisuje předdefinované kontextové proměnné používané ladicím programem XSLT.

|Název|Popis|
|----------|-----------------|
|`last()`|Velikost kontextu.|
|`position()`|Pozice nebo číslo indexu kontextu uzlu vzhledem k velikosti kontextu.|
|`self::node()`|Hodnota uzlu kontextu.|

 Další informace najdete v tématu [Postupy: Změna kontextu ladicího programu](https://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).

## <a name="output-window"></a>Okno Výstup
 V okně výstup se zobrazí všechny chybové zprávy nebo výjimky zabezpečení, ke kterým došlo během ladění.

 Ladicí program XSLT používá samostatné okno pro zobrazení výstupu ladicího programu. Toto je stejné okno, které slouží k zobrazení výstupu z příkazu **Zobrazit výstup v prvku xsl** .

## <a name="task-list"></a>Seznam úkolů
 Seznam úkolů uvádí všechny chyby kompilace v šabloně stylů. Dvojím kliknutím na chybu se převezme kurzor na řádek s chybou.

 Seznam úkolů obsahuje všechny chyby, ke kterým dochází ve blocích skriptu v souboru XSLT.

> [!NOTE]
> Ladicí program XSLT neobsahuje žádná upozornění, takže se nikdy nezobrazí v Seznam úkolů.

## <a name="breakpoints-window"></a>Okno zarážek
 Okno zarážky zobrazuje všechny zarážky nastavené v aktuálním projektu. Pokud je při zobrazení okna přidána zarážka, okno se automaticky aktualizuje, aby se zobrazila Nová zarážka.

 Okno zarážky by se mělo chovat stejným způsobem jako ostatní ladicí programy sady Visual Studio.

## <a name="command-windowimmediate-window"></a>Příkazové okno/Okamžité okno
 Není implementováno v této verzi ladicího programu XSLT.

## <a name="watch-window"></a>Okno kukátka
 Okno Kukátko slouží k vyhodnocení proměnných. Můžete také změnit hodnoty proměnných.

 Proměnné zobrazené v okno Kukátko jsou pro aktuální kontext (nejvyšší položka v zásobníku volání). Změníte-li kontext, okno kukátko aktualizuje a zobrazí sady proměnných pro daný kontext.

## <a name="call-stack-window"></a>Okno zásobníku volání
 Okno zásobník volání slouží k zobrazení názvů funkcí v zásobníku volání, typech parametrů a hodnotách parametrů. Informace zásobníku volání se zobrazují jenom v případě, že program, který se právě ladí, je ve stavu přerušení.

 Zásobník volání představuje různé kontexty, které prochází prováděním XSLT. Například pokud je volání ze šablony "a" na šablonu "b", šablona "a" a šablona "b" se zobrazí v okně zásobník volání s aktuálním kontextem v horní části seznamu. Uživatel může zobrazit aktuálně prováděný dotaz.

 Pokud šablony nemají název v souboru XSLT, budou použity názvy generované procesorem XSLT.

 Kliknutím na jinou položku, než je v horní části seznamu, se zobrazí prohlížeč, ve kterém se větev spuštění XSLT stala pomocí standardního zeleného zvýraznění a zelených šipek.

## <a name="quickwatch-dialog-box"></a>Dialogové okno QuickWatch
 Dialogové okno **QuickWatch** slouží k vyhodnocení výrazů XPath 1,0. Kontextový uzel ( `self::node()` uzel z okna místní hodnoty) poskytuje kontext pro spuštění výrazu XPath. Výsledek spuštění výrazu XPath je zobrazen v okno Kukátko.

 Následující seznam popisuje některá omezení pro vyhodnocení výrazu XPath.

- Jsou povoleny pouze předdefinované funkce XPath.

- Integrované funkce XSLT, jako například `document()` , `key()` a tak dále, nejsou povoleny.

- Uživatelsky definované funkce nejsou povoleny.

  Další informace naleznete v tématu [How to: Evaluate a XPath Expression](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Okno zpětného překladu
 Okno zpětný překlad zobrazuje kód sestavení generovaný kompilátorem XSLT. Toto okno lze použít stejným způsobem jako všechny ostatní okna aplikace sady Visual Studio pro zpětný překlad.

 Další informace najdete v tématu [Postup: použití okna](../debugger/how-to-use-the-disassembly-window.md)zpětného překladu.

## <a name="see-also"></a>Viz také
 [Ladění](../xml-tools/debugging-xslt.md) [oken s proměnnými](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e) [základní ladicího programu](../debugger/debugger-basics.md) XSLT
