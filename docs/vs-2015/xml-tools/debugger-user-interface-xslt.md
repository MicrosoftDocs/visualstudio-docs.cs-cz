---
title: Ladicí program uživatelského rozhraní (XSLT) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 02ba962a3410b2e964e7653fcb6308b9209def44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891846"
---
# <a name="debugger-user-interface-xslt"></a>Uživatelské rozhraní ladicího programu (XSLT)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje oknech ladicího programu a dialogových oknech. Popisuje pouze uživatelské rozhraní části, ze kterých mají ladění chování specifické pro XSLT.  
  
 Další informace najdete v tématu [ladění odkazu uživatelského rozhraní](../debugger/debugging-user-interface-reference.md).  
  
## <a name="locals-window"></a>Okno místních hodnot  
 V okně místních hodnot zobrazí informace o všechny proměnné definované v šabloně stylů. V okně místních hodnot obsahuje tři sloupce informací:  
  
 **Jméno**  
 Tento sloupec obsahuje názvy všech místních proměnných v aktuálním oboru. Uzel sady mají ovládacím prvkem strom, který je můžete přejít na najdete v jejích podsložkách.  
  
 **Hodnota**  
 Tento sloupec zobrazuje hodnota obsažená v každé proměnné. Atribut zpracování instrukce, komentáře, text a CData uzlů zobrazovat textové hodnoty uzlu. Uzly Namespace zobrazit identifikátor URI oboru názvů.  
  
 **Typ**  
 V tomto sloupci určuje datový typ uvedených v proměnných **název** sloupce.  
  
 V okně místních hodnot také zobrazí předdefinovaný kontextové proměnné, které sledují kontextu transformace XSLT. Následující tabulka popisuje předdefinované kontextové proměnné použít ladicí program XSLT.  
  
|Název|Popis|  
|----------|-----------------|  
|`last()`|Velikost kontextu.|  
|`position()`|Pozici nebo číslo indexu, vzhledem k velikosti kontextu kontextu uzlu.|  
|`self::node()`|Hodnota kontextu uzlu.|  
  
 Další informace najdete v tématu [postupy: Změna kontextu ladicího programu](http://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).  
  
## <a name="output-window"></a>Okno Výstup  
 V okně výstupu se zobrazí všechny chybové zprávy nebo zabezpečení, ke kterým dochází během ladění.  
  
 Ladicí program XSLT používá samostatné okno k zobrazení výstupu ladicího programu. Toto je stejné okno sloužící k zobrazení výstupu z **zobrazení výstupu XSL** příkazu.  
  
## <a name="task-list"></a>Seznam úloh  
 Seznam úkolů obsahuje seznam všech chyb kompilace v šabloně stylů. Poklepáním chybu přesměruje kurzor na řádku s chybou.  
  
 Seznam úkolů obsahuje všechny chyby, ke kterým dochází v blocích skriptu v souboru XSLT.  
  
> [!NOTE]
>  Ladicí program XSLT nemá žádná upozornění, proto nikdy objeví v seznamu úkolů.  
  
## <a name="breakpoints-window"></a>Zarážky – okno  
 V okně zarážek se zobrazí všechny zarážky nastavené v aktuálním projektu. Pokud přidáte zarážku v okně je v zobrazení, v okně automaticky aktualizuje a zobrazí novou zarážku.  
  
 V okně zarážek by se měly chovat stejně jako ostatní ladicích programů sady Visual Studio.  
  
## <a name="command-windowimmediate-window"></a>Příkaz okno/příkazové podokno  
 V této verzi ladicí program XSLT není implementováno.  
  
## <a name="watch-window"></a>Okno kukátka  
 V okně kukátko se používá k vyhodnocení proměnné. Můžete také změnit hodnoty proměnných.  
  
 Proměnné zobrazí v okně kukátka jsou pro aktuální kontext (položka úplně nahoře v zásobníku volání). Pokud změníte kontext, okna kukátka aktualizuje a zobrazí proměnné nastavené pro tento kontext.  
  
## <a name="call-stack-window"></a>Okno zásobník volání  
 V okně zásobník volání se používá k zobrazení názvy funkcí v zásobníku volání, typy parametrů a hodnot parametrů. Informace v zásobníku volání se zobrazí, pouze pokud laděnému programu je ve stavu přerušení.  
  
 Zásobník volání představuje různé kontexty, které právě probíhá zpracování XSLT. Například, pokud je volání z šablony "a" do šablony "b", šablona "a" a šablony "b" se zobrazí v okně zásobníku volání s aktuální kontext na začátek seznamu. Uživatel se může zobrazit dotaz, který aktuálně spouští.  
  
 Pokud se šablony nemají název v souboru XSLT, se používají názvy generovaných procesoru XSLT.  
  
 Kliknutí na položku než v horní části seznamu označuje do prohlížeče, kde větev provedení transformace XSLT pomocí standardní zelené zvýraznění se stalo a zelené šipky.  
  
## <a name="quickwatch-dialog-box"></a>Dialogové okno Rychlé kukátko  
 **QuickWatch** dialogové okno se používá k vyhodnocení výrazů XPath 1.0. Kontextový uzel ( `self::node()` uzel v okně místní hodnoty) poskytuje kontext pro provádění výrazu XPath. Výsledek provedení výraz XPath se zobrazí v okně kukátko.  
  
 Následující seznam popisuje některé omezení pro vyhodnocení výrazu XPath.  
  
- Jsou povoleny pouze integrované funkce XPath.  
  
- XSLT integrované funkce, jako například `document()`, `key()`, a tak dále, nejsou povoleny.  
  
- Uživatelem definované funkce nejsou povoleny.  
  
  Další informace najdete v tématu [postupy: vyhodnocení výrazu XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>Okno zpětného překladu  
 V okně zpětný překlad zobrazí kód sestavení generovaný kompilátorem XSLT. Toto okno lze použít stejně jako všechny ostatní okna zpětného překladu sady Visual Studio.  
  
 Další informace najdete [postupy: použití okna zpětného překladu](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění XSLT](../xml-tools/debugging-xslt.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Proměnné Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)

