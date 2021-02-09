---
title: Procházení a změna uspořádání map kódu
description: Přečtěte si, jak můžete změnit uspořádání položek v mapách kódu, aby bylo snazší je číst a zlepšovat jejich výkon.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e579f62c24795ad99939fe10f68c42acaaa89b60
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861931"
---
# <a name="browse-and-rearrange-code-maps"></a>Procházení a změna uspořádání map kódu

Změna uspořádání položek v mapách kódu pro snazší čtení a zlepšení výkonu.

Mapy kódu můžete přizpůsobit bez vlivu na podkladový kód v řešení. To je užitečné, pokud se chcete zaměřit na prvky kódu klíče nebo sdělit nápady týkající se kódu. Například pro zdůraznění zajímavých oblastí můžete vybrat prvky kódu na mapě a filtrovat je, změnit styl prvků kódu a odkazy, skrýt nebo odstranit prvky kódu a uspořádat prvky kódu pomocí vlastností, kategorií nebo skupin.

 **Požadavky**

- Chcete-li vytvořit mapy kódu, je nutné mít Visual Studio Enterprise.

- Můžete zobrazit mapy kódu a provádět omezené úpravy map kódu v Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Začínáme pracovat s mapami kódu

Vytvořte mapu kódu (další podrobnosti najdete v tématu [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md) ). Pokud nechcete čekat na dokončení generování mapy, kliknutím na odkaz **Zrušit** můžete zastavit proces generování. Pokud to uděláte, nezobrazí se podrobnosti o všech závislostech a odkazech.

Po vygenerování mapy začněte s těmito tipy pro kontrolu vašeho kódu:

