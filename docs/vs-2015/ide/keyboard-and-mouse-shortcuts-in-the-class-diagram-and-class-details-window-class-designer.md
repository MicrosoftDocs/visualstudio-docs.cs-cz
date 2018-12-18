---
title: Klávesové zkratky a zkratky myši v diagramu tříd a okně podrobností třídy (návrhář tříd) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f607046609208804f349eb06e927ab8e72e28992
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247907"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Klávesové zkratky a zkratky myši v diagramu tříd a okně podrobností třídy (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klávesnice kromě myši můžete použít k provádění akcí navigace v Návrháři tříd a **podrobností třídy** okna.  
  
 **V tomto tématu**  
  
-   [Pomocí myši v Návrháři tříd](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)  
  
-   [Pomocí myši v okně podrobností třídy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)  
  
-   [Pomocí klávesnice v Návrháři tříd](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)  
  
-   [Pomocí klávesnice v okně podrobností třídy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)  
  
##  <a name="MouseClassDesigner"></a> Pomocí myši v Návrháři tříd  
 Tyto akce myši, jsou podporovány v diagramech tříd:  
  
|Kombinace myši|Kontext|Popis|  
|-----------------------|-------------|-----------------|  
|Dvakrát klikněte na panel|elementy obrazců|Otevře se editor kódu.|  
||Konektor typu Lupa|Rozbalit/sbalit lollipop.|  
||Popisek konektor typu Lupa|Vyvolá **zobrazit rozhraní** příkazu.|  
|Kolečko myši|Diagram tříd|Posuňte svisle.|  
|SHIFT + kolečko myši|Diagram tříd|Posuňte se vodorovně.|  
|CTRL + kolečko myši|Diagram tříd|Přiblížení.|  
|CTRL + Shift + kliknutí|Diagram tříd|Přiblížení.|  
  
##  <a name="MouseClassDetails"></a> Pomocí myši v okně podrobností třídy  
 Pomocí myši, můžete změnit vzhled v okně podrobností třídy a data, která se zobrazí takto:  
  
-   Kliknutím na libovolnou buňku upravitelné umožňuje upravovat obsah buňky. Vaše změny se projeví na všech místech, že data uložená nebo zobrazena, včetně v okně Vlastnosti ve zdrojovém kódu.  
  
-   Kliknutím na libovolnou buňku řádku způsobí, že v okně Vlastnosti k zobrazení vlastností pro element reprezentovaný daném řádku.  
  
-   Chcete-li změnit šířku sloupce přetáhněte okraj na pravé straně záhlaví sloupce sloupec je požadovanou šířku.  
  
-   Můžete rozbalit nebo sbalit oddíl nebo vlastnost uzly kliknutím na šipky vlevo od řádku.  
  
-   V okně podrobností třídy nabízí několik tlačítka pro vytvoření nové členy v aktuální třídě a pro procházení mezi oddíly členů v mřížce okno podrobností třídy. Další informace najdete v tématu tlačítka okna podrobností třídy.  
  
##  <a name="KeyboardClassDesigner"></a> Pomocí klávesnice v Návrháři tříd  
 Podporovány jsou následující akce klávesnice v diagramech tříd:  
  
