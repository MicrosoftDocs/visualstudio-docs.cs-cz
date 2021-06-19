---
title: Procházení a změna uspořádání map kódu
description: Zjistěte, jak můžete změnit uspořádání položek v mapách kódu, aby se snadněji četly a vylepšoval jejich výkon.
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83132cfccd0af7244cf31f502669144eb3388bd8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385549"
---
# <a name="browse-and-rearrange-code-maps"></a>Procházení a změna uspořádání map kódu

Změna uspořádání položek v mapách kódu, aby se snadněji četly a vylepšoval jejich výkon.

Mapy kódu můžete přizpůsobit, aniž by to ovlivnilo základní kód v řešení. To je užitečné, když se chcete zaměřit na klíčové elementy kódu nebo sdělovat nápady o kódu. Pokud chcete například zvýraznit zajímavé oblasti, můžete vybrat prvky kódu na mapě a filtrovat je, změnit styl prvků kódu a odkazů, skrýt nebo odstranit prvky kódu a uspořádat prvky kódu pomocí vlastností, kategorií nebo skupin.

 **Požadavky**

- Pokud chcete vytvořit mapy kódu, musíte mít Visual Studio Enterprise.

- Mapy kódu můžete zobrazit a provádět omezené úpravy map kódu v Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Začínáme pracovat s mapami kódu

Vytvořte mapu kódu (další podrobnosti najdete v tématu Mapování závislostí [napříč](../modeling/map-dependencies-across-your-solutions.md) řešeními). Pokud nechcete čekat na dokončení generování mapy, kdykoli  kliknutím na odkaz Zrušit proces generování zastavte. V takovém případě ale neuvidíte podrobnosti o všech závislostech a odkazech.

Po vygenerování mapy můžete začít s těmito tipy pro revize kódu:

- Podívejte se na clustery přirozených závislostí v kódu. Na panelu nástrojů mapy zvolte **Tlačítko Rozložení**, **Rychlé clustery** Rychlé ![ clustery na panelu nástrojů ](../modeling/media/quickclustersicon.gif) grafu. Viz [Změna rozložení mapy.](#Selecting)

     ![Graf závislostí &#45; rychlého rozložení clusterů](../modeling/media/dependencygraph_quickclusters.png)

- Uspořádejte mapu do menších oblastí seskupením souvisejících uzlů. Sbalte tyto skupiny, abyste viděli pouze závislosti meziskupiny, které se zobrazí automaticky. Viz [Seskupení uzlů](#OrganizeGroups).

- Pomocí filtrů můžete mapu zjednodušit a zaměřit se na typy uzlů nebo odkazů, které vás zajímají. Viz [Filtrování uzlů a odkazů](#FilterNodes).

- Maximalizujte výkon velkých map. Další [informace najdete v tématu Mapování závislostí napříč](../modeling/map-dependencies-across-your-solutions.md) řešeními. Můžete například zapnout přeskočit **sestavení** na panelu nástrojů mapy, aby Visual Studio při aktualizaci položek na mapě znovu nevytvářel řešení.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Změna rozložení mapy

|**Do**|**Proveďte tyto kroky:**|
|-|-|
|Uspořádejte tok závislostí pro celou mapu v určitém směru. To vám může pomoct vidět vrstvy architektury v kódu.|Na panelu nástrojů mapy zvolte **Rozložení** a pak:<br /><br /> -   **Shora dolů** ![ Tlačítko grafu shora dolů](../modeling/media/topbottomgraphbutton.gif)<br />-   **Shora dolů** ![ Tlačítko Dole na horní graf](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Zleva doprava** ![ Tlačítko rozložení zleva doprava](../modeling/media/leftrightgraphbutton.gif)<br />-   **Zprava doleva** ![ Tlačítko grafu zprava doleva](../modeling/media/rightleftgraphbutton.gif)|
|Prohlédněte si clustery přirozených závislostí v kódu s nejvíce závislými uzly uprostřed clusterů a nejméně závislými uzly mimo tyto clustery.|Na panelu nástrojů mapy zvolte **Rozložení** a pak **na** panelu nástrojů grafu klikněte na tlačítko Rychlé ![ clustery Rychlé ](../modeling/media/quickclustersicon.gif) clustery.|
|Vyberte jeden nebo více uzlů na mapě.|Kliknutím vyberte uzel. Pokud chcete vybrat nebo zrušit výběr více než jednoho uzlu, podržte při kliknutí **klávesu CTRL.**<br /><br /> Klávesnice: Stisknutím **klávesy TAB** nebo klávesami se šipkami přesuňte tečkovaný obdélník fokusu na uzel a stisknutím **mezerníku** ho vyberte. Stisknutím **kláves CTRL**  +  **MEZERNÍK** můžete vybrat více uzlů nebo zrušit jejich výběr.|
|Přesuňte konkrétní uzly na mapě.|Přetažením uzlů je přesuňte. Pokud chcete při přetahování uzlů přesunout jiné uzly a odkazy, stiskněte a podržte **klávesu SHIFT.**<br /><br /> Klávesnice: **Podržte klávesu CTRL** a stiskněte klávesy se šipkami.|
|Změňte rozložení uvnitř skupiny nezávisle na ostatních uzlech a skupinách na mapě.|Vyberte uzel a otevřete místní nabídku. Zvolte **Rozložení** a vyberte styl rozložení.<br /><br /> - nebo -<br /><br /> Vyberte uzel a rozbalte ho, aby se zobrazí podřízené uzly. Kliknutím na název uzlu zobrazíte místní panel nástrojů skupiny a otevřete panel nástrojů Změnit styl rozložení skupiny Graf závislostí &#45; panelu nástrojů ![ &#45; ](../modeling/media/dependencygraph_grouptoolbar.gif) rozložení. Vyberte jedno ze stromových rozložení, **rychlé clustery** nebo zobrazení seznamu **(které** uspořádá obsah skupiny do seznamu).<br /><br /> Další [podrobnosti najdete v tématu Uzly](#OrganizeGroups) skupin.|
|Vrátí zpět akci na mapě.|Stiskněte **CTRL**  +  **Z** nebo použijte příkaz Visual Studio **Zpět.**|

## <a name="browse-the-map"></a><a name="Explore"></a> Procházení mapy

|**Do**|**Proveďte tyto kroky:**|
|-|-|
|Naskenujte mapu.|Přetáhněte mapu v libovolném směru pomocí myši.<br /><br /> - nebo -<br /><br /> Podržte **klávesu SHIFT** a otočením kolečka myši se posuňte vodorovně. Podržte **klávesu**  +  **SHIFT CTRL** a otočením kolečka myši se posuňte vodorovně.|
|Přiblížení nebo oddálení mapy|Otočení kolečka myši.<br /><br /> - nebo -<br /><br /> Použijte rozevírací **seznam** Lupa na panelu nástrojů mapy kódu.<br /><br /> - nebo -<br /><br /> Použijte klávesové zkratky. Pokud chcete zobrazení přiblížit, stiskněte **kombinaci kláves CTRL + SHIFT + .** (období). Pokud chcete zobrazení oddálit, **stiskněte kombinaci kláves CTRL + SHIFT + ,** (čárka).|
|Přiblížení konkrétní oblasti pomocí myši|Při kreslení obdélníku kolem této oblasti, která vás zajímá, podržte pravé tlačítko myši.|
|Změňte velikost mapy a přizpůsobte se jejímu oknu.|V **seznamu Lupa** na panelu **nástrojů** mapy kódu zvolte Zoom to Fit (Přiblížit podle velikosti).<br /><br /> - nebo -<br /><br /> Na panelu nástrojů **mapy** kódu klikněte na ikonu Zoom to fit (Přiblížit podle velikosti) Ikona Lupa na panelu ![ nástrojů ](../modeling/media/almcodemapzoomicon.png) mapy. Klávesnice: Stiskněte **CTRL + 0** (nula).|
|Vyhledejte uzel na mapě podle jeho názvu. **Tip:**  To funguje jenom u položek na mapě. Pokud chcete najít položky v řešení, ale ne na mapě, vyhledejte je v Průzkumník řešení **a** pak je přetáhněte na mapu. (Přetáhněte svůj výběr nebo na **panelu** Průzkumník řešení klikněte na Zobrazit na **mapě kódu**).|1. Zvolte  ikonu Najít Ikona Najít na panelu nástrojů mapy na panelu nástrojů mapy kódu (Klávesnice: stisknutím kombinace kláves CTRL + F ) zobrazíte vyhledávací pole v pravém horním ![ rohu ](../modeling/media/almcodemapfindicon.png) mapy.<br />2. Zadejte název položky a stiskněte **Return** nebo klikněte na ikonu lupy. Na mapě se zobrazí první položka, která odpovídá vašemu hledání.<br />3. Pokud chcete hledání přizpůsobit, otevřete rozevírací seznam a zvolte možnost hledání. Možnosti jsou Najít **další,** **Najít předchozí** a **Vybrat vše.** Potom klikněte na odpovídající tlačítko vedle textového pole hledání.<br />     ![Rozevírací seznam možností&#45;hledání](../modeling/media/almcodemapssearchdropdown.png)<br />     Případně můžete použít klávesnici: stisknutím **klávesy F3** vyberte další odpovídající uzel nebo **SHIFT + F3** a vyberte předchozí odpovídající uzel.<br />4. Kliknutím na ikony pod textovým polem hledání vyberte libovolnou z možností, které určují, jak se mají hledané termíny zpracovat.<br />     ![Možnosti hledání shody](../modeling/media/almcodemapssearchmatchicons.png)<br />     Možnosti jsou zleva doprava, porovnávání s rozlišování malých a malých písmen, shoda pouze s celými slovy, použití syntaxe regulárního výrazu .NET, automatické rozbalení skupin, aby se zobrazují shody uzavřených položek. **Důležité:**  Vyhledávací pole můžete použít k vyhledání shod ve sbalené skupině pouze v případě, že byly dříve rozbaleny. Pokud chcete tyto shody vyhledat a automaticky rozbalit jejich nadřazené skupiny, vyberte tuto možnost ve vyhledávacím poli.|
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
|Přidání nového uzlu stejného typu a jeho propojení s existujícím uzlem.|1. Vyberte prvek kódu. Nad ním se zobrazí místní panel nástrojů.<br />     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)<br />2. na panelu nástrojů vyberte druhou ikonu **vytvořit uzel se stejnou kategorií, jako má tento uzel, a přidejte do něj nový odkaz**.<br />3. Zvolte místo na mapě, kam chcete nový prvek kódu umístit, a klikněte na levé tlačítko myši.<br />4. Zadejte název nového uzlu a stiskněte **Klávesu Return.**|
|Přidejte nový obecný uzel, který je propojený z existujícího elementu kódu, který má fokus.|1. Stisknutím klávesy Tab stiskněte **klávesu Tab,** dokud prvek kódu, ze který chcete vytvořit odkaz, nemá fokus (tečkovaný obdélník).<br />2. Stiskněte **Alt** + **Insert**.<br />3. Zadejte název nového uzlu a stiskněte **Klávesu Return.**|
|Přidejte nový obecný uzel, který odkazuje na existující prvek kódu, který má fokus.|1. Stisknutím klávesy Tab stiskněte **klávesu Tab,** dokud prvek kódu, na který chcete vytvořit odkaz, nemá fokus (tečkovaný obdélník).<br />2. Stiskněte **Alt** + **Shift** + **Insert**.<br />3. Zadejte název nového uzlu a stiskněte **Klávesu Return.**|

|**Přidání elementů kódu pro**|**Proveďte tyto kroky:**|
|-|-|
|Prvky kódu v řešení.|1. Najděte element kódu v **Průzkumník řešení**. Použijte vyhledávací **Průzkumník řešení** nebo vyhledejte řešení. **Tip:**      Pokud chcete najít elementy kódu, které mají závislosti na typu nebo členu, otevřete místní nabídku pro typ nebo člena v **Průzkumník řešení**. Vyberte vztah, který vás zajímá. **Průzkumník řešení** se zobrazí pouze elementy kódu se zadanými závislostmi.<br />2. Přetáhněte prvky kódu, které vás zajímají, na plochu mapy. Můžete také přetáhnout prvky kódu z Zobrazení tříd nebo Prohlížeče objektů.<br />     - nebo -<br />     V **Průzkumník řešení** vyberte prvky kódu, které chcete namapovat. Pak na panelu **Průzkumník řešení** klikněte na Zobrazit na mapě **kódu.**<br /><br /> Ve výchozím nastavení se nadřazená hierarchie kontejneru pro nové elementy kódu zobrazuje na mapě. Toto chování **můžete změnit pomocí** tlačítka Include Parents (Zahrnout rodiče) na panelu nástrojů mapy kódu. Když je vypnuté, do mapy se přidá pouze samotný element kódu. Pokud chcete toto chování vrátit zpět jenom u jedné akce přetažení, stiskněte a podržte klávesu **CTRL** a přetáhněte prvky kódu na mapu.<br /><br /> Visual Studio přidá prvky kódu pro prvky kódu nejvyšší úrovně ve vašem výběru. Pokud chcete zobrazit, jestli element kódu obsahuje další prvky kódu, přesuňte ukazatel myši nad prvek kódu tak, aby se zobrazí šipka dolů. Výběrem symbolu chevron rozbalte prvek kódu. Pokud chcete rozbalit všechny prvky kódu, stiskněte **CTRL** A, abyste vybrali všechny prvky, otevřete místní nabídku pro mapu a zvolte +  **Skupina**, **Rozbalit**. Tento příkaz není dostupný, pokud by rozbalení všech skupin způsobilo nepoužitelné mapování nebo způsobilo nedostatek problémů s pamětí.|
|Prvky kódu související s elementy kódu na mapě.|Na panelu **nástrojů mapy** kódu klikněte na tlačítko Zobrazit související a zvolte typ souvisejících položek, které vás zajímají.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro element kódu. V závislosti na **typu relace,** který vás zajímá, zvolte jednu z položek Zobrazit ... v nabídce. Můžete například zobrazit položky, na které aktuální položka odkazuje, položky, které odkazují na aktuální položku, základní a odvozené typy pro třídy, volající metody a obsahující třídy, obory názvů a sestavení.<br /><br /> Další podrobnosti najdete v [tomto tématu.](../modeling/map-dependencies-across-your-solutions.md)|
|Zkompilovaná sestavení .NET (.dll nebo .exe) nebo binární soubory.|Přetáhněte sestavení nebo binární soubory z Visual Studio na mapu.<br /><br /> Můžete přetáhnout z Průzkumník Windows nebo Průzkumník souborů jenom v případě, že ho používáte a Visual Studio na stejné úrovni oprávnění Access Control (UAC). Pokud je například řízení uživatelských účtů zapnuté a Visual Studio správce, Průzkumník Windows nebo Průzkumník souborů operaci přetažení zablokují.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Přidání propojení mezi existujícími elementy kódu

1. Vyberte prvek zdrojového kódu. Nad elementem kódu se zobrazí panel nástrojů.

    ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2. Na panelu nástrojů zvolte první ikonu Create new link from this node to which ever node that you click on next (Vytvořit nový odkaz z tohoto uzlu), na který **kdy kliknete.**

3. Vyberte cílový prvek kódu. Mezi těmito dvěma elementy kódu se zobrazí propojení.

**OR**

1. Vyberte prvek zdrojového kódu na mapě.

2. Pokud máte nainstalovanou myš, přesuňte ukazatel myši mimo hranice mapy.

3. Otevřete místní nabídku elementu kódu a zvolte **Upravit**  >  **přidat**  >  **obecný odkaz.**

4. Pomocí tabulátoru na odkaz vyberte cílový element kódu.

5.  Stiskněte **Enter**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Přidání komentáře k existujícímu uzlu na mapě

1. Vyberte element kódu. Nad ní se zobrazí panel nástrojů.

     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2. Na panelu nástrojů zvolte třetí ikonu Vytvořit nový uzel komentáře s novým **odkazem na vybraný uzel**.

     \- nebo –

     Otevřete místní nabídku pro element kódu a zvolte **Upravit**  >  **nový komentář**.

3. Zadejte komentáře. Pokud chcete zadat na nový řádek, stiskněte **Klávesu Shift**  +  **Enter.**

#### <a name="add-a-comment-to-the-map-itself"></a>Přidání komentáře k samotné mapě

1. Otevřete místní nabídku pro mapu a zvolte **Upravit**  >  **nový komentář.**

2. Zadejte komentáře. Pokud chcete zadat na nový řádek, stiskněte **Klávesu Shift**  +  **Enter.**

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Přejmenování elementu kódu nebo odkazu

1. Vyberte element kódu nebo odkaz, který chcete přejmenovat.

2. Stiskněte **klávesu F2** nebo otevřete místní nabídku a zvolte **Upravit**  >  **přejmenovat.**

3. Jakmile se v mapě zobrazí textové pole, přejmenujte element kódu nebo odkaz.

**OR**

1. Otevřete místní nabídku a zvolte **Upravit**  >  **vlastnosti**.

2. Upravte vlastnost **Popisek** v Visual Studio okno Vlastnosti.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Odebrání elementu kódu nebo odkazu z mapy

1. Vyberte element kódu nebo odkaz a stiskněte **klávesu** Delete.

     \- nebo –

     Otevřete místní nabídku pro element kódu nebo odkaz a zvolte **Upravit**  >  **odebrat**.

2. Pokud je prvek nebo odkaz součástí skupiny, zobrazí se ve skupině tlačítko **Znovu** načtou děti Ikona Znovu načtou ![ ](../modeling/media/dependencygraph_deletednodesicon.png) děti. Kliknutím na tuto možnost načtete chybějící prvky a odkazy.

- Prvky kódu a odkazy z mapy můžete odebrat, aniž by to ovlivnilo základní kód. Když je odstraníte, jejich definice se odstraní ze souboru DGML (.dgml).

- Mapy vytvořené úpravou jazyka DGML, přidáním nedefinovaných elementů kódu nebo některými staršími verzemi Visual Studio nepodporují tuto funkci.

#### <a name="flag-a-code-element-for-follow-up"></a>Označení elementu kódu příznakem pro následné sledování

1. Vyberte element kódu nebo odkaz, který chcete označit příznakem pro následné následování.

2. Otevřete místní nabídku a v **nabídce**  >  **Sledovat zvolte Upravit příznak.**

- Ve výchozím nastavení získá prvek kódu červené pozadí. Zvažte [přidání komentáře](#AddComments) s příslušnými náplněmi.

- Změňte barvu pozadí elementu nebo zrušte zaškrtnutí následující příznaku výběrem možnosti **Upravit**  >  **jiné barvy příznaků.**

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Změna stylu elementu kódu nebo odkazu

Pomocí předdefinovaných ikon a barev můžete změnit ikony u prvků kódu a barev prvků kódu a odkazů. Můžete například zvolit barvu a zvýraznit prvky kódu a odkazy, které mají určitou kategorii nebo vlastnost. To vám umožní identifikovat konkrétní oblasti mapy a zaměřit se na tyto oblasti. Vlastní ikony a barvy můžete zadat úpravou souboru .dgml mapy. Viz [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Použití předdefinované barvy nebo ikony u prvků kódu nebo odkazů s určitou kategorií nebo vlastností

1. Na panelu nástrojů mapy zvolte **Legenda**.

2. V poli **Legenda** se podívejte, jestli se v seznamu už zobrazuje kategorie nebo vlastnost elementu kódu.

3. Pokud seznam neobsahuje kategorii nebo vlastnost, zvolte v poli Legenda a pak zvolte Vlastnost uzlu, Kategorie uzlu, Vlastnost propojení **+** nebo Kategorie **propojení.**     Pak zvolte vlastnost nebo kategorii. Kategorie nebo vlastnost se teď zobrazí v **poli Legenda.**

    > [!NOTE]
    > Pokud chcete vytvořit kategorii nebo vlastnost prvku kódu a přiřadit ji, můžete upravit soubor .dgml mapy. Viz [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. V poli **Legenda** klikněte na ikonu vedle kategorie nebo vlastnosti, kterou jste přidali nebo kterou chcete změnit.

5. Pro výběr stylu, který chcete změnit, použijte následující tabulku:

    |**Změna**|**Zvolte**|
    |-|-|
    |Barva pozadí|**Pozadí**|
    |Barva obrysu|**Tahu**|
    |Barva textu (zobrazí se písmeno "f", které zobrazuje výsledek)|**Popředí**|
    |Ikona|**Ikony**|

     Zobrazí se dialogové  okno **Výběr** sady barev nebo Výběr sady ikon, ve které můžete vybrat barvu nebo ikonu.

6. V **dialogovém okně Výběr sady barev** nebo Výběr sady **ikon** proveďte jednu z následujících akcí:

    |**Použití**|**Proveďte tyto kroky:**|
    |-|-|
    |Sada barev nebo ikon|Otevřete seznam **setů Vybrat** **barvu (nebo** **ikonu).** Vyberte sadu barev nebo ikon.|
    |Konkrétní barva nebo ikona|Otevřete seznam hodnot kategorií nebo vlastností. Vyberte barvu nebo ikonu.|

    > [!NOTE]
    > V poli **Legenda** můžete změnit uspořádání, odstranit nebo dočasně deaktivovat styly. Viz [Úprava pole Legenda.](#ModifyLegend)

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Úprava pole Legenda

Styly legendy můžete přeuspořádat, odstranit nebo dočasně **deaktivovat:**

1. Otevřete místní nabídku pro styl v **poli Legenda.**

2. Proveďte některou z následujících úloh:

    |**Do**|**Zvolte**|
    |-|-|
    |Deaktivace elementu kódu|**Zakázat**|
    |Odstranění elementu kódu|**Odstranit**|
    |Přesunutí stylu nahoru|**Přesunout nahoru**|
    |Přesunutí elementu kódu dolů|**Přesunout dolů**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Kopírování stylů z jedné mapy do jiné

1. Ujistěte **se, že** se na zdrojové mapě zobrazí pole Legenda. Pokud se nezobrazí, klikněte na panelu nástrojů mapy na **Legenda**.

2. Otevřete místní nabídku pro **pole Legenda.** Zvolte **Copy Legend (Kopírovat legendu).**

3. Vložte legendu na cílovou mapu.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Sloučení map kódu

Mapy můžete sloučit zkopírováním a vložením prvků kódu mezi mapami. Pokud se identifikátory elementů kódu shodují, vložení prvků kódu funguje jako operace sloučení. Aby byla tato úloha jednodušší, umístěte všechna sestavení nebo binární soubory, které chcete vizualizovat, do stejné složky, aby byla úplná cesta ke každému sestavení nebo binárnímu souboru stejná pro každou mapu, kterou chcete sloučit.

Případně můžete tato sestavení nebo binární soubory přetáhnout na stejnou mapu z této složky.

## <a name="see-also"></a>Viz také

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Referenční dokumentace jazyka přímého značení grafů (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
