---
title: Klávesové zkratky a klávesové zkratky pro Návrháře tříd
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
ms.openlocfilehash: 6df4932a1043c984509632951ba67864fefe31ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590758"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Klávesové zkratky a klávesové zkratky myši v okně Diagram třídy a Podrobnosti o třídě

Kromě myši můžete používat klávesnici k provádění navigačních akcí v **Návrháři tříd** a v okně **Podrobnosti o třídě.**

## <a name="use-the-mouse-in-class-designer"></a>Použití myši v Návrháři tříd

V diagramech tříd jsou podporovány následující akce myši:

|Kombinace myši|Kontext|Popis|
| - |-------------|-----------------|
|Poklepejte|elementy obrazců|Otevře editor kódu.|
|Poklepejte|Konektor lízátka|Rozbalit / sbalit lízátko.|
|Poklepejte|Popisek konektoru Lollipop|Vyvolá příkaz **Zobrazit rozhraní.**|
|Kolečko myši|Diagram třídy|Posuňte se svisle.|
|**Shift** + kolečko myši|Diagram třídy|Posuňte se vodorovně.|
|**Ctrl** + kolečko myši|Diagram třídy|Zoom.|
|**Ctrl**+**Shift** + klikněte|Diagram třídy|Zoom.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Použití myši v okně Podrobnosti o třídě

Pomocí myši můžete změnit vzhled okna **Podrobnosti o třídě** a data, která se zobrazí následujícími způsoby:

- Kliknutím na libovolnou upravitelnou buňku můžete upravit obsah této buňky. Změny se projeví na všech místech, kde jsou data uložena nebo zobrazena, včetně v okně **Vlastnosti** a ve zdrojovém kódu.

- Klepnutí na libovolnou buňku řádku způsobí, že okno **Vlastnosti** zobrazí vlastnosti prvku reprezentovaného tímto řádkem.

- Chcete-li změnit šířku sloupce, přetáhněte ohraničení na pravé straně záhlaví sloupce tak, aby byl sloupec požadovaným šířkou.

- Uzly prostoru nebo vlastností můžete rozbalit nebo sbalit klepnutím na symboly šipek vlevo od řádku.

- Okno **Podrobnosti třídy** nabízí několik tlačítek pro vytváření nových členů v aktuální třídě a pro navigaci mezi oddíly členů v mřížce okna **Podrobnosti třídy.**

## <a name="use-the-keyboard-in-class-designer"></a>Použití klávesnice v Návrháři tříd

V diagramech tříd jsou podporovány následující akce klávesnice:

|Klíč|Kontext|Popis|
|---------|-------------|-----------------|
|**Šipkové klávesy**|Obrazce vnitřního textu|Navigace ve stromovém stylu na obsahu obrazce (obtékání kolem obrazce je podporováno). Levé a pravé klíče rozbalit nebo sbalit aktuální položku, pokud je rozšiřitelná a přejděte na nadřazenou, pokud ne (podrobné chování naleznete v navigaci stromového zobrazení).|
|**Šipkové klávesy**|Obrazce nejvyšší úrovně|Přesouvání obrazců v diagramu.|
|**Klávesy**+**se šipkami**|Obrazce vnitřního textu|Vytváření souvislého výběru skládající ho z prvků tvaru, jako jsou členy, vnořené typy nebo oddíly. Tyto zkratky nepodporují obtékání.|
|**Domů**|Obrazce vnitřního textu|Přejděte na název obrazce nejvyšší úrovně.|
|**Domů**|Obrazce nejvyšší úrovně|Přejděte k prvnímu obrazci v diagramu.|
|**Ukončení**|Obrazce vnitřního textu|Přejděte na poslední viditelný prvek uvnitř obrazce.|
|**Ukončení**|Obrazce nejvyšší úrovně|Přejděte k poslednímu obrazci v diagramu.|
|**Přesunout**+**domů**|Vnitřní tvar typu|Vybere prvky v obrazci počínaje aktuální položkou a končící položkou zcela nahoře na stejném obrazci.|
|**Konec směny**+**End**|Vnitřní tvar typu|Stejné jako **Shift**+**Home,** ale ve směru shora dolů.|
|**Enter**|Všechny kontexty|Vyvolá výchozí akci na obrazci, která je také k dispozici poklepáním. Ve většině případů se jedná o zobrazit kód, ale některé prvky definovat jinak (lízátka, záhlaví prostoru, lízátko štítky).|
|**+** A**-**|Všechny kontexty|Pokud aktuálně zaměřený prvek je rozbalitelný, tyto klíče rozbalit nebo sbalit prvek.|
|**>**|Všechny kontexty|Na prvky s podřízenými, to rozbalí prvek, pokud je sbalena a přejde na první podřízené.|
|**<**|Všechny kontexty|Přejde na nadřazený prvek.|
|**Alt**+**Shift**+**L**|Obrazce vnitřního textu + u obrazců textu.|Přejde na lízátko aktuálně vybraného obrazce, pokud je k dispozici.|
|**Alt**+**Shift**+**B**|Obrazce vnitřního textu + u obrazců textu.|Pokud je seznam základního typu zobrazen na obrazci typu a obsahuje více než jednu položku, přepíná se stav rozšíření seznamu (sbalit/rozbalit).|
|**Odstranit**|Na textařech a textech komentářů|Vyvolá **příkaz Odebrat z diagramu.**|
|**Odstranit**|Na všechno ostatní.|Vyvolá **příkaz Delete from Code** (členy, parametry, přidružení, dědičnost, popisky lízátka).|
|**Odstranění kláves Ctrl**+**Delete**|Všechny kontexty|Vyvolá příkaz **Odstranit z kódu** při výběru.|
|**Karta**|Všechny kontexty|Přejde na další podřízené v rámci stejného nadřazeného objektu (podporuje obtékání).|
|**Shift**+**Karta** Shift|Všechny kontexty|Přejde na předchozí podřízené v rámci stejného nadřazeného objektu (podporuje obtékání).|
|**Mezerník**|Všechny kontexty|Přepíná výběr na aktuálníprvek.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Použití klávesnice v okně Podrobnosti o třídě