- Podívejte se na clustery s přirozenými závislostmi v kódu. Na panelu nástrojů Mapa klikněte na tlačítko rozložení **, rychlé clustery** ![ rychlé clustery na panelu nástrojů grafu ](../modeling/media/quickclustersicon.gif) . Viz [Změna rozložení mapy](#Selecting).

     ![Graf závislosti &#45; rozložení pro rychlé clustery](../modeling/media/dependencygraph_quickclusters.png)

- Uspořádejte mapu do menších oblastí seskupením souvisejících uzlů. Sbalením těchto skupin zobrazíte pouze závislosti mezi skupinami, které se zobrazí automaticky. Viz [uzel skupiny](#OrganizeGroups).

- Pomocí filtrů můžete zjednodušit mapu a soustředit se na typy uzlů nebo odkazy, které vás zajímají. Viz téma [filtrování uzlů a propojení](#FilterNodes).

- Maximalizujte výkon velkých map. Další informace najdete v tématu [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md) . Například na panelu nástrojů mapa zapněte položku **Přeskočit sestavení** tak, aby aplikace Visual Studio při aktualizaci položek na mapě znovu sestavila vaše řešení.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Změna rozložení mapy

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Uspořádat tok závislostí pro celou mapu v určitém směru. To vám může pomáhat při zobrazení vrstev architektury v kódu.|Na panelu nástrojů mapa zvolte **rozložení** a pak:<br /><br /> -   **Shora dolů** ![ Tlačítko shora dolů v grafu](../modeling/media/topbottomgraphbutton.gif)<br />-   **Zdola nahoru** ![ Tlačítko dolních horních a horních grafů](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Zleva doprava** ![ Tlačítko pro rozložení zleva doprava](../modeling/media/leftrightgraphbutton.gif)<br />-   **Zprava doleva** ![ Tlačítko vlevo od levého grafu](../modeling/media/rightleftgraphbutton.gif)|
|Seznamte se s clustery s přirozenými závislostmi v kódu s nejvíce závislými uzly uprostřed clusterů a nejméně závislými uzly mimo tyto clustery.|Na panelu nástrojů Mapa klikněte na tlačítko **rozložení** **a rychlé clustery** ![ rychlé clustery na panelu nástrojů grafu ](../modeling/media/quickclustersicon.gif) .|
|Vyberte jeden nebo více uzlů na mapě.|Kliknutím vyberte uzel. Pokud chcete vybrat nebo zrušit výběr více než jednoho uzlu, podržte při kliknutí **klávesu CTRL** .<br /><br /> Klávesnice: stiskněte klávesu **TAB** nebo pomocí kláves se šipkami přesuňte obdélník pro výběr s tečkami na uzel a stisknutím **mezerníku** ho vyberte. Stiskněte **CTRL +**  +  **MEZERNÍK** pro vícenásobný výběr nebo zrušte výběr uzlů.|
|Přesuňte konkrétní uzly kolem mapy.|Přetažením uzlů je přesuňte. Chcete-li přesunout jiné uzly a odkazy ze způsobu přetahování uzlů, stiskněte a podržte klávesu **SHIFT** .<br /><br /> Klávesnice: stiskněte **klávesu CTRL** a stiskněte klávesy se šipkami.|
|Změna rozložení v rámci skupiny nezávisle na ostatních uzlech a skupinách na mapě.|Vyberte uzel a otevřete místní nabídku. Zvolte **rozložení** a vyberte styl rozložení.<br /><br /> - nebo -<br /><br /> Vyberte uzel a rozbalte ho pro zobrazení podřízených uzlů. Kliknutím na název uzlu zobrazíte místní panel nástrojů pro skupinu a otevřete okno **změnit styl rozložení** ![ grafu závislostí skupiny &#45; panelu nástrojů skupiny &#45; ](../modeling/media/dependencygraph_grouptoolbar.gif) seznamu rozložení. Vyberte jedno z rozložení stromové struktury, **rychlé clustery** nebo **zobrazení seznamu** (které uspořádá obsah skupiny do seznamu).<br /><br /> Další podrobnosti najdete v tématu [skupiny uzlů](#OrganizeGroups) .|
|Zruší akci na mapě.|Stiskněte klávesu **CTRL**  +  **Z** nebo použijte příkaz pro **vrácení zpět** sady Visual Studio.|

## <a name="browse-the-map"></a><a name="Explore"></a> Procházet mapu

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Naskenujte mapu.|Přetáhněte mapu v libovolném směru pomocí myši.<br /><br /> - nebo -<br /><br /> Podržením **klávesy SHIFT** a otočením kolečka myši se posuňte vodorovně. Podržte stisknutou klávesu **SHIFT**  +   a otáčejte kolečkem myši, aby se posouvají vodorovně.|
|Přiblížení nebo oddálení mapy.|Otočení kolečka myši<br /><br /> - nebo -<br /><br /> Použijte rozevírací seznam **Lupa** na panelu nástrojů mapa kódu.<br /><br /> - nebo -<br /><br /> Použijte klávesové zkratky. Přiblížíte se stisknutím **kombinace kláves CTRL + SHIFT +.** (tečka). Chcete-li zmenšit, stiskněte klávesy **CTRL + SHIFT +,** (čárka).|
|Přiblížení konkrétní oblasti pomocí myši|Držte pravé tlačítko myši při kreslení obdélníku kolem oblasti, které vás zajímá.|
|Změňte velikost a přizpůsobte mapu do svého okna.|Vyberte možnost **přizpůsobit tak, aby se vešla** do seznamu **zvětšení** na panelu nástrojů mapa kódu.<br /><br /> - nebo -<br /><br /> Na panelu nástrojů mapa na panelu nástrojů mapa kódu klikněte na ikonu **přiblížení, aby se přizpůsobila** ikona ![ lupy ](../modeling/media/almcodemapzoomicon.png) . Klávesnice: stiskněte **kombinaci kláves CTRL + 0** (nula).|
|Vyhledejte uzel na mapě podle jeho názvu. **Tip:**  To funguje pouze pro položky na mapě. Pokud chcete najít položky ve vašem řešení, ale ne na mapě, Najděte je v **Průzkumník řešení** a pak je přetáhněte na mapu. (Přetáhněte výběr nebo na panelu nástrojů **Průzkumník řešení** klikněte na tlačítko **Zobrazit na mapě kódu**).|1. v pravém  ![ horním rohu mapy zvolte ikonu hledání ikony najít na panelu nástrojů mapa ](../modeling/media/almcodemapfindicon.png) kódu (klávesnice: stiskněte klávesy **CTRL + F**).<br />2. Zadejte název položky a stiskněte **ENTER** nebo klikněte na ikonu Lupa. Na mapě se zobrazí první položka, která odpovídá vašemu hledání.<br />3. Pokud chcete hledání přizpůsobit, otevřete rozevírací seznam a vyberte možnost hledání. Možnosti najdete na stránce **Další**, **Najít předchozí** a **Vybrat vše**. Pak klikněte na příslušné tlačítko vedle textového pole hledání.<br />     ![&#45;rozevírací seznam a možnosti hledání](../modeling/media/almcodemapssearchdropdown.png)<br />     Alternativně použijte klávesnici: stisknutím klávesy **F3** vyberte další vyhovující uzel nebo **SHIFT + F3** a vyberte předchozí vyhovující uzel.<br />4. Vyberte jednu z možností, které určují, jak se budou zpracovávat hledané výrazy, kliknutím na ikony pod textovým polem hledání.<br />     ![Možnosti hledání shody](../modeling/media/almcodemapssearchmatchicons.png)<br />     Možnosti jsou zleva doprava, porovnávání malých a velkých písmen, pouze celá slova, používají syntaxi regulárního výrazu .NET, automaticky rozbalí skupiny, aby se zobrazily shody s uzavřenými položkami. **Důležité informace:**  Pomocí vyhledávacího pole můžete vyhledat shody ve sbalených skupinách pouze v případě, že byly tyto skupiny rozbaleny dříve. Chcete-li najít tyto shody a rozbalit své nadřazené skupiny automaticky, vyberte tuto možnost pod vyhledávacím polem.|
|Vyberte všechny nevybrané uzly.|Otevřete místní nabídku zvolených uzlů. Zvolte **Vybrat** a **Invertovat výběr**.|
|Vyberte další uzly, které odkazují na vybrané.|Otevřete místní nabídku zvolených uzlů. Zvolte **Vybrat** a jednu z těchto akcí:<br /><br /> – Chcete-li vybrat další uzly, které odkazují přímo na vybraný uzel, zvolte **příchozí závislosti**.<br />– Chcete-li vybrat další uzly, které odkazují přímo z vybraného uzlu, zvolte **odchozí závislosti**.<br />– Chcete-li vybrat další uzly, které odkazují přímo na vybraný uzel a z něj, zvolte **obojí**.<br />– Chcete-li vybrat všechny uzly, které odkazují na vybraný uzel a z něj, zvolte možnost **připojený podgraf**.<br />– Chcete-li vybrat všechny podřízené položky vybraného uzlu, zvolte možnost **podřízené**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Filtrování uzlů a propojení

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Umožňuje zobrazit nebo skrýt podokno filtry.|Klikněte na tlačítko **filtry** na panelu nástrojů mapa kódu. Podokno **filtry** se v **Průzkumník řešení** ve výchozím nastavení zobrazuje jako stránka s kartami.|
|Filtrovat typy uzlů, které jsou zobrazeny na mapě.|Nastavte nebo zrušte zaškrtnutí políček v seznamu **prvky kódu** v podokně filtry.|
|Filtrovat typy odkazů, které jsou zobrazeny na mapě.|Nastavte nebo zrušte zaškrtnutí políček v seznamu **relace** v podokně filtry.|
|Zobrazit nebo skrýt uzly testovacího projektu na mapě.|Nastavte nebo zrušte zaškrtnutí políčka **test assets (prostředky testu** ) v seznamu **různé** v podokně filtry.|

Ikony zobrazené na panelu legenda v mapě odrážejí nastavení, které provedete v seznamu. Chcete-li zobrazit nebo skrýt panel legenda, klikněte na tlačítko **Legenda** na panelu nástrojů mapa kódu.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Kontrola uzlů a propojení

Mapy kódu ukazují tyto typy odkazů:

- Jednotlivé odkazy představují jednu relaci mezi dvěma uzly.

- Propojení mezi skupinami představuje vztah mezi dvěma uzly v různých skupinách.

- Agregovaný odkaz představuje všechny vztahy, které ukazují ve stejném směru mezi dvěma skupinami.

> [!TIP]
> Ve výchozím nastavení Mapa zobrazuje propojení mezi skupinami pouze pro vybrané uzly. Chcete-li toto chování změnit, aby se zobrazily nebo skryly agregované odkazy mezi skupinami, klikněte na tlačítko **rozložení** na panelu nástrojů mapa kódu a zvolte možnost **Upřesnit**, **Zobrazte všechny odkazy mezi skupinami** nebo **skryjte všechny odkazy mezi skupinami**. Další podrobnosti najdete v tématu [Skrytí nebo zobrazení uzlů a odkazů](#HidingShowing) .

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Zobrazit další informace o uzlu nebo odkazu.|Přesuňte ukazatel myši nad uzel nebo propojení, dokud se nezobrazí popisek.<br /><br /> Popis pro agregovaný odkaz obsahuje seznam jednotlivých závislostí, které představuje.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro uzel nebo odkaz. Vyberte možnost **Upravit**, **vlastnosti**.|
|Umožňuje zobrazit nebo skrýt obsah skupiny.|– Chcete-li rozšířit skupinu, otevřete místní nabídku uzlu a vyberte možnost **Skupina**, **rozbalte položku**.<br />     - nebo -<br />     Přesuňte ukazatel myši nad uzel, dokud se nezobrazí tlačítko se šipkou (šipka dolů). Kliknutím na toto tlačítko skupinu rozbalíte. Klávesnice: Chcete-li rozbalit nebo sbalit vybranou skupinu, stiskněte klávesu **plus** ( **+** ) nebo **mínus** ( **-** ).<br />– Chcete-li sbalit skupinu, otevřete místní nabídku uzlu a vyberte možnost **Skupina**, **sbalit**.<br />     - nebo -<br />     Přesuňte ukazatel myši nad skupinu, dokud se nezobrazí tlačítko dvojité šipky (šipka nahoru). Kliknutím na toto tlačítko skupinu sbalíte.<br />– Chcete-li rozbalit všechny skupiny, stiskněte klávesu **CTRL**  +  **a** vyberte všechny uzly. Otevřete místní nabídku pro mapu a vyberte možnost **Skupina** a **Rozbalit**. **Poznámka:**      Tento příkaz není k dispozici, pokud rozšířením všech skupin vygenerujete nepoužitou mapu nebo problémy s pamětí. Doporučuje se rozšířit mapu jenom na úroveň podrobností, o které se zajímáte.<br />– Chcete-li sbalit všechny skupiny, otevřete místní nabídku pro uzel nebo pro mapu. Vyberte možnost **Skupina**, **Sbalit vše**.|
|Viz definice kódu pro obor názvů, typ nebo člen.|Otevřete místní nabídku uzlu a vyberte možnost **Přejít k definici**.<br /><br /> -nebo-<br /><br /> Dvakrát klikněte na uzel. V případě rozšířených skupin dvakrát klikněte na záhlaví skupiny.<br /><br /> -nebo-<br /><br /> Vyberte uzel a stiskněte klávesu **F12**.<br /><br /> Příklad:<br /><br /> – Pro obor názvů obsahující jednu třídu se otevře soubor s kódem pro třídu, ve kterém se zobrazí definice této třídy. V jiných případech okno **výsledků hledání symbolů** zobrazuje seznam souborů kódu. **Poznámka:**      Při provádění této úlohy v oboru názvů Visual Basic se soubor kódu za oborem názvů neotevře. K tomuto problému dochází také při provádění této úlohy ve skupině vybraných uzlů, které zahrnují obor názvů Visual Basic. Chcete-li tento problém obejít, přejděte ručně do souboru kódu za oborem názvů nebo vynechejte uzel pro obor názvů z výběru.<br />– Pro třídu nebo částečnou třídu se otevře soubor kódu této třídy, aby se zobrazila definice třídy.<br />– Pro metodu se otevře soubor kódu pro nadřazenou třídu, aby se zobrazila definice metody.|
|Prověřte závislosti a položky, které se účastní agregačního odkazu.|Vyberte odkazy, které vás zajímají, a otevřete místní nabídku pro svůj výběr. Vyberte **Zobrazit přispívající odkazy**  nebo **Zobrazit přispívající odkazy na nové mapě kódu**.<br /><br /> Visual Studio rozbalí skupiny na obou koncích spojení a zobrazí pouze položky a závislosti, které se účastní odkazu. **Poznámka:**  Když prohlížíte závislosti mezi položkami v částečných skupinách, může se toto chování zobrazit: <ul><li>Odkazy na položky, které nejsou součástí vašeho zkoumání, zmizí z mapy, i když tyto odkazy stále existují.</li><li>Řekněme, že prohlížíte odkaz na položku v částečné skupině a později provedete kontrolu jiného odkazu na stejnou položku. Během druhého testu zobrazuje cílová částečná skupina jenom položky z prvního testu. Odkazy a cílové položky, které se neúčastnily vašeho prvního zkoumání, ale účastní se druhého testu, se nezobrazí.</li></ul> Chcete-li zobrazit chybějící položky ze skupiny, klikněte na tlačítko znovu **načíst podřízené**– ![ ikona pro opětovné načtení podřízených objektů ](../modeling/media/dependencygraph_deletednodesicon.png) (což znamená, že na mapě se nezobrazí všichni členové skupiny). Můžete také zkusit provést akce (klávesnice: stiskněte **kombinaci kláves CTRL + Z**) a prozkoumávat závislosti na nové mapě.|
|Prověřte závislosti mezi několika uzly v různých skupinách.|Rozbalte skupiny, abyste viděli všechny své podřízené položky. Vyberte všechny uzly, které vás zajímají, včetně jejich podřízených objektů. Mapa zobrazuje propojení mezi skupinami mezi vybranými uzly.<br /><br /> Pokud chcete vybrat všechny uzly ve skupině, stiskněte a podržte klávesu **SHIFT** a levé tlačítko myši, zatímco se kolem této skupiny nakreslí obdélník. Chcete-li vybrat všechny uzly na mapě, stiskněte klávesu **CTRL** + **a**. **Tip:**  Chcete-li zobrazit propojení mezi skupinami, klikněte na tlačítko **rozložení** na panelu nástrojů mapa, **Upřesnit**, **Zobrazit všechny odkazy mezi jednotlivými skupinami**.|
|Podívejte se na položky, na které odkazuje uzel nebo propojení.|Otevřete místní nabídku uzlu a vyberte **Najít všechny odkazy**. **Poznámka:**  To platí pouze v případě, že `Reference` je atribut nastaven pro uzel nebo propojení v souboru. dgml mapy. Chcete-li přidat odkazy na položky z uzlů nebo propojení, přečtěte si téma [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Skrytí nebo zobrazení uzlů a propojení

Skrytí uzlů umožňuje vynechat tyto uzly při použití algoritmů rozložení. Ve výchozím nastavení jsou propojení mezi skupinami skryta. Propojení mezi skupinami jsou jednotlivá propojení, která spojují uzly mezi skupinami. Když jsou skupiny sbaleny, mapa agreguje všechny odkazy mezi skupinami do jednoduchých propojení mezi skupinami. Pokud skupinu rozbalíte a vyberete v ní uzly, zobrazí se propojení mezi skupinami, která znázorňují závislosti v této skupině.

> [!CAUTION]
> Předtím, než nasdílíte mapu vytvořenou v Visual Studio Enterprise s uživateli, kteří používají Visual Studio Professional, nezapomeňte Zobrazit všechny uzly nebo propojení mezi skupinami, které chcete ostatním zobrazit. V opačném případě uživatelé nebudou moci tyto položky zobrazit.

### <a name="to-hide-or-show-nodes"></a>Skrytí nebo zobrazení uzlů

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Skryje vybrané uzly.|1. Vyberte uzly, které chcete skrýt.<br />2. Otevřete místní nabídku pro vybrané uzly nebo pro mapu. Zvolte **Vybrat** a **Skrýt vybrané**.|
|Skrýt nevybrané uzly.|1. Vyberte uzly, které chcete zůstat viditelné.<br />2. Otevřete místní nabídku pro vybrané uzly nebo pro mapu. Zvolte **Vybrat** a **Skrýt zrušit výběr**.|
|Zobrazit skryté uzly.|– Chcete-li zobrazit všechny skryté uzly ve skupině, nejprve se ujistěte, že je skupina rozbalená. Otevřete místní nabídku a zvolte **možnost vybrat**, **Zobrazit podřízené položky**.<br />     - nebo -<br />     V levém horním rohu skupiny klikněte na ikonu **Zobrazit podřízené objekty** ![ Zobrazit podřízené položky ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) (Tato možnost se zobrazí jenom v případě, že existují skryté podřízené uzly).<br />– Chcete-li zobrazit všechny skryté uzly, otevřete místní nabídku pro mapu nebo uzel a zvolte **možnost vybrat**, **Zobrazit vše**.|

### <a name="to-hide-or-show-links"></a>Skrytí nebo zobrazení odkazů

|**Do**|**Na panelu nástrojů mapa zvolte rozložení, Upřesnit a pak zvolte**|
|-|-|
|Zobrazit propojení mezi skupinami za všech okolností.|**Zobrazit všechny odkazy mezi skupinami**. Tím budou skryta souhrnná propojení mezi skupinami.|
|Nepřetržitě Skryjte propojení mezi skupinami.|**Skrýt všechny odkazy mezi skupinami**|
|Zobrazit pouze propojení mezi skupinami pro vybrané uzly.|**Zobrazit propojení mezi skupinami na vybraných uzlech**|
|Skrýt všechny odkazy.|**Skrýt všechny odkazy**. Chcete-li znovu zobrazit odkazy, vyberte jednu z možností uvedených výše.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Skupinové uzly

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Zobrazit uzly kontejneru jako uzly skupiny nebo uzly typu list.|Chcete-li zobrazit uzly kontejneru jako listové uzly: Vyberte uzly, otevřete místní nabídku pro svůj výběr a zvolte možnost **Skupina**, **převést na list**.<br /><br /> Chcete-li zobrazit uzly kontejneru jako uzly skupiny: Vyberte uzly, otevřete místní nabídku pro svůj výběr a zvolte možnost **Skupina**, **převést na skupinu**.|
|Změna rozložení v rámci skupiny.|Vyberte skupinu, otevřete místní nabídku, zvolte možnost **rozložení** a vyberte požadovaný styl rozložení.<br /><br /> - nebo -<br /><br /> 1. Vyberte skupinu a ujistěte se, že je rozbalená.<br />2. klikněte znovu na záhlaví skupiny a zobrazí se panel nástrojů skupina.<br />     ![Panel nástrojů &#45; seskupení grafu závislostí](../modeling/media/dependencygraph_group.png)<br />3. Otevřete okno **změnit styl rozložení** ![ grafu závislosti seznamu skupin &#45; skupinu &#45; rozložení ](../modeling/media/dependencygraph_grouptoolbar.gif) a vyberte požadovaný styl rozložení.<br /><br /> **Zobrazení seznamu** změní uspořádání členů skupiny na seznam. **Graph – výchozí** obnoví rozložení skupiny na výchozí rozložení mapy. Další možnosti najdete v tématu [Změna rozložení mapy](#Selecting).|
|Přidejte uzel do skupiny.|Přetáhněte uzel do skupiny.<br /><br /> Když přetáhnete uzel, Visual Studio zobrazí indikátor, který ukazuje, že přesouváte uzel.<br /><br /> Uzly lze přetáhnout také mimo skupinu.|
|Přidejte uzel do uzlu mimo skupinu.|Přetáhněte uzel na cílový uzel. Libovolný cílový uzel můžete převést na skupinu tak, že do něj přidáte uzly.|
|Seskupí vybrané uzly.|1. Vyberte uzly, které chcete seskupit. Místní panel nástrojů se zobrazí nad posledním vybraným uzlem.<br />     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)<br />2. na panelu nástrojů vyberte čtvrtou skupinu ikon **vybrané uzly** (Pokud je uzel rozbalený, bude mít pět ikon místo čtyř ikon). Zadejte název nové skupiny a stiskněte **vrátit**.<br />     - nebo -<br />     Vyberte uzly, které chcete seskupit, a otevřete místní nabídku pro svůj výběr. Zvolte možnost **Skupina**, **Přidat nadřazenou skupinu**, zadejte název nové skupiny a stiskněte tlačítko **vrátit**.<br /><br /> Skupinu můžete přejmenovat. Otevřete místní nabídku pro skupinu a kliknutím na položku **Upravit**, **vlastnosti** otevřete okno Vlastnosti sady Visual Studio. Ve vlastnosti **popisek** přejmenujte skupinu podle potřeby.|
|Odeberte skupiny.|Vyberte skupinu nebo skupiny, které mají být odstraněny. Otevřete místní nabídku pro svůj výběr a vyberte možnost **Skupina**, **Odebrat skupinu**.|
|Odeberte uzly ze své nadřazené skupiny.|Vyberte uzly, které mají být odebrány. Otevřete místní nabídku pro svůj výběr a vyberte možnost **Skupina**, **Odebrat z nadřazeného objektu**. Tím se odeberou uzly až do úrovně prarodič nebo mimo skupinu, pokud nemají žádnou skupinu prarodičů.<br /><br /> - nebo -<br /><br /> Vyberte uzly a přetáhněte je mimo skupinu.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Přidání, odebrání nebo přejmenování uzlů, odkazů a komentářů

Můžete zobrazit více nebo méně položek na mapě, aby bylo možné přejít k podrobnostem nebo zjednodušení mapy. Můžete také přejmenovat položky a přidat komentáře k položkám.

> [!CAUTION]
> Než nasdílíte mapu, která byla vytvořena pomocí Visual Studio Enterprise s uživateli, kteří používají Visual Professional, zajistěte, aby na mapě byly viditelné všechny prvky kódu, které mají ostatní vidět. V opačném případě uživatelé nebudou moci načíst odstraněné prvky kódu.

### <a name="add-a-node-for-a-code-element"></a>Přidat uzel pro prvek kódu

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Přidá nový obecný uzel v aktuálním umístění ukazatele myši.|1. přesuňte ukazatel myši na místo na mapě, kam chcete vložit nový prvek kódu, a stiskněte **Vložit**.<br />     - nebo -<br />     Otevřete místní nabídku pro mapu a vyberte možnost **Upravit**, **Přidat**, **obecný uzel**.<br />2. Zadejte název nového uzlu a stiskněte tlačítko **vrátit**.|
|Přidat konkrétní typ uzlu prvku kódu v aktuálním umístění ukazatele myši.|1. přesuňte ukazatel myši na místo na mapě, kam chcete vložit nový prvek kódu, a otevřete místní nabídku pro mapu.<br />2. Zvolte **Upravit**, **Přidat** a vyberte typ uzlu, který chcete.<br />3. Zadejte název nového uzlu a stiskněte tlačítko **vrátit**.|
|Přidejte do skupiny obecný nebo konkrétní typ uzlu elementu kódu.|1. vyberte uzel skupiny a otevřete místní nabídku.<br />2. Zvolte **Upravit**, **Přidat** a vyberte typ uzlu, který chcete.<br />3. Zadejte název nového uzlu a stiskněte tlačítko **vrátit**.|
|Přidání nového uzlu stejného typu a jeho propojení s existujícím uzlem.|1. Vyberte prvek kódu. Nad ním se zobrazí místní panel nástrojů.<br />     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)<br />2. na panelu nástrojů vyberte druhou ikonu **vytvořit uzel se stejnou kategorií, jako má tento uzel, a přidejte do něj nový odkaz**.<br />3. Vyberte místo na mapě pro vložení nového prvku kódu a klikněte levým tlačítkem myši.<br />4. Zadejte název nového uzlu a stiskněte tlačítko **vrátit**.|
|Přidejte nový obecný uzel, který je propojený z existujícího prvku kódu, který má fokus.|1. pomocí klávesnice stiskněte klávesu **TAB** , dokud prvek kódu, ze kterého se má propojit, má fokus (tečkovaný obdélník).<br />2. stiskněte klávesu **ALT** + **INSERT**.<br />3. Zadejte název nového uzlu a stiskněte tlačítko **vrátit**.|
|Přidejte nový obecný uzel, který odkazuje na existující prvek kódu, který má fokus.|1. pomocí klávesnice stiskněte klávesu **TAB** , dokud prvek kódu, na který chcete vytvořit odkaz, má fokus (tečkovaný obdélník).<br />2. stiskněte klávesu **ALT** + **SHIFT** + **INSERT**.<br />3. Zadejte název nového uzlu a stiskněte tlačítko **vrátit**.|

|**Přidání elementů kódu pro**|**Proveďte tyto kroky**|
|-|-|
|Prvky kódu v řešení.|1. Vyhledejte prvek kódu v **Průzkumník řešení**. Použijte vyhledávací pole **Průzkumník řešení** nebo procházejte řešením. **Tip:**      Chcete-li najít prvky kódu, které mají závislosti na typu nebo členu, otevřete místní nabídku pro typ nebo člen v **Průzkumník řešení**. Vyberte vztah, který vás zajímá. **Průzkumník řešení** zobrazuje pouze prvky kódu se zadanými závislostmi.<br />2. Přetáhněte prvky kódu, které vás zajímají na plochu rozvržení. Prvky kódu lze také přetáhnout z Zobrazení tříd nebo Prohlížeč objektů.<br />     - nebo -<br />     V **Průzkumník řešení** vyberte prvky kódu, které chcete namapovat. Pak na panelu nástrojů **Průzkumník řešení** klikněte na možnost **Zobrazit na mapě kódu**.<br /><br /> Ve výchozím nastavení se na mapě zobrazí nadřazená hierarchie kontejneru pro nové prvky kódu. Chcete-li toto chování změnit, použijte tlačítko **Zahrnout nadřazené prvky** na panelu nástrojů mapa kódu. Pokud je vypnutý, do mapy se přidá pouze samotný prvek kódu. Chcete-li toto chování vrátit pouze pro jednu akci přetažení, stiskněte a podržte stisknutou klávesu **CTRL** a přetáhněte prvky kódu na mapu.<br /><br /> Visual Studio přidá prvky kódu pro prvky kódu nejvyšší úrovně do výběru. Chcete-li zjistit, zda prvek kódu obsahuje jiné prvky kódu, přesuňte ukazatel myši nad prvek kódu tak, aby se zobrazila Dvojitá šipka (šipka dolů). Vyberte dvojitou šipku pro rozbalení prvku kódu. Chcete-li rozbalit všechny prvky kódu, stiskněte klávesu **CTRL** + **a** vyberte všechny prvky, otevřete místní nabídku pro mapu a zvolte možnost **Skupina** a **Rozbalit**. Tento příkaz není k dispozici, pokud rozšíření všech skupin vyprodukuje nepoužitelnou mapu nebo způsobí nedostatek problémů s pamětí.|
|Prvky kódu související s prvky kódu na mapě.|Klikněte na tlačítko **Zobrazit související** na panelu nástrojů mapa kódu a vyberte typ souvisejících položek, které vás zajímají.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro prvek kódu. V nabídce vyberte jednu z položek **Zobrazit...** v závislosti na druhu vztahu, který vás zajímá. Například můžete zobrazit položky, které odkazují na aktuální položku, položky odkazující na aktuální položku, základní a odvozené typy pro třídy, volající metody a obsahující třídy, obory názvů a sestavení.<br /><br /> Další podrobnosti najdete v [tomto tématu](../modeling/map-dependencies-across-your-solutions.md).|
|Kompilovaná sestavení .NET (. dll nebo. exe) nebo binární soubory.|Přetáhněte sestavení nebo binární soubory z vnějšku sady Visual Studio na mapu.<br /><br /> Z Průzkumníka Windows nebo Průzkumníka souborů můžete přetahovat jenom v případě, že ho spouštíte a Visual Studio na stejné úrovni oprávnění User Access Control (UAC). Pokud je například zapnutý nástroj řízení uživatelských účtů a používáte aplikaci Visual Studio jako správce, Průzkumník Windows nebo Průzkumník souborů zablokuje operaci přetažení.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Přidat propojení mezi existující prvky kódu

1. Vyberte prvek zdrojového kódu. Panel nástrojů se zobrazí nad prvkem kódu.

    ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2. Na panelu nástrojů klikněte na ikonu první, **vytvořte nový odkaz z tohoto uzlu na to, na který jste vytvořili uzel na další**.

3. Vyberte element cílového kódu. Mezi dvěma prvky kódu se zobrazí odkaz.

**OR**

1. Vyberte prvek zdrojového kódu na mapě.

2. Pokud máte nainstalovanou myš, přesuňte ukazatel myši mimo hranice mapy.

3. Otevřete místní nabídku prvku kódu a vyberte možnost **Upravit**  >  **Přidat**  >  **obecný odkaz**.

4. Na kartu a vyberte cílový prvek kódu pro odkaz.

5.  Stiskněte **Enter**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Přidat komentář na existující uzel na mapě

1. Vyberte prvek kódu. Nad ním se zobrazí panel nástrojů.

     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2. Na panelu nástrojů klikněte na třetí ikonu, **vytvořte nový uzel komentáře s novým odkazem na vybraný uzel**.

     \- ani

     Otevřete místní nabídku pro prvek kódu a vyberte možnost **Upravit**  >  **Nový komentář**.

3. Zadejte komentáře. Chcete-li zadat nový řádek, stiskněte klávesu **SHIFT**  +  **ENTER**.

#### <a name="add-a-comment-to-the-map-itself"></a>Přidání komentáře k samotné mapě

1. Otevřete místní nabídku pro mapu a klikněte na možnost **Upravit**  >  **Nový komentář**.

2. Zadejte komentáře. Chcete-li zadat nový řádek, stiskněte klávesu **SHIFT**  +  **ENTER**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Přejmenování elementu kódu nebo odkazu

1. Vyberte prvek kódu nebo odkaz, který chcete přejmenovat.

2. Stiskněte klávesu **F2** nebo otevřete místní nabídku a zvolte možnost **Upravit**  >  **přejmenování**.

3. Když se v mapě zobrazí pole pro úpravy, přejmenujte prvek kódu nebo odkaz.

**OR**

1. Otevřete místní nabídku a vyberte možnost **Upravit**  >  **vlastnosti**.

2. Upravte vlastnost **popisek** v okno Vlastnosti sady Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Odebrání elementu kódu nebo propojení z mapy

1. Vyberte prvek kódu nebo odkaz a stiskněte klávesu **Delete** .

     \- ani

     Otevřete místní nabídku pro prvek kódu nebo odkaz a klikněte na tlačítko **Upravit**  >  **Odebrat**.

2. Pokud je element nebo odkaz součástí skupiny,  ![ ](../modeling/media/dependencygraph_deletednodesicon.png) zobrazí se v rámci skupiny tlačítko znovu načíst podřízené položky. Kliknutím na tuto položku načtěte chybějící prvky a odkazy.

- Prvky kódu a odkazy z mapy lze odebrat, aniž by to ovlivnilo podkladový kód. Když je odstraníte, jejich definice se odeberou ze souboru DGML (. dgml).

- Mapy vytvořené úpravou DGML, přidáním nedefinovaných prvků kódu nebo pomocí některých dřívějších verzí sady Visual Studio, tuto funkci nepodporují.

#### <a name="flag-a-code-element-for-follow-up"></a>Označit prvek kódu pro následný

1. Vyberte prvek kódu nebo odkaz, pro který chcete nastavit příznak pro následné zpracování.

2. Otevřete místní nabídku a vyberte možnost **Upravit**  >  **příznak pro následné zpracování**.

- Ve výchozím nastavení prvek Code získá červené pozadí. Zvažte [Přidání komentáře](#AddComments) k tomuto s příslušnými následnými informacemi.

- Změňte barvu pozadí prvku nebo zrušte zaškrtnutí příznaku pro zpracování výběrem možnosti **Upravit**  >  **ostatní barvy příznaku**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Změna stylu elementu kódu nebo odkazu

Můžete změnit ikony prvků kódu a barvy prvků kódu a odkazy pomocí předdefinovaných ikon a barev. Můžete například zvolit barvu pro zvýraznění prvků kódu a odkazů, které mají určitou kategorii nebo vlastnost. To vám umožní identifikovat konkrétní oblasti mapy a soustředit se na ně. Vlastní ikony a barvy můžete zadat úpravou souboru. dgml mapy. Další informace najdete v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Použití předdefinované barvy nebo ikony pro prvky kódu nebo odkazy s určitou kategorií nebo vlastností

1. Na panelu nástrojů mapa vyberte možnost **Legenda**.

2. V poli **Legenda** je vidět, zda se kategorie nebo vlastnost kódu již v seznamu nachází.

3. Pokud seznam neobsahuje kategorii ani vlastnost, zvolte možnost **+** v poli **Legenda** a pak zvolte **vlastnost uzlu**, **kategorii uzlu**, **vlastnost odkazu** nebo **kategorii odkazů**. Pak zvolte vlastnost nebo kategorii. Kategorie nebo vlastnost se nyní zobrazí v poli **Legenda** .

    > [!NOTE]
    > Chcete-li vytvořit a přiřadit kategorii nebo vlastnost prvku kódu, můžete upravit soubor. dgml mapy. Další informace najdete v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. V poli **Legenda** klikněte na ikonu vedle kategorie nebo vlastnosti, kterou jste přidali nebo kterou chcete změnit.

5. Pro výběr stylu, který chcete změnit, použijte následující tabulku:

    |**Chcete-li změnit**|**Výběrem**|
    |-|-|
    |Barva pozadí|**Pozadí**|
    |Barva obrysu|**Tažen**|
    |Barva textu (pro zobrazení výsledku se zobrazí písmeno "f")|**Popředí**|
    |Ikona|**Ikony**|

     Pro výběr barvy nebo ikony se zobrazí dialogové okno Výběr **sady barev** nebo **Výběr sady ikon** .

6. V dialogovém okně **Výběr sady barev** nebo dialogové okno **pro výběr sady ikon** proveďte jednu z následujících akcí:

    |**Použití**|**Proveďte tyto kroky**|
    |-|-|
    |Sada barev nebo ikon|Otevřete seznam **Vybrat** **sadu** barev (nebo **ikon**). Vyberte sadu barev nebo ikon.|
    |Konkrétní barva nebo ikona|Otevřete seznam hodnot kategorií nebo vlastností. Vyberte barvu nebo ikonu.|

    > [!NOTE]
    > V poli **Legenda** můžete styly znovu uspořádat, odstranit nebo dočasně deaktivovat. Viz [Upravit pole legenda](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Úprava pole legenda

V poli **Legenda** můžete styly znovu uspořádat, odstranit nebo dočasně deaktivovat:

1. Otevřete místní nabídku pro styl v poli **Legenda** .

2. Proveďte některou z následujících úloh:

    |**Do**|**Výběrem**|
    |-|-|
    |Deaktivovat prvek kódu|**Zakázat**|
    |Odstranit prvek kódu|**Odstranit**|
    |Přesunutí stylu nahoru|**Přesunout nahoru**|
    |Přesunout element kódu dolů|**Přesunout dolů**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Kopírovat styly z jednoho mapování na jiný

1. Ujistěte se, že se pole **Legenda** zobrazuje na zdrojovém mapování. Pokud není zobrazená, na panelu nástrojů Mapa klikněte na **Legenda**.

2. Otevřete místní nabídku pro pole **Legenda** . Vyberte možnost **Kopírovat legendu**.

3. Vložte legendu na cílovou mapu.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Sloučit mapy kódu

Mapy můžete sloučit kopírováním a vložením prvků kódu mezi mapami. Pokud se identifikátory prvků kódu shodují, pak vložení prvků kódu funguje jako operace sloučení. Chcete-li tuto úlohu usnadnit, vložte všechna sestavení nebo binární soubory, které chcete vizualizovat, do stejné složky tak, aby úplná cesta každého sestavení nebo binárního souboru byla stejná pro každou mapu, kterou chcete sloučit.

Alternativně můžete tato sestavení nebo binární soubory přetáhnout na stejnou mapu z této složky.

## <a name="see-also"></a>Viz také

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Referenční dokumentace jazyka přímého značení grafů (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
