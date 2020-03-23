---
title: Procházení a změna uspořádání map kódu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e38308c5bb94028fa17e78740da2b0df2779447
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302964"
---
# <a name="browse-and-rearrange-code-maps"></a>Procházení a změna uspořádání map kódu

Změňte uspořádání položek na mapách kódu, aby byly čitelnější a zlepšily jejich výkon.

Mapy kódu můžete přizpůsobit bez ovlivnění základního kódu v řešení. To je užitečné, pokud se chcete zaměřit na klíčové prvky kódu nebo sdělit nápady o kódu. Chcete-li například zvýraznit zajímavé oblasti, můžete vybrat prvky kódu na mapě a filtrovat je, změnit styl prvků kódu a odkazů, skrýt nebo odstranit prvky kódu a uspořádat prvky kódu pomocí vlastností, kategorií nebo skupin.

 **Požadavky**

- Chcete-li vytvořit mapy kódu, musíte mít Visual Studio Enterprise.

- Mapy kódu můžete zobrazit a provádět omezené úpravy map kódu v aplikaci Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a>Začínáme pracovat s mapami kódu

Vytvořte mapu kódu (další podrobnosti [najdete v tématu Mapové závislosti napříč řešeními).](../modeling/map-dependencies-across-your-solutions.md) Pokud nechcete čekat na dokončení generování mapy, klepněte na odkaz **Zrušit** a ukončete proces generování. Pokud to však provedete, neuvidíte podrobnosti o všech závislostech a odkazech.

Po vygenerování mapy můžete začít s těmito tipy pro kontrolu kódu:

