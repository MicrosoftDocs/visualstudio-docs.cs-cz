---
title: Klávesové zkratky a zkratky myši v diagramu tříd a Okno podrobností třídy (Návrhář tříd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5865059e60907397ae7d69b230676ac63a5c3386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543114"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Klávesové zkratky a zkratky myši v diagramu tříd a okně podrobností třídy (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí klávesnice můžete kromě myši provádět navigační akce v Návrhář tříd a v okně **podrobností třídy** .

 **V tomto tématu**

- [Používání myši v Návrhář tříd](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)

- [Používání myši v Okno podrobností třídy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)

- [Používání klávesnice v Návrhář tříd](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)

- [Použití klávesnice v Okno podrobností třídy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)

## <a name="using-the-mouse-in-class-designer"></a><a name="MouseClassDesigner"></a> Používání myši v Návrhář tříd
 Následující akce myši jsou podporovány v diagramech tříd:

|Kombinace myši|Kontext|Popis|
|-----------------------|-------------|-----------------|
|Dvakrát klikněte na|elementy obrazců|Otevře Editor kódu.|
||Konektor lupy|Rozbalit nebo sbalit Lupa|
||Popisek konektoru lupy|Vyvolá příkaz **Zobrazit rozhraní** .|
|Kolečko myši|Diagram tříd|Posuňte se vertikálně.|
|SHIFT + kolečko myši|Diagram tříd|Posuňte se vodorovně.|
|CTRL + kolečko myši|Diagram tříd|Přibliž.|
|CTRL + SHIFT + kliknutí|Diagram tříd|Přibliž.|

## <a name="using-the-mouse-in-the-class-details-window"></a><a name="MouseClassDetails"></a> Používání myši v Okno podrobností třídy
 Pomocí myši můžete změnit vzhled okna podrobností třídy a zobrazená data, a to následujícími způsoby:

- Kliknutím na libovolnou upravitelnou buňku můžete upravit obsah této buňky. Vaše změny se projeví na všech místech, kde jsou data uložená nebo zobrazená, včetně v okno Vlastnosti a ve zdrojovém kódu.

- Kliknutí na libovolnou buňku řádku způsobí, že okno Vlastnosti zobrazí vlastnosti prvku reprezentovaného tímto řádkem.

- Chcete-li změnit šířku sloupce, přetáhněte hranici na pravé straně záhlaví sloupce, dokud sloupec nedosáhne požadované šířky.

- Můžete rozbalit nebo Sbalit oddíl nebo uzly vlastností kliknutím na symbol šipky nalevo od řádku.

- Okno podrobností třídy nabízí několik tlačítek pro vytváření nových členů v aktuální třídě a pro navigaci mezi přihrádkami členů v mřížce Okno podrobností třídy. Další informace najdete v tématu Okno podrobností třídych tlačítek.

## <a name="using-the-keyboard-in-class-designer"></a><a name="KeyboardClassDesigner"></a> Používání klávesnice v Návrhář tříd
 V diagramech tříd jsou podporovány následující akce klávesnice:

|Klíč|Kontext|Popis|
|---------|-------------|-----------------|
|Šipkové klávesy|Uvnitř typů tvarů|Navigace ve stylu stromu v obsahu obrazce (je podporováno obtékání kolem obrazce). Levé a pravé klávesy rozbalí nebo sbalí aktuální položku, pokud je rozšiřitelná, a pokud ne, přejděte na nadřazený objekt (podrobné chování najdete v tématu navigace stromu zobrazení).|
||Tvary nejvyšší úrovně|Přesunutí tvarů v diagramu.|
|SHIFT + klávesy se šipkami|Uvnitř typů tvarů|Sestavování průběžného výběru sestávající z prvků tvaru, jako jsou členy, vnořené typy nebo oddíly. Tyto klávesové zkratky nepodporují obtékání kolem.|
|DOMŮ|Uvnitř typů tvarů|Přejděte k názvu obrazce nejvyšší úrovně.|
||Tvary nejvyšší úrovně|Přejděte k prvnímu tvaru v diagramu.|
|END|Uvnitř typů tvarů|Přejděte k poslednímu viditelnému prvku uvnitř obrazce.|
||Tvary nejvyšší úrovně|Přejděte k poslednímu obrazci v diagramu.|
|SHIFT + HOME|Uvnitř tvaru typu|Vybere prvky v rámci tvaru počínaje aktuální položkou a končící nejvyšší položkou na stejném obrazci.|
|SHIFT + END|Uvnitř tvaru typu|Stejné jako SHIFT + HOME, ale v směru shora dolů.|
|ENTER|Všechny kontexty|Vyvolá výchozí akci pro obrazec, který je také k dispozici prostřednictvím dvojího kliknutí. Ve většině případů se jedná o kód zobrazení kódu, ale některé prvky jej definují odlišně (Lupa, záhlaví oddílů, popisky lupy).|
|+/-|Všechny kontexty|Pokud je aktuálně zaměřený element rozšiřitelný, tyto klíče rozbalí nebo sbalí element.|
|>|Všechny kontexty|U elementů s podřízenými prvky rozbalí prvek, pokud je sbalený, a přejde na první podřízenou položku.|
|<|Všechny kontexty|Přejde na nadřazený element.|
|ALT + SHIFT + L|Uvnitř typů Shapes + u tvarů typů.|Přejde na Lupa aktuálně vybraného obrazce, pokud je přítomen.|
|ALT + SHIFT + B|Uvnitř typů Shapes + u tvarů typů.|Pokud je v obrazovém prvku zobrazen seznam základních typů a má více než jednu položku, Přepíná stav rozbalení seznamu (sbalení a rozbalení).|
|DELETE|Pro tvary typu a komentáře|Vyvolá příkaz **Remove z diagramu** .|
||Na všechno ostatní.|Vyvolá příkaz **Odstranit z kódu** (členové, parametry, přidružení, dědičnost, popisky typu Lupa).|
|CTRL + DELETE|Všechny kontexty|Vyvolá **odstranění z příkazu kódu** při výběru.|
|TAB|Všechny kontexty|Přejde na další podřízenou položku v rámci stejné nadřazené položky (podporuje zalamování).|
|SHIFT+TAB|Všechny kontexty|Přejde na předchozí podřízenou položku v rámci stejné nadřazené položky (podporuje zalamování).|
|SPACE|Všechny kontexty|Přepíná výběr na aktuálním prvku.|

## <a name="using-the-keyboard-in-the-class-details-window"></a><a name="KeyboardClassDetails"></a> Použití klávesnice v Okno podrobností třídy

> [!NOTE]
> Následující vazby klíčů byly zvoleny pro specificky napodobení možnosti psaní kódu.

 K procházení okna podrobností třídy použijte následující klávesy:

|Klíč|Výsledek|
|-|-|
|, (čárka)|Pokud je kurzor v řádku parametrů, zadáním čárky se přesune kurzor do pole název dalšího parametru. Pokud je kurzor v řádku posledního parametru metody, přesune kurzor do \<add parameter> pole, které můžete použít k vytvoření nového parametru.<br /><br /> Pokud se kurzor nachází jinde v Okno podrobností třídy, zadejte čárkou, která bude v aktuálním poli přidána čárkou.|
|; střední<br /><br /> nebo<br /><br /> ) (pravá závorka)|Přesuňte kurzor do pole název dalšího řádku člena v mřížce Okno podrobností třídy.|
|Karta|Přesune kurzor do dalšího pole, nejprve se přesunou zleva doprava a pak shora dolů. Pokud se kurzor pohybuje z pole, ve kterém jste zadali text, Okno podrobností třídy zpracuje tento text a uloží jej, pokud nevytvoří chybu.<br /><br /> Pokud je kurzor na prázdném poli \<add parameter> , například, TAB ho přesune do prvního pole v dalším řádku.|
|\<space>|Přesune kurzor do dalšího pole, nejprve se přesunou zleva doprava a pak shora dolů. Pokud je kurzor na prázdném poli \<add parameter> , například, přesune se do prvního pole dalšího řádku. Všimněte si, že \<space> zadané hned po čárkě se ignorují.<br /><br /> Pokud je kurzor v poli Souhrn, zadáním mezery se přidá znak mezery.<br /><br /> Pokud se kurzor nachází ve sloupci skrýt daného řádku, zadáním mezery se přepíná hodnota zaškrtávacího políčka Skrýt.|
|CTRL + TAB|Přepne na další okno dokumentu. Například přepněte z Okno podrobností třídy na otevřený soubor kódu.|
|ESC (řídicí znak)|Pokud jste začali psát text do pole, stiskněte klávesu ESC jako klíč k vrácení zpět a vrátíte obsah pole na předchozí hodnotu. Pokud má Okno podrobností třídy obecný fokus, ale žádná konkrétní buňka nemá fokus, se stisknutí klávesy ESC přesune mimo Okno podrobností třídy fokus.|
|Šipka nahoru a šipka dolů|Tyto klávesy posunou kurzor z řádku do řádku svisle v Okno podrobností třídy mřížce.|
|Šipka vlevo|Pokud je kurzor ve sloupci název, stisknutím šipky vlevo sbalíte aktuální uzel v hierarchii (Pokud je otevřený).|
|Šipka vpravo|Pokud je kurzor ve sloupci název, stisknutí šipky vpravo rozbalí aktuální uzel v hierarchii (Pokud je sbalený).|

## <a name="see-also"></a>Viz také
 [Vytváření a konfigurace členů typů (návrhář tříd)](../ide/creating-and-configuring-type-members-class-designer.md)
