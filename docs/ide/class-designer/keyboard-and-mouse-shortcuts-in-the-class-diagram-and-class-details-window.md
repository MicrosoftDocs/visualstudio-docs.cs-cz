---
title: Klávesové zkratky a zkratky myši pro návrháře tříd
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87b447c3cf2fbba77584675edf3d34f44a98cb64
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848498"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Klávesové zkratky klávesnice a myši v diagramu tříd a podrobností třídy okna

Klávesnice kromě myši můžete použít k provádění akcí navigační v **návrhář tříd** a **podrobností třídy** okna.

## <a name="use-the-mouse-in-class-designer"></a>Pomocí myši v Návrháři tříd

Tyto akce myši, jsou podporovány v diagramech tříd:

|Kombinace myši|Kontext|Popis|
| - |-------------|-----------------|
|Dvakrát klikněte na panel|elementy obrazců|Otevře se editor kódu.|
|Dvakrát klikněte na panel|Konektor typu Lupa|Rozbalit/sbalit lollipop.|
|Dvakrát klikněte na panel|Popisek konektor typu Lupa|Vyvolá **zobrazit rozhraní** příkazu.|
|Kolečko myši|Diagram tříd|Posuňte svisle.|
|**SHIFT** + kolečko myši|Diagram tříd|Posuňte se vodorovně.|
|**CTRL** + kolečko myši|Diagram tříd|Přiblížení.|
|**CTRL**+**Shift** + klikněte na|Diagram tříd|Přiblížení.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Pomocí myši v okně podrobností třídy

Pomocí myši, můžete změnit vzhled **podrobností třídy** okno a data se zobrazí takto:

- Kliknutím na libovolnou buňku upravitelné umožňuje upravovat obsah buňky. Vaše změny se projeví na všech místech, že data uložená nebo zobrazena, včetně **vlastnosti** okno a ve zdrojovém kódu.

- Kliknutím na libovolnou buňku řádku způsobí, že **vlastnosti** okno k zobrazení vlastností pro element reprezentovaný daném řádku.

- Chcete-li změnit šířku sloupce přetáhněte okraj na pravé straně záhlaví sloupce sloupec je požadovanou šířku.

- Můžete rozbalit nebo sbalit oddíl nebo vlastnost uzly kliknutím na šipky vlevo od řádku.

- **Podrobností třídy** okno nabízí několik tlačítka pro vytvoření nové členy v aktuální třídě a pro procházení mezi oddíly členů v **podrobností třídy** mřížky okna okno.

## <a name="use-the-keyboard-in-class-designer"></a>Použití klávesnice v Návrháři tříd

Podporovány jsou následující akce klávesnice v diagramech tříd:

|Key|Kontext|Popis|
|---------|-------------|-----------------|
|**Klávesy se šipkami**|Typ uvnitř obrazce|Navigační strom style na obrazec obsah (zabalení kolem obrazce se podporuje). Levé a pravé klíče Rozbalit/sbalit aktuální položky. Pokud je rozšiřitelná a přejděte do nadřazené, pokud nebude (Zobrazit zobrazení stromu navigace pro podrobné chování).|
|**Klávesy se šipkami**|Nejvyšší úrovně tvary|Přesunutí tvary v diagramu.|
|**SHIFT**+**klávesy se šipkami**|Typ uvnitř obrazce|Výběr průběžné vytváření skládající se z elementy obrazců například členů, vnořené typy nebo oddíly. Tyto klávesové zkratky zabalení kolem nepodporují.|
|**Domovská stránka**|Typ uvnitř obrazce|Přejděte na nadpis obrazec nejvyšší úrovně.|
|**Domovská stránka**|Nejvyšší úrovně tvary|Přejděte do první obrazec v diagramu.|
|**ukončení**|Typ uvnitř obrazce|Přechod na poslední prvek viditelný uvnitř obrazce.|
|**ukončení**|Nejvyšší úrovně tvary|Přejděte na poslední obrazec v diagramu.|
|**SHIFT**+**Domů**|Typ uvnitř obrazce|Vybere elementy v rámci tvaru spuštění s aktuální položkou a konče nejvyšším položku na stejný tvar.|
|**SHIFT**+**End**|Typ uvnitř obrazce|Stejné jako **Shift**+**Domů** , ale ve směru shora dolů.|
|**Zadejte**|Všechny kontexty|Volá výchozí akce na obrazec, který je také k dispozici prostřednictvím dvojím kliknutím. Ve většině případů jde zobrazit kód, ale některé prvky definujte ho jinak (cukroví, oddíl hlavičky, popisky typu Lupa).|
|**+** a **-**|Všechny kontexty|Pokud je aktuálně nastavený fokus element rozšíření, tyto klíče rozbalit nebo sbalit elementu.|
|**>**|Všechny kontexty|U elementů s podřízenými rozšíří element, pokud je sbalené a přejde na prvním podřízeným objektem.|
|**<**|Všechny kontexty|Přejde na nadřazený prvek.|
|**ALT**+**Shift**+**L**|Uvnitř obrazce typu + obrazců typu.|Přejde k lupě aktuálně vybraný tvar, pokud je k dispozici.|
|**ALT**+**Shift**+**B**|Uvnitř obrazce typu + obrazců typu.|Pokud seznam základních typů se zobrazí na tvar typu a má více než jednu položku, to přepíná stavu rozbalení seznamu (rozbalení/sbalení).|
|**Delete**|Na typu a přidejte komentář u obrazce|Vyvolá **odebrat z diagramu** příkazu.|
|**Delete**|Na všechno ostatní.|Vyvolá **odstranit z kódu** příkazu (členy, parametry, přidružení, dědičnosti a lollipop štítků).|
|**CTRL**+**odstranit**|Všechny kontexty|Vyvolá **odstranit z kódu** příkaz na výběr.|
|**Karta**|Všechny kontexty|Přejde na další podřízenou položku v rámci stejnou nadřazenou položku (zabalení podporuje).|
|**SHIFT**+**kartu**|Všechny kontexty|Přejde na předchozí podřízenou položku v rámci stejnou nadřazenou položku (zabalení podporuje).|
|**MEZERNÍK**|Všechny kontexty|Přepne výběr u aktuálního elementu.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Použití klávesnice v okně podrobností třídy

