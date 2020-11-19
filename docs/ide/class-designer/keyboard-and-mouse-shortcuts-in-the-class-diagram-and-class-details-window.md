---
title: Zkratky klávesnice a myši pro Návrhář tříd
description: Naučte se používat klávesnici kromě myši k provádění navigačních akcí v Návrhář tříd a v okně podrobností třídy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c184a12474e2d7ff0b626547acaaf2a37d460c8e
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901099"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Klávesové zkratky a zkratky myši v diagramu tříd a okně podrobností třídy

Pomocí klávesnice můžete kromě myši provádět navigační akce v **Návrhář tříd** a v okně **podrobností třídy** .

## <a name="use-the-mouse-in-class-designer"></a>Použít myš v Návrhář tříd

Následující akce myši jsou podporovány v diagramech tříd:

|Kombinace myši|Kontext|Popis|
| - |-------------|-----------------|
|Dvakrát klikněte na|elementy obrazců|Otevře Editor kódu.|
|Dvakrát klikněte na|Konektor lupy|Rozbalit nebo sbalit Lupa|
|Dvakrát klikněte na|Popisek konektoru lupy|Vyvolá příkaz **Zobrazit rozhraní** .|
|Kolečko myši|Diagram tříd|Posuňte se vertikálně.|
|**SHIFT** + kolečko myši|Diagram tříd|Posuňte se vodorovně.|
|**CTRL** + kolečko myši|Diagram tříd|Přibliž.|
|**CTRL** + **SHIFT** + kliknutí|Diagram tříd|Přibliž.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Použití myši v okně podrobností třídy

Pomocí myši můžete změnit vzhled okna **podrobností třídy** a data, která se zobrazí, následujícími způsoby:

- Kliknutím na libovolnou upravitelnou buňku můžete upravit obsah této buňky. Vaše změny se projeví na všech místech, kde jsou data uložená nebo zobrazená, včetně v okně **vlastnosti** a ve zdrojovém kódu.

- Kliknutí na libovolnou buňku řádku způsobí, že okno **vlastnosti** zobrazí vlastnosti prvku reprezentovaného tímto řádkem.

- Chcete-li změnit šířku sloupce, přetáhněte hranici na pravé straně záhlaví sloupce, dokud sloupec nedosáhne požadované šířky.

- Můžete rozbalit nebo Sbalit oddíl nebo uzly vlastností kliknutím na symbol šipky nalevo od řádku.

- Okno **podrobností třídy** nabízí několik tlačítek pro vytváření nových členů v aktuální třídě a pro navigaci mezi přihrádkami členů v mřížce okna **podrobností třídy** .

## <a name="use-the-keyboard-in-class-designer"></a>Použijte klávesnici v Návrhář tříd

V diagramech tříd jsou podporovány následující akce klávesnice:

|Klíč|Kontext|Popis|
|---------|-------------|-----------------|
|**Šipkové klávesy**|Uvnitř typů tvarů|Navigace ve stylu stromu v obsahu obrazce (je podporováno obtékání kolem obrazce). Levé a pravé klávesy rozbalí nebo sbalí aktuální položku, pokud je rozšiřitelná, a pokud ne, přejděte na nadřazený objekt (podrobné chování najdete v tématu navigace stromu zobrazení).|
|**Šipkové klávesy**|Tvary nejvyšší úrovně|Přesunutí tvarů v diagramu.|
|**Posun** + **klávesy se šipkami**|Uvnitř typů tvarů|Sestavování průběžného výběru sestávající z prvků tvaru, jako jsou členy, vnořené typy nebo oddíly. Tyto klávesové zkratky nepodporují obtékání kolem.|
|**Domů**|Uvnitř typů tvarů|Přejděte k názvu obrazce nejvyšší úrovně.|
|**Domů**|Tvary nejvyšší úrovně|Přejděte k prvnímu tvaru v diagramu.|
|**End**|Uvnitř typů tvarů|Přejděte k poslednímu viditelnému prvku uvnitř obrazce.|
|**End**|Tvary nejvyšší úrovně|Přejděte k poslednímu obrazci v diagramu.|
|**Posun** + **Domovská stránka**|Uvnitř tvaru typu|Vybere prvky v rámci tvaru počínaje aktuální položkou a končící nejvyšší položkou na stejném obrazci.|
|**Posun** + **Konec**|Uvnitř tvaru typu|Stejné jako při **posunu** + **Domů** , ale směr shora dolů.|
|**Napište**|Všechny kontexty|Vyvolá výchozí akci pro obrazec, který je také k dispozici prostřednictvím dvojího kliknutí. Ve většině případů se jedná o kód zobrazení kódu, ale některé prvky jej definují odlišně (Lupa, záhlaví oddílů, popisky lupy).|
|**+** ani **-**|Všechny kontexty|Pokud je aktuálně zaměřený element rozšiřitelný, tyto klíče rozbalí nebo sbalí prvek.|
|**>**|Všechny kontexty|U elementů s podřízenými prvky rozbalí prvek, pokud je sbalený, a přejde na první podřízenou položku.|
|**<**|Všechny kontexty|Přejde na nadřazený element.|
|**ALT** + **Posun** + **L**|Uvnitř typů Shapes + u tvarů typů.|Přejde na Lupa aktuálně vybraného obrazce, pokud je přítomen.|
|**ALT** + **Posun** + **B**|Uvnitř typů Shapes + u tvarů typů.|Pokud je v obrazovém prvku zobrazen seznam základních typů a má více než jednu položku, Přepíná stav rozbalení seznamu (sbalení a rozbalení).|
|**Odstranit**|Pro tvary typu a komentáře|Vyvolá příkaz **Remove z diagramu** .|
|**Odstranit**|Na všechno ostatní.|Vyvolá příkaz **Odstranit z kódu** (členové, parametry, přidružení, dědičnost, popisky typu Lupa).|
|**CTRL** + **Odstranit**|Všechny kontexty|Vyvolá **odstranění z příkazu kódu** při výběru.|
|**Rážky**|Všechny kontexty|Přejde na další podřízenou položku v rámci stejné nadřazené položky (podporuje zalamování).|
|**Posun** + **Karta**|Všechny kontexty|Přejde na předchozí podřízenou položku v rámci stejné nadřazené položky (podporuje zalamování).|
|**Mezerník**|Všechny kontexty|Přepíná výběr na aktuálním prvku.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Použití klávesnice v okně podrobností třídy