> [!NOTE]
> Následující klíče vazby byly vybrány konkrétně napodobovat zkušenosti psaní kódu.

K navigaci v okně Podrobnosti o třídě použijte následující **klávesy:**

|||
|-|-|
|Klíč|Výsledek|
|**,** (čárka)|Pokud je kurzor v řádku parametru, zadáním čárky přesune kurzor do pole Název dalšího parametru. Pokud je kurzor v posledním řádku parametru metody, \<přesune kurzor na parametr add> pole, které můžete použít k vytvoření nového parametru.<br /><br /> Pokud je kurzor jinde v okně **Podrobnosti třídy,** zadáním čárky doslova přidá čárku v aktuálním poli.|
|**;** (středník) nebo **)** (uzavírací závorka)|Přesuňte kurzor do pole Název dalšího řádku člena v mřížce okna **Podrobnosti třídy.**|
|**Karta**|Přesune kurzor na další pole, nejprve se posune zleva doprava a potom shora dolů. Pokud se kurzor přesouvá z pole, do kterého jste zadali text, **podrobnosti třídy tento** text zpracují a uloží, pokud nezpůsobí chybu.<br /><br /> Pokud je kurzor na prázdném poli, například \<přidat parametr>, karta jej přesune do prvního pole dalšího řádku.|
|**Mezerník**|Přesune kurzor na další pole, nejprve se posune zleva doprava a potom shora dolů. Pokud je kurzor na prázdné \<masce, například přidat parametr>, přesune se do prvního pole dalšího řádku. Všimněte \<si, že místo> zadáno ihned po ignorování čárky.<br /><br /> Pokud je kurzor v poli Souhrn, zadáním mezery se přidá znak mezery.<br /><br /> Pokud je kurzor ve sloupci Skrýt daného řádku, přepnete mezeru na hodnotu zaškrtávacího políčka Skrýt.|
|**Ctrl**+**Karta** Ctrl|Přepněte do jiného okna dokumentu. Můžete například přepnout z okna **Podrobnosti třídy** na otevřený soubor kódu.|
|**Esc**|Pokud jste začali psát text do pole, stisknutí klávesy ESC funguje jako klávesa zpět a obsah pole se vrátí na jeho předchozí hodnotu. Pokud okno Podrobnosti třídy má obecné fokus, ale žádná konkrétní buňka má fokus, stisknutím klávesy ESC přesune fokus od okna **Podrobnosti třídy.**|
|**Šipka nahoru** a **šipka dolů**|Tyto klávesy přesunou kurzor z řádku do řádku svisle v mřížce okna **Podrobnosti třídy.**|
|**Šipka doleva**|Pokud je kurzor ve sloupci Název, stisknutím levé šipky se sbalí aktuální uzel v hierarchii (pokud je otevřený).|
|**Šipka doprava**|Pokud je kurzor ve sloupci Název, stisknutím šipky vpravo se rozšíří aktuální uzel v hierarchii (pokud je sbalený).|

## <a name="see-also"></a>Viz také

- [Vytvoření a konfigurace členů typu](creating-and-configuring-type-members.md)
- [Jak používat klávesnici výhradně](../reference/how-to-use-the-keyboard-exclusively.md)
- [Výchozí klávesové zkratky v Sadě Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md)
- [Klávesové zkratky v Blendu](../../xaml-tools/keyboard-shortcuts-in-blend.md)