- Podívejte se na clustery přirozených závislostí v kódu. Na panelu nástrojů mapy zvolte **Na panelu**](../modeling/media/quickclustersicon.gif)nástrojů Graf tlačítko Rozložení , **Rychlé clustery**![Rychlé clustery . Viz [Změna rozložení mapy](#Selecting).

     ![Graf závislostí &#45; rozložení Rychlých clusterů](../modeling/media/dependencygraph_quickclusters.png)

- Uspořádejte mapu do menších oblastí seskupením souvisejících uzlů. Sbalením těchto skupin zobrazíte pouze závislosti meziskupiny, které se zobrazí automaticky. Viz [Skupinové uzly](#OrganizeGroups).

- Pomocí filtrů můžete zjednodušit mapu a zaměřit se na typy uzlů nebo odkazů, které vás zajímají. Viz [Filtrovat uzly a odkazy](#FilterNodes).

- Maximalizujte výkon velkých map. Další informace najdete [v tématu Mapové závislosti napříč vašimi řešeními.](../modeling/map-dependencies-across-your-solutions.md) Například zapněte **přeskočit sestavení** na panelu nástrojů mapy tak, aby Visual Studio není znovu vytvořit řešení při aktualizaci položek na mapě.

## <a name="change-the-map-layout"></a><a name="Selecting"></a>Změna rozložení mapy

|**Akce**|**Provedení těchto kroků**|
|-|-|
|Uspořádejte tok závislostí pro celou mapu v určitém směru. To vám může pomoci zobrazit architektonické vrstvy v kódu.|Na panelu nástrojů mapy zvolte **Rozložení**a pak:<br /><br /> -   Tlačítko grafu **shora dolů** ![shora dolů](../modeling/media/topbottomgraphbutton.gif)<br />-   **Tlačítko grafu** ![zdola nahoru nahoru](../modeling/media/bottomtopgraphbutton.gif)<br />-   Tlačítko rozložení **Zleva doprava** ![doprava doprava](../modeling/media/leftrightgraphbutton.gif)<br />-   Tlačítko grafu **zprava doleva** ![](../modeling/media/rightleftgraphbutton.gif)|
|Zobrazit clustery přirozených závislostí v kódu s nejvíce závislými uzly ve středu clusterů a nejméně závislými uzly na vnější straně těchto clusterů.|Na panelu nástrojů mapy zvolte **Rozložení**a potom tlačítko Rychlé](../modeling/media/quickclustersicon.gif) **clustery**![Rychlé clustery na panelu nástrojů grafu .|
|Vyberte jeden nebo více uzlů na mapě.|Kliknutím na uzel jej vyberte. Chcete-li vybrat nebo zrušit výběr více uzlů, podržte při klepnutí **klávesu CTRL.**<br /><br /> Klávesnice: Stisknutím **kláves Y TAB** nebo pomocí kláves se šipkami přesuňte tečkovaný obdélník fokusu do uzlu a stisknutím **klávesy SPACE** jej vyberte. Stisknutím **klávesCTRL** + **MEZERA** pro vícenásobné výběr nebo zrušení výběru uzlů.|
|Přesuňte konkrétní uzly na mapě.|Přetažením uzlů je přesuňte. Chcete-li při přetahování uzlů přesunout ostatní uzly a odkazy z cesty, stiskněte a podržte klávesu **SHIFT.**<br /><br /> Klávesnice: podržte **klávesu CTRL** a stiskněte klávesy se šipkami.|
|Změňte rozložení uvnitř skupiny nezávisle na ostatních uzlech a skupinách na mapě.|Vyberte uzel a otevřete místní nabídku. Zvolte **Rozložení** a vyberte styl rozložení.<br /><br /> - nebo -<br /><br /> Vyberte uzel a rozbalte ho, aby se zobrazily podřízené uzly. Kliknutím na název uzlu zobrazte rozbalovací panel nástrojů skupiny a otevřete styl rozložení grafu](../modeling/media/dependencygraph_grouptoolbar.gif) závislostí **skupiny**![&#45; panelu nástrojů skupiny &#45; seznamu rozložení. Vyberte jedno z rozložení stromu, **rychlé clustery**nebo **zobrazení seznamu** (které uspořádá obsah skupiny do seznamu).<br /><br /> Další podrobnosti najdete v [tématu Uzly skupin.](#OrganizeGroups)|
|Vrátit zpět akci v mapě.|Stiskněte **kombinaci kláves CTRL** + **Z** nebo použijte **příkaz** Zpět v sadě Visual Studio.|

## <a name="browse-the-map"></a><a name="Explore"></a>Procházet mapu

|**Akce**|**Provedení těchto kroků**|
|-|-|
|Proskenujte mapu.|Přetáhněte mapu v libovolném směru pomocí myši.<br /><br /> - nebo -<br /><br /> Podržte **klávesu SHIFT** a otočte kolečkem myši, abyste se posouvali vodorovně. Podržte **klávesu SHIFT** + **CTRL** a otočením kolečka myši se posunete vodorovně.|
|Přiblížení nebo oddálení mapy.|Otočte kolečkem myši.<br /><br /> - nebo -<br /><br /> Použijte rozevírací seznam **Lupa** na panelu nástrojů mapy kódu.<br /><br /> - nebo -<br /><br /> Použijte klávesové zkratky. Přiblížení přiblížíte stisknutím **kláves CTRL + SHIFT + .** (tečka). Oddálení oddálíte stisknutím **kombinace kláves CTRL + SHIFT +** (čárka).|
|Přibližte určitou oblast pomocí myši.|Při kreslení obdélníku kolem oblasti, která vás zajímá, podržte pravé tlačítko myši.|
|Změňte velikost a vejde mapu do okna.|Ze seznamu **Lupa** na panelu nástrojů mapy kódu zvolte **Lupa, aby se vešel.**<br /><br /> - nebo -<br /><br /> Klepněte na ikonu ![ **Lupa, aby se ikona** Lupa vešla na panel](../modeling/media/almcodemapzoomicon.png) nástrojů mapy na panelu nástrojů mapy kódu. Klávesnice: stiskněte **kombinaci kláves CTRL + 0** (nula).|
|Najít uzel na mapě podle jeho názvu. **Tip:**  To funguje pouze pro položky na mapě. Chcete-li najít položky v řešení, ale ne na mapě, najděte je v **Průzkumníku řešení**a přetáhněte je na mapu. (Přetáhněte výběr nebo na panelu nástrojů **Průzkumník řešení** klikněte na Zobrazit na **mapě kódu).**|1. Zvolte ![ikonu **Najít** ikonu](../modeling/media/almcodemapfindicon.png) Najít na panelu nástrojů mapy na panelu nástrojů mapy kódu (Klávesnice: stiskněte **kombinaci kláves CTRL + F)** a zobrazte vyhledávací pole v pravém horním rohu mapy.<br />2. Zadejte název položky a stiskněte **return** nebo klikněte na ikonu lupy. Na mapě se zobrazí vybraná první položka, která odpovídá vašemu hledání.<br />3. Chcete-li přizpůsobit vyhledávání, otevřete rozevírací seznam a zvolte možnost hledání. Možnosti jsou **Najít další**, **Najít předchozí**a Vybrat **vše**. Pak klikněte na odpovídající tlačítko vedle vyhledávacího textového pole.<br />     ![Rozevírací seznam možností hledání&#45;](../modeling/media/almcodemapssearchdropdown.png)<br />     Případně použijte klávesnici: stisknutím **klávesy F3** vyberte další odpovídající uzel nebo **SHIFT + F3** a vyberte předchozí odpovídající uzel.<br />4. Vyberte některou z možností, které určují, jak jsou vyhledávací termíny zpracovávány, kliknutím na ikony pod vyhledávacím textovým polem.<br />     ![Možnosti shody hledání](../modeling/media/almcodemapssearchmatchicons.png)<br />     Možnosti jsou, zleva doprava, malá a velká písmena odpovídající, odpovídají pouze celá slova, použijte .NET regulární výraz syntaxe, automaticky rozbalit skupiny zobrazit shody na uzavřené položky. **Důležité:**  Vyhledávací pole můžete použít k vyhledání shod ve sbalených skupinách pouze v případě, že tyto skupiny byly dříve rozbaleny. Chcete-li tyto shody najít a automaticky rozbalit jejich nadřazené skupiny, zvolte tuto možnost pod vyhledávacím polem.|
|Vyberte všechny nevybrané uzly.|Otevřete místní nabídku zvolených uzlů. Zvolte **Vybrat**, **Invertovat výběr**.|
|Vyberte další uzly, které odkazují na vybrané.|Otevřete místní nabídku zvolených uzlů. Zvolte **Vybrat** a jednu z těchto možností:<br /><br /> - Chcete-li vybrat další uzly, které se propojují přímo s vybraným **uzlem,** zvolte Příchozí závislosti .<br />- Chcete-li vybrat další uzly, které propojují přímo z vybraného uzlu, zvolte **Odchozí závislosti**.<br />- Chcete-li vybrat další uzly, které odkazují přímo na a z vybraného uzlu, zvolte **Oba**.<br />- Chcete-li vybrat všechny uzly, které odkazují na vybraný uzel a z ní, zvolte **Připojený podgraf**.<br />- Chcete-li vybrat všechny podřízené položky vybraného uzlu, zvolte **Děti**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a>Filtrování uzlů a odkazů

|**Akce**|**Provedení těchto kroků**|
|-|-|
|Zobrazení nebo skrytí podokna Filtry|Zvolte tlačítko **Filtry** na panelu nástrojů mapy kódu. Podokno **Filtry** se ve výchozím nastavení zobrazuje jako stránka s kartami v **Průzkumníku řešení**.|
|Filtrujte typy uzlů, které jsou zobrazeny na mapě.|Nastavte nebo zrušte zaškrtnutí zaškrtávacích políček v seznamu **Prvky kódu** v podokně Filtry.|
|Filtrujte typy odkazů, které jsou zobrazeny na mapě.|Nastavte nebo zrušte zaškrtnutí políček v seznamu **Relace** v podokně Filtry.|
|Zobrazit nebo skrýt testovací uzly projektu na mapě.|Zaškrtněte políčko **Testovat datové zdroje** v seznamu Různé v podokně **Filtry.**|

Ikony zobrazené v panelu Legenda na mapě odrážejí nastavení, která provedete v seznamu. Chcete-li zobrazit nebo skrýt panel Legenda, klepněte na tlačítko **Legenda** na panelu nástrojů mapy kódu.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a>Zkontrolujte uzly a odkazy

Kód mapy ukazují tyto druhy odkazů:

- Jednotlivé propojení představuje jeden vztah mezi dvěma uzly.

- Propojení mezi skupinami představuje vztah mezi dvěma uzly v různých skupinách.

- Agregační propojení představuje všechny vztahy, které ukazují ve stejném směru mezi dvěma skupinami.

> [!TIP]
> Ve výchozím nastavení mapa zobrazuje odkazy mezi skupinami pouze pro vybrané uzly. Chcete-li toto chování změnit tak, aby se zobrazila nebo skryla agregovaná propojení mezi skupinami, klepněte na **tlačítko Rozložení** na panelu nástrojů mapy kódu a zvolte **Upřesnit**, potom **zobrazit všechny odkazy mezi skupinami** nebo **Skrýt všechny odkazy mezi skupinami**. Další podrobnosti najdete v tématu [Skrytí nebo zobrazení uzlů a odkazů.](#HidingShowing)

|**Akce**|**Provedení těchto kroků**|
|-|-|
|Další informace o uzlu nebo odkazu.|Přesuňte ukazatel myši nad uzel nebo odkaz, dokud se nezobrazí popisek.<br /><br /> Popispro agregovaný odkaz uvádí jednotlivé závislosti, které představuje.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku uzlu nebo odkazu. Zvolte **Upravit**, **Vlastnosti**.|
|Zobrazení nebo skrytí obsahu skupiny.|- Chcete-li rozbalit skupinu, otevřete místní nabídku uzlu a zvolte **Skupina**, **Rozbalit**.<br />     - nebo -<br />     Přesuňte ukazatel myši nad uzel, dokud se nezobrazí dvojité šipka (šipka dolů). Klepnutím na toto tlačítko rozbalte skupinu. Klávesnice: Chcete-li vybranou skupinu **PLUS** rozbalit**+** nebo sbalit, stiskněte klávesu PLUS ( ) nebo klávesu **MINUS** (**-**).<br />- Chcete-li sbalit skupinu, otevřete místní nabídku uzlu a zvolte **Skupinu**, **Sbalit**.<br />     - nebo -<br />     Přesuňte ukazatel myši nad skupinu, dokud se nezobrazí dvojité šipka (šipka nahoru). Klepnutím na toto tlačítko sbalíte skupinu.<br />- Chcete-li rozbalit všechny skupiny, stisknutím **klávesctrl** + **a** vyberte všechny uzly. Otevřete místní nabídku mapy a zvolte **Skupina**, **Rozbalit**. **Poznámka:**      Tento příkaz není k dispozici, pokud rozbalení všech skupin generuje nepoužitelnou mapu nebo problémy s pamětí. Doporučujeme rozšířit mapu pouze na úroveň podrobností, na které vám záleží.<br />- Chcete-li sbalit všechny skupiny, otevřete místní nabídku pro uzel nebo pro mapu. Zvolte **Skupina**, **Sbalit vše**.|
|Podívejte se na definici kódu pro obor názvů, typ nebo člen.|Otevřete místní nabídku uzlu a zvolte **Přejít na definici**.<br /><br /> -nebo-<br /><br /> Poklepejte na uzel. U rozbalených skupin poklikejte na záhlaví skupiny.<br /><br /> -nebo-<br /><br /> Vyberte uzel a stiskněte **klávesu F12**.<br /><br /> Například:<br /><br /> - Pro obor názvů obsahující jednu třídu se otevře soubor kódu pro třídu, který zobrazí definici této třídy. V ostatních případech se v okně **Výsledky hledání symbolů** zobrazí seznam souborů kódu. **Poznámka:**      Pokud provedete tuto úlohu v oboru názvů jazyka Visual Basic, soubor kódu za oborem názvů se neotevře. K tomuto problému dochází také při provádění tohoto úkolu na skupině vybraných uzlů, které obsahují obor názvů jazyka Visual Basic. Chcete-li tento problém vyřešit, projděte ručně soubor kódu za oborem názvů nebo vynechat uzel pro obor názvů z vašeho výběru.<br />- Pro třídu nebo částečnou třídu se otevře soubor kódu pro tuto třídu, který zobrazí definici třídy.<br />- Pro metodu se otevře soubor kódu pro nadřazenou třídu, aby se zobrazila definice metody.|
|Prozkoumejte závislosti a položky, které se účastní agregační propojení.|Vyberte odkazy, které vás zajímají, a otevřete místní nabídku pro váš výběr. V nové mapě kódu zvolte **Zobrazit přispívající odkazy** nebo **Zobrazit přispívající odkazy**.<br /><br /> Visual Studio rozbalí skupiny na obou koncích spojení a zobrazí pouze položky a závislosti, které se účastní odkazu. **Poznámka:**  Při kontrole závislostí mezi položkami v částečných skupinách se může zobrazit toto chování: <ul><li>Odkazy na položky, které se neúčastní vašeho vyšetření, zmizí z mapy, i když tyto odkazy stále existují.</li><li>Předpokládejme, že prozkoumáte odkaz na položku v částečné skupině a později prozkoumáte jiný odkaz na stejnou položku. Během druhé zkoušky cílová částečná skupina zobrazuje pouze položky z první zkoušky. Odkazy a cílové položky, které se nezúčastnily vaší první zkoušky, ale účastnily se druhé zkoušky, se nezobrazují.</li></ul> Chcete-li zobrazit chybějící položky ze skupiny, zvolte **Znovu načíst ikonu dětí**![znovu načíst děti](../modeling/media/dependencygraph_deletednodesicon.png) (což znamená, že ne všichni členové skupiny se zobrazí na mapě). Můžete také zkusit vrátit zpět své akce (Klávesnice: stiskněte **kombinaci kláves CTRL+Z**) a prozkoumat závislosti na nové mapě.|
|Prozkoumejte závislosti napříč více uzly v různých skupinách.|Rozbalte skupiny, abyste viděli všechny jejich děti. Vyberte všechny uzly, které vás zajímají, včetně jejich podřízených. Mapa zobrazuje propojení mezi skupinami mezi vybranými uzly.<br /><br /> Chcete-li vybrat všechny uzly ve skupině, stiskněte a podržte **klávesu SHIFT** a levé tlačítko myši při kreslení obdélníku kolem této skupiny. Chcete-li vybrat všechny uzly na mapě, stiskněte **kombinaci kláves CTRL**+**A**. **Tip:**  Chcete-li odkazy mezi skupinami zobrazovat vždy, zvolte **Rozložení** na panelu nástrojů **mapy, Upřesnit**, **Zobrazit odkazy mezi skupinami**.|
|Podívejte se na položky, na které odkazuje uzel nebo odkaz.|Otevřete místní nabídku uzlu a zvolte **Najít všechny reference**. **Poznámka:**  To platí pouze `Reference` v případě, že je atribut nastaven pro uzel nebo odkaz v souboru .dgml mapy. Informace o přidání odkazů na položky z uzlů nebo odkazů naleznete v [tématu Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a>Skrytí nebo zobrazení uzlů a odkazů

Skrytí uzlů umožňuje vynechat tyto uzly při použití algoritmů rozložení. Ve výchozím nastavení jsou propojení mezi skupinami skryta. Propojení mezi skupinami jsou jednotlivá propojení, která spojují uzly mezi skupinami. Při sbalení skupin y agreguje mapa všechna propojení mezi skupinami do jednotlivých propojení mezi skupinami. Pokud skupinu rozbalíte a vyberete v ní uzly, zobrazí se propojení mezi skupinami, která znázorňují závislosti v této skupině.

> [!CAUTION]
> Před sdílením mapy, která byla vytvořena v sadě Visual Studio Enterprise s těmi, kteří používají Visual Studio Professional, nezapomeňte zobrazit všechny uzly nebo odkazy mezi skupinami, které chcete ostatní zobrazit. V opačném případě uživatelé nebudou moci tyto položky zobrazit.

### <a name="to-hide-or-show-nodes"></a>Skrytí nebo zobrazení uzlů

|**Akce**|**Provedení těchto kroků**|
|-|-|
|Skrýt vybrané uzly|1. Vyberte uzly, které chcete skrýt.<br />2. Otevřete místní nabídku pro vybrané uzly nebo pro mapu. Zvolte **Vybrat**, **Skrýt vybrané**.|
|Skrýt nevybrané uzly.|1. Vyberte uzly, které chcete zůstat viditelné.<br />2. Otevřete místní nabídku pro vybrané uzly nebo pro mapu. Zvolte **Vybrat**, **Skrýt nevybranou**.|
|Zobrazí skryté uzly.|- Chcete-li zobrazit všechny skryté uzly uvnitř skupiny, nejprve se ujistěte, že je skupina rozbalena. Otevřete místní nabídku a zvolte **Vybrat**, **Zobrazit děti**.<br />     - nebo -<br />     V **Unhide Children**![levém horním rohu skupiny klikněte na ikonu Zobrazit podřízené](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) děti (tato ikona je viditelná pouze v případě, že jsou skryté podřízené uzly).<br />- Chcete-li zobrazit všechny skryté uzly, otevřete místní nabídku mapy nebo uzlu a zvolte **Vybrat**, **Zobrazit vše**.|

### <a name="to-hide-or-show-links"></a>Skrytí nebo zobrazení odkazů

|**Akce**|**Na panelu nástrojů mapy zvolte Rozložení, Upřesnit a pak zvolte**|
|-|-|
|Vždy zobrazovat odkazy mezi skupinami.|**Zobrazit všechny odkazy mezi skupinami**. Tím budou skryta souhrnná propojení mezi skupinami.|
|Vždy skryjte odkazy mezi skupinami.|**Skrýt všechny odkazy mezi skupinami**|
|Zobrazí pouze odkazy mezi skupinami pro vybrané uzly.|**Zobrazit odkazy mezi skupinami na vybraných uzlech**|
|Skryjte všechny odkazy.|**Skrýt všechny odkazy**. Chcete-li odkazy zobrazit znovu, zvolte jednu z výše uvedených možností.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a>Skupinové uzly

|**Akce**|**Provedení těchto kroků**|
|-|-|
|Zobrazí uzly kontejneru jako uzly skupiny nebo uzly listů.|Chcete-li zobrazit uzly kontejnerů jako uzly na list: vyberte uzly, otevřete místní nabídku pro váš výběr a zvolte **Seskupit**, **Převést na list**.<br /><br /> Chcete-li zobrazit uzly kontejnerů jako uzly skupin: vyberte uzly, otevřete místní nabídku pro váš výběr a zvolte **Seskupit**, **Převést na skupinu**.|
|Změňte rozložení uvnitř skupiny.|Vyberte skupinu, otevřete místní nabídku, zvolte **Rozložení**a vyberte požadovaný styl rozvržení.<br /><br /> - nebo -<br /><br /> 1. Vyberte skupinu a ujistěte se, že je rozbalena.<br />2. Znovu klikněte na záhlaví skupiny a zobrazí se panel nástrojů skupiny.<br />     ![Panel nástrojů &#45; skupiny grafů závislostí](../modeling/media/dependencygraph_group.png)<br />3. Otevřete **styl rozložení grafu** ![závislostí seznamu skupin &#45;](../modeling/media/dependencygraph_grouptoolbar.gif) panelu nástrojů skupiny &#45; rozložení a zvolte požadovaný styl rozložení.<br /><br /> **Zobrazení seznamu** změní uspořádání členů skupiny do seznamu. **Výchozí graf** obnoví rozložení skupiny na výchozí rozložení mapy. Další možnosti najdete [v tématu Změna rozložení mapy](#Selecting).|
|Přidejte uzel do skupiny.|Přetáhněte uzel do skupiny.<br /><br /> Při přetahování uzlu visual studio zobrazí indikátor, který ukazuje, že uzel přesouváte.<br /><br /> Uzly lze přetáhnout také mimo skupinu.|
|Přidejte uzel do uzlu, který není skupinovým.|Přetáhněte uzel na cílový uzel. Libovolný cílový uzel můžete převést na skupinu přidáním uzlů.|
|Seskupit vybrané uzly.|1. Vyberte uzly, které chcete seskupit. Nad posledním vybraným uznem se zobrazí rozbalovací panel nástrojů.<br />     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)<br />2. Na panelu nástrojů zvolte čtvrtou ikonu **Seskupí vybrané uzly** (pokud je uzel rozbalen, bude mít pět místo čtyř ikon). Zadejte název nové skupiny a stiskněte **Return**.<br />     - nebo -<br />     Vyberte uzly, které chcete seskupit, a otevřete místní nabídku pro váš výběr. Zvolte **Skupina**, **Přidat nadřazenou skupinu**, zadejte název nové skupiny a stiskněte **Return**.<br /><br /> Skupinu můžete přejmenovat. Otevřete místní nabídku skupiny a zvolte **Upravit**, **Vlastnosti** otevřete okno Vlastnosti sady Visual Studio. Ve vlastnosti **Label** přejmenujte skupinu podle potřeby.|
|Odeberte skupiny.|Vyberte skupinu nebo skupiny, které mají být odstraněny. Otevřete místní nabídku pro výběr a zvolte **Skupina**, **Odebrat skupinu**.|
|Odeberte uzly z jejich nadřazené skupiny.|Vyberte uzly, které mají být odebrány. Otevřete místní nabídku pro výběr a zvolte **Skupina**, **Odebrat z nadřazené položky**. Tím odeberete uzly až do jejich prarodiče nebo mimo skupinu, pokud nemají žádnou skupinu prarodičů.<br /><br /> - nebo -<br /><br /> Vyberte uzly a přetáhněte je ze skupiny.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a>Přidání, odebrání nebo přejmenování uzlů, odkazů a komentářů

Můžete zobrazit více nebo méně položek na mapě, abyste mohli přejít k podrobnostem nebo zjednodušit mapu. Můžete také přejmenovat položky a přidat komentáře k položkám.

> [!CAUTION]
> Před sdílením mapy, která byla vytvořena pomocí sady Visual Studio Enterprise s těmi, kteří používají Visual Professional, ujistěte se, že všechny prvky kódu, které chcete, aby ostatní viděli, jsou viditelné na mapě. V opačném případě tito uživatelé nebudou moci načíst odstraněné prvky kódu.

### <a name="add-a-node-for-a-code-element"></a>Přidání uzlu pro prvek kódu

|**Akce**|**Provedení těchto kroků**|
|-|-|
|Přidejte nový obecný uzel v aktuálním umístění ukazatele myši.|1. Přesuňte ukazatel myši na místo na mapě, kam chcete umístit nový prvek kódu, a stiskněte **tlačítko Vložit**.<br />     - nebo -<br />     Otevřete místní nabídku mapy a zvolte **Upravit**, **Přidat** **obecný uzel**.<br />2. Zadejte název nového uzlu a stiskněte **return**.|
|Přidejte určitý typ uzlu elementu kódu v aktuálním umístění ukazatele myši.|1. Přesuňte ukazatel myši na místo na mapě, kam chcete umístit nový prvek kódu, a otevřete místní nabídku mapy.<br />2. Zvolte **Upravit**, **Přidat**a vyberte požadovaný typ uzlu.<br />3. Zadejte název nového uzlu a stiskněte **return**.|
|Přidejte do skupiny obecný nebo určitý typ uzlu elementu kódu.|1. Vyberte uzel skupiny a otevřete místní nabídku.<br />2. Zvolte **Upravit**, **Přidat**a vyberte požadovaný typ uzlu.<br />3. Zadejte název nového uzlu a stiskněte **return**.|
|Přidejte nový uzel stejného typu a propojený z existujícího uzlu.|1. Vyberte prvek kódu. Nad ním se zobrazí rozbalovací panel nástrojů.<br />     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)<br />2. Na panelu nástrojů zvolte druhou ikonu **Vytvořte uzel se stejnou kategorií jako tento uzel a přidejte k němu nový odkaz**.<br />3. Vyberte místo na mapě, aby nový prvek kódu a klikněte na levé tlačítko myši.<br />4. Zadejte název nového uzlu a stiskněte **return**.|
|Přidejte nový obecný uzel, který je propojen z existujícího prvku kódu, který má fokus.|1. Pomocí klávesnice stiskněte **klávesu Tab,** dokud prvek kódu, ze kterýchcete vytvořit odkaz, nebude mít fokus (tečkovaný obdélník).<br />2. Stiskněte **klávesu Alt**+**Insert**.<br />3. Zadejte název nového uzlu a stiskněte **return**.|
|Přidejte nový obecný uzel, který odkazuje na existující prvek kódu, který má fokus.|1. Pomocí klávesnice stiskněte **klávesu Tab,** dokud prvek kódu, na který chcete vytvořit odkaz, nebude mít fokus (tečkovaný obdélník).<br />2. Stiskněte **klávesu Alt**+**Shift**+**Insert**.<br />3. Zadejte název nového uzlu a stiskněte **return**.|

|**Přidání prvků kódu pro**|**Provedení těchto kroků**|
|-|-|
|Prvky kódu v řešení.|1. Najděte prvek kódu v **Průzkumníku řešení**. Použijte vyhledávací pole **Průzkumníka řešení** nebo projděte řešení. **Tip:**      Chcete-li najít prvky kódu, které mají závislosti na typu nebo členu, otevřete místní nabídku pro typ nebo člena v **Průzkumníku řešení**. Vyberte vztah, který vás zajímá. **Průzkumník řešení** zobrazuje pouze ty prvky kódu se zadanými závislostmi.<br />2. Přetáhněte prvky kódu, které vás zajímají, na povrch mapy. Můžete také přetáhnout prvky kódu ze zobrazení tříd nebo prohlížeče objektů.<br />     - nebo -<br />     V **Průzkumníku řešení**vyberte prvky kódu, které chcete mapovat. Potom na panelu nástrojů **Průzkumník řešení** klikněte na Zobrazit na **mapě kódu**.<br /><br /> Ve výchozím nastavení je na mapě zobrazena nadřazená hierarchie kontejnerů pro nové prvky kódu. Toto chování můžete změnit pomocí tlačítka **Zahrnout rodiče** na panelu nástrojů mapy kódu. Když je vypnutý, do mapy se přidá pouze samotný prvek kódu. Chcete-li toto chování zvrátit pouze pro jednu akci přetažení, stiskněte a podržte klávesu **CTRL** při přetahování prvků kódu na mapu.<br /><br /> Visual Studio přidá prvky kódu pro prvky kódu nejvyšší úrovně ve vašem výběru. Chcete-li zjistit, zda prvek kódu obsahuje další prvky kódu, přesuňte ukazatel myši nad element kódu tak, aby se zobrazila dvojitá šipka (šipka dolů). Zvolte dvojitou šipku pro rozšíření prvku kódu. Chcete-li rozbalit všechny prvky kódu, stisknutím **klávesctrl**+**a** vyberte všechny prvky, otevřete místní nabídku mapy a zvolte **Skupina**, **Rozbalit**. Tento příkaz není k dispozici, pokud by rozbalení všech skupin vytvořilo nepoužitelnou mapu nebo způsobilo nedostatek problémů s pamětí.|
|Prvky kódu související s prvky kódu na mapě.|Klepněte na tlačítko **Zobrazit související** na panelu nástrojů mapy kódu a zvolte typ souvisejících položek, které vás zajímají.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro prvek kódu. Vyberte si jednu z **položek Show ...** v nabídce v závislosti na druhu vztahu, který vás zajímá. Můžete například zobrazit položky, na které odkazuje aktuální položka, položky, které odkazují na aktuální položku, základní a odvozené typy pro třídy, volající metody a obsahující třídy, obory názvů a sestavení.<br /><br /> Další podrobnosti naleznete v [tomto tématu](../modeling/map-dependencies-across-your-solutions.md).|
|Kompilovaná sestavení .NET (.dll nebo .exe) nebo binární soubory.|Přetáhněte sestavení nebo binární soubory z mimo Visual Studio na mapu.<br /><br /> Z Průzkumníka Windows nebo Průzkumníka souborů můžete trvat pouze v případě, že jej používáte, a sady Visual Studio na stejné úrovni oprávnění řízení přístupu uživatelů (UAC). Pokud je například funkce Řízení přístupu zapnuto a používáte visual studio jako správce, průzkumník Windows nebo Průzkumník souborů zablokují operaci přetažení.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Přidání propojení mezi existujícími prvky kódu

1. Vyberte prvek zdrojového kódu. Nad elementem kódu se zobrazí panel nástrojů.

    ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2. Na panelu nástrojů zvolte první ikonu, **Vytvořit nový odkaz z tohoto uzlu, na který uzel, na který kliknete na další**.

3. Vyberte prvek cílového kódu. Zobrazí se propojení mezi dvěma prvky kódu.

**Nebo**

1. Vyberte prvek zdrojového kódu na mapě.

2. Pokud máte nainstalovanou myš, přesuňte ukazatel myši mimo hranice mapy.

3. Otevřete místní nabídku prvku kódu a zvolte **Upravit** > **přidat** > **obecný odkaz**.

4. Tabulátorem a vyberte prvek cílového kódu pro propojení.

5. Stiskněte **Enter**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Přidání komentáře k existujícímu uzlu na mapě

1. Vyberte prvek kódu. Nad ním se zobrazí panel nástrojů.

     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2. Na panelu nástrojů zvolte třetí **ikonu, Vytvořte nový uzel komentáře s novým odkazem na vybraný uzel**.

     \-nebo -

     Otevřete místní nabídku elementu kódu a zvolte **Upravit** > **nový komentář**.

3. Zadejte komentáře. Chcete-li psát na nový řádek, stiskněte **shift** + **enter**.

#### <a name="add-a-comment-to-the-map-itself"></a>Přidání komentáře k samotné mapě

1. Otevřete místní nabídku mapy a zvolte **Upravit** > **nový komentář**.

2. Zadejte komentáře. Chcete-li psát na nový řádek, stiskněte **shift** + **enter**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Přejmenování prvku kódu nebo odkazu

1. Vyberte prvek kódu nebo odkaz, který chcete přejmenovat.

2. Stiskněte **klávesu F2**nebo otevřete místní nabídku a zvolte **Upravit** > **přejmenování**.

3. Když se v mapě objeví textové pole, přejmenujte prvek kódu nebo odkaz.

**Nebo**

1. Otevřete místní nabídku a zvolte **Upravit** > **vlastnosti**.

2. Upravte vlastnost **Label** v okně Vlastnosti sady Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Odebrání prvku kódu nebo odkazu z mapy

1. Vyberte prvek kódu nebo odkaz a stiskněte klávesu **Delete.**

     \-nebo -

     Otevřete místní nabídku elementu kódu nebo odkazu a zvolte **Upravit** > **odebrat**.

2. Pokud je prvek nebo odkaz součástí skupiny, ![zobrazí se](../modeling/media/dependencygraph_deletednodesicon.png) uvnitř skupiny tlačítko **Znovu načíst podřízené** objekty. Klepnutím na toto tlačítko načtete chybějící prvky a odkazy.

- Prvky kódu a odkazy můžete odebrat z mapy bez ovlivnění základního kódu. Když je odstraníte, jejich definice jsou odebrány ze souboru DGML (.dgml).

- Mapy vytvořené úpravou DGML, přidáním nedefinovaných prvků kódu nebo pomocí některých dřívějších verzí sady Visual Studio tuto funkci nepodporují.

#### <a name="flag-a-code-element-for-follow-up"></a>Označení prvku kódu příznakem pro zpracování

1. Vyberte prvek kódu nebo odkaz, který chcete označit příznakem pro zpracování.

2. Otevřete místní nabídku a zvolte **Upravit** > **příznak pro zpracování**.

- Ve výchozím nastavení získá prvek kódu červené pozadí. Zvažte [přidání komentáře](#AddComments) s příslušnými informacemi o následných opatřeních.

- Změňte barvu pozadí prvku nebo zrušte zaškrtnutí příznaku zpracování výběrem **možnosti Upravit** > **jiné barvy příznaku**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a>Změna stylu prvku kódu nebo odkazu

Ikony prvků kódu a barvy prvků kódu a odkazů můžete změnit pomocí předdefinovaných ikon a barev. Můžete například zvolit barvu pro zvýraznění prvků kódu a odkazů, které mají určitou kategorii nebo vlastnost. To vám umožní identifikovat a zaměřit se na konkrétní oblasti mapy. Vlastní ikony a barvy můžete určit úpravou souboru DGML mapy. viz [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Použití předdefinované barvy nebo ikony na prvky kódu nebo odkazy s určitou kategorií nebo vlastností

1. Na panelu nástrojů mapy zvolte **Legenda**.

2. V poli **Legenda** zjistěte, jestli se kategorie nebo vlastnost prvku kódu již v seznamu zobrazuje.

3. Pokud seznam neobsahuje kategorii nebo vlastnost, **+** zvolte v poli **Legenda** a pak zvolte **Vlastnost uzlu**, **Kategorie uzlu**, **Vlastnost propojení**nebo Kategorie **propojení**. Pak zvolte vlastnost nebo kategorii. Kategorie nebo vlastnost se nyní zobrazí v poli **Legenda.**

    > [!NOTE]
    > Chcete-li vytvořit a přiřadit prvek kódu kategorii nebo vlastnost, můžete upravit soubor .dgml mapy. viz [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. V poli **Legenda** klikněte na ikonu vedle kategorie nebo vlastnosti, kterou jste přidali nebo chcete změnit.

5. Pro výběr stylu, který chcete změnit, použijte následující tabulku:

    |**Chcete-li změnit**|**Pomocí volby**|
    |-|-|
    |Barvu pozadí|**Pozadí**|
    |Barva obrysu|**Tahu**|
    |Barva textu (zobrazí se písmeno "f" pro zobrazení výsledku)|**Popředí**|
    |Ikona|**Ikony**|

     Zobrazí se dialogové okno **Výběr sady barev** nebo Sady **ikon,** ve které můžete vybrat barvu nebo ikonu.

6. V dialogovém okně **Výběr sady barev** nebo Sady **ikon** proveďte jeden z následujících akcí:

    |**Chcete-li použít**|**Provedení těchto kroků**|
    |-|-|
    |Sada barev nebo ikon|Otevřete seznam select **color** (nebo **icon).** **set** Vyberte sadu barev nebo ikon.|
    |Určitá barva nebo ikona|Otevřete seznam hodnot kategorií nebo vlastností. Vyberte barvu nebo ikonu.|

    > [!NOTE]
    > V poli **Legenda** můžete změnit uspořádání, odstranit nebo dočasně deaktivovat styly. Viz [Pole Upravit legendu](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a>Upravit pole Legenda

Styly můžete změnit, odstranit nebo dočasně deaktivovat v poli **Legenda:**

1. Otevřete místní nabídku pro styl v poli **Legenda.**

2. Proveďte některou z následujících úloh:

    |**Akce**|**Pomocí volby**|
    |-|-|
    |Deaktivace prvku kódu|**Zakázat**|
    |Odstranění prvku kódu|**Odstranit**|
    |Přesunutí stylu nahoru|**Přesunout nahoru**|
    |Přesunutí prvku kódu dolů|**Přesunout dolů**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a>Kopírování stylů z jedné mapy do druhé

1. Ujistěte se, že se na zdrojové mapě zobrazí pole **Legenda.** Pokud není viditelná, klepněte na panelu nástrojů mapy na **položku Legenda**.

2. Otevřete místní nabídku pro pole **Legenda.** Zvolte **Kopírovat legendu**.

3. Vložte legendu do cílové mapy.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a>Sloučit mapy kódu

Mapy můžete sloučit zkopírováním a vložením prvků kódu mezi mapy. Pokud se shodovat s identifikátory prvků kódu, potom vložení prvků kódu funguje jako operace sloučení. Chcete-li tento úkol usnadnit, vložte všechna sestavení nebo binární soubory, které chcete vizualizovat, do stejné složky tak, aby úplná cesta každé sestavení nebo binární je stejná pro každou mapu, kterou chcete sloučit.

Případně můžete přetáhnout tato sestavení nebo binární soubory na stejnou mapu z této složky.

## <a name="see-also"></a>Viz také

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Referenční dokumentace jazyka přímého značení grafů (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