> [!NOTE]
> Následující vazby klíčů byly zvoleny pro specificky napodobení možnosti psaní kódu.

K procházení okna **podrobností třídy** použijte následující klávesy:

|Klíč|Výsledek|
|-|-|
|**,** (čárka)|Pokud je kurzor v řádku parametrů, zadáním čárky se přesune kurzor do pole název dalšího parametru. Pokud je kurzor v řádku posledního parametru metody, přesune kurzor do \<add parameter> pole, které můžete použít k vytvoření nového parametru.<br /><br /> Pokud se kurzor nachází jinde v okně **podrobností třídy** , zadáním čárky do aktuálního pole se přidá čárka.|
|**;** (středník) nebo **)** (pravá kulatá závorka)|Přesuňte kurzor na pole název dalšího řádku člena v mřížce okna **podrobností třídy** .|
|**Rážky**|Přesune kurzor do dalšího pole, nejprve se přesunou zleva doprava a pak shora dolů. Pokud se kurzor pohybuje z pole, ve kterém máte zadaný text, **Detaily třídy** zpracuje tento text a uloží, pokud nevytvoří chybu.<br /><br /> Pokud je kurzor na prázdném poli \<add parameter> , například, TAB ho přesune do prvního pole v dalším řádku.|
|**Mezerník**|Přesune kurzor do dalšího pole, nejprve se přesunou zleva doprava a pak shora dolů. Pokud je kurzor na prázdném poli \<add parameter> , například, přesune se do prvního pole dalšího řádku. Všimněte si, že \<space> zadané hned po čárkě se ignorují.<br /><br /> Pokud je kurzor v poli Souhrn, zadáním mezery se přidá znak mezery.<br /><br /> Pokud se kurzor nachází ve sloupci skrýt daného řádku, zadáním mezery se přepíná hodnota zaškrtávacího políčka Skrýt.|
|**CTRL** + **Karta**|Přepne na další okno dokumentu. Například přepněte z okna **podrobností třídy** na otevřený soubor kódu.|
|**Esc**|Pokud jste začali psát text do pole, stiskněte klávesu ESC jako klíč k vrácení zpět a vrátíte obsah pole na předchozí hodnotu. Pokud má Okno podrobností třídy obecný fokus, ale žádná konkrétní buňka nemá fokus, stisknutí klávesy ESC přesune fokus z okna **podrobností třídy** .|
|Šipka **nahoru** a **šipka dolů**|Tyto klávesy posunou kurzor z řádku do řádku svisle v mřížce okna **podrobností třídy** .|
|**Šipka vlevo**|Pokud je kurzor ve sloupci název, stisknutím šipky vlevo sbalíte aktuální uzel v hierarchii (Pokud je otevřený).|
|**Šipka doprava**|Pokud je kurzor ve sloupci název, stisknutí šipky vpravo rozbalí aktuální uzel v hierarchii (Pokud je sbalený).|

## <a name="see-also"></a>Viz také

- [Vytvoření a konfigurace členů typu](creating-and-configuring-type-members.md)
- [Jak používat výhradně klávesnici](../reference/how-to-use-the-keyboard-exclusively.md)
- [Výchozí klávesové zkratky v aplikaci Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md)
- [Klávesové zkratky v Blendu](../../xaml-tools/keyboard-shortcuts-in-blend.md)