|Key|Kontext|Popis|  
|---------|-------------|-----------------|  
|Klávesy se šipkami|Typ uvnitř obrazce|Navigační strom style na obrazec obsah (zabalení kolem obrazce se podporuje). Levé a pravé klíče Rozbalit/sbalit aktuální položky. Pokud je rozšiřitelná a přejděte do nadřazené, pokud nebude (Zobrazit zobrazení stromu navigace pro podrobné chování).|  
||Nejvyšší úrovně tvary|Přesunutí tvary v diagramu.|  
|SHIFT + ŠIPKA klíče|Typ uvnitř obrazce|Výběr průběžné vytváření skládající se z elementy obrazců například členů, vnořené typy nebo oddíly. Tyto klávesové zkratky zabalení kolem nepodporují.|  
|DOMOVSKÁ STRÁNKA|Typ uvnitř obrazce|Přejděte na nadpis obrazec nejvyšší úrovně.|  
||Nejvyšší úrovně tvary|Přejděte do první obrazec v diagramu.|  
|END|Typ uvnitř obrazce|Přechod na poslední prvek viditelný uvnitř obrazce.|  
||Nejvyšší úrovně tvary|Přejděte na poslední obrazec v diagramu.|  
|SHIFT + HOME|Typ uvnitř obrazce|Vybere elementy v rámci tvaru spuštění s aktuální položkou a konče nejvyšším položku na stejný tvar.|  
|SHIFT + END|Typ uvnitř obrazce|Stejné jako SHIFT + HOME, ale ve směru shora dolů.|  
|ZADEJTE|Všechny kontexty|Volá výchozí akce na obrazec, který je také k dispozici prostřednictvím dvojím kliknutím. Ve většině případů jde zobrazit kód, ale některé prvky definujte ho jinak (cukroví, oddíl hlavičky, popisky typu Lupa).|  
|+/-|Všechny kontexty|Pokud je aktuálně nastavený fokus element rozšíření, tyto klíče Rozbalit/sbalit elementu.|  
|>|Všechny kontexty|U elementů s podřízenými rozšíří element, pokud je sbalené a přejde na prvním podřízeným objektem.|  
|<|Všechny kontexty|Přejde na nadřazený prvek.|  
|ALT + SHIFT + L|Uvnitř obrazce typu + obrazců typu.|Přejde k lupě aktuálně vybraný tvar, pokud je k dispozici.|  
|ALT + SHIFT + B|Uvnitř obrazce typu + obrazců typu.|Pokud seznam základních typů se zobrazí na tvar typu a má více než jednu položku, to přepíná stavu rozbalení seznamu (rozbalení/sbalení).|  
|DELETE|Na typu a přidejte komentář u obrazce|Vyvolá **odebrat z diagramu** příkazu.|  
||Na všechno ostatní.|Vyvolá **odstranit z kódu** příkazu (členy, parametry, přidružení, dědičnosti a lollipop štítků).|  
|CTRL + DELETE|Všechny kontexty|Vyvolá **odstranit z kódu** příkaz na výběr.|  
|KARTA|Všechny kontexty|Přejde na další podřízenou položku v rámci stejnou nadřazenou položku (zabalení podporuje).|  
|SHIFT + TAB|Všechny kontexty|Přejde na předchozí podřízenou položku v rámci stejnou nadřazenou položku (zabalení podporuje).|  
|MÍSTO|Všechny kontexty|Přepne výběr u aktuálního elementu.|  
  
##  <a name="KeyboardClassDetails"></a> Pomocí klávesnice v okně podrobností třídy  
  
> [!NOTE]
>  Následující klávesové zkratky byly rozhodli konkrétně tak, aby napodoboval prostředí psaní kódu.  
  
 Použijte následující klíče pro navigaci v okně podrobností třídy:  
  
|||  
|-|-|  
|Key|Výsledek|  
|, (čárka)|Pokud je kurzor na řádku parametru, zadáním čárku přesune kurzor do pole Název parametru Další. Pokud je kurzor na poslední řádek parametru metody, přesune kurzor \<přidat parametr > pole, které můžete použít k vytvoření nového parametru.<br /><br /> Pokud je kurzor jinde v okně podrobností třídy, zadáním čárku doslova přidá čárku v aktuálním poli.|  
|; (středník)<br /><br /> or<br /><br /> ) (pravá závorka)|Přesuňte kurzor do pole název dalšího člena řádku v mřížce okno podrobností třídy.|  
|Tabulátor|Přesune kurzor na další pole, první přesun klikněte shora dolů a zleva doprava. Pokud je kurzor přesouvá z pole, ve které jste zadali text, okno podrobností třídy zpracovává text a uloží jej případě nevytváří chybu.<br /><br /> Jestli je ukazatel na prázdné pole, jako \<přidat parametr >, přejde se na první pole na další řádek.|  
|\<místo >|Přesune kurzor na další pole, první přesun klikněte shora dolů a zleva doprava. Jestli je ukazatel na prázdné pole, jako \<přidat parametr >, přejde do prvního pole na další řádek. Všimněte si, že \<místo > zadali ihned poté, co je ignorován čárkou.<br /><br /> Pokud je kurzor v poli Summary, zadáním mezery přidá znak mezery.<br /><br /> Pokud je kurzor v skrýt sloupce daného řádku, zadáte mezeru přepne hodnotu zaškrtávací políčko Skrýt.|  
|CTRL + Tab|Přepnout na další okno dokumentu. Například přepněte v okně podrobností třídy do souboru otevřete kód.|  
|ESC (ESC)|Pokud jste začali můžete napsat text v poli, stiskněte klávesu ESC funguje jako klíč vrácení zpět, vrácení zpět pole obsah na původní hodnotu. Pokud okno podrobností třídy obecné fokus, ale žádné konkrétní buňky má fokus, stiskněte klávesu ESC přesune fokus z okna podrobností třídy.|  
|Šipka nahoru a Šipka dolů|Tyto klíče přesuňte kurzor na řádek řádku svisle v mřížce okno podrobností třídy.|  
|Šipka doleva|Pokud je kurzor ve sloupci Název, stisknete šipku vlevo sbalí aktuální uzel v hierarchii (je-li otevřít).|  
|Šipka doprava|Pokud je kurzor ve sloupci Název, stisknutím klávesy se šipkou vpravo rozšíří aktuální uzel v hierarchii (Pokud je sbalený).|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a konfigurace členů typů (Návrhář tříd)](../ide/creating-and-configuring-type-members-class-designer.md)