> [!NOTE]
> Následující klávesové zkratky byly rozhodli konkrétně tak, aby napodoboval prostředí psaní kódu.

Pomocí těchto klíčů přejděte **podrobností třídy** okno:

|||
|-|-|
|Key|Výsledek|
|**,** (čárka)|Pokud je kurzor na řádku parametru, zadáním čárku přesune kurzor do pole Název parametru Další. Pokud je kurzor na poslední řádek parametru metody, přesune kurzor \<přidat parametr > pole, které můžete použít k vytvoření nového parametru.<br /><br /> Pokud je kurzor v jiném místě **podrobností třídy** okna, zadáním čárku doslova přidá čárku v aktuálním poli.|
|**;**  (středník) nebo **)** (ukončovací závorka)|Přesuňte kurzor do pole název v dalším řádku člena **podrobností třídy** mřížky okna okno.|
|**Karta**|Přesune kurzor na další pole, první přesun klikněte shora dolů a zleva doprava. Pokud je kurzor přesouvá z pole, ve které jste zadali text, **podrobností třídy** zpracovává text a uloží je v případě nevytváří chybu.<br /><br /> Jestli je ukazatel na prázdné pole, jako \<přidat parametr >, přejde se na první pole na další řádek.|
|**MEZERNÍK**|Přesune kurzor na další pole, první přesun klikněte shora dolů a zleva doprava. Jestli je ukazatel na prázdné pole, jako \<přidat parametr >, přejde do prvního pole na další řádek. Všimněte si, že \<místo > zadali ihned poté, co je ignorován čárkou.<br /><br /> Pokud je kurzor v poli Summary, zadáním mezery přidá znak mezery.<br /><br /> Pokud je kurzor v skrýt sloupce daného řádku, zadáte mezeru přepne hodnotu zaškrtávací políčko Skrýt.|
|**CTRL**+**kartu**|Přepnout na další okno dokumentu. Například přejít z **podrobností třídy** okna do souboru otevřete kód.|
|**ESC**|Pokud jste začali můžete napsat text v poli, stiskněte klávesu ESC funguje jako klíč vrácení zpět, vrácení zpět pole obsah na původní hodnotu. Pokud okno podrobností třídy obecné fokus, ale žádné konkrétní buňky má fokus, stiskněte klávesu ESC přesune fokus klávesou **podrobností třídy** okna.|
|**Šipka nahoru** a **šipka dolů**|Tyto klíče přesuňte kurzor na řádek řádku svisle v **podrobností třídy** mřížky okna okno.|
|**Šipka doleva**|Pokud je kurzor ve sloupci Název, stisknete šipku vlevo sbalí aktuální uzel v hierarchii (je-li otevřít).|
|**Šipka doprava**|Pokud je kurzor ve sloupci Název, stisknutím klávesy se šipkou vpravo rozšíří aktuální uzel v hierarchii (Pokud je sbalený).|

## <a name="see-also"></a>Viz také:

- [Vytvoření a konfigurace členů typu](creating-and-configuring-type-members.md)