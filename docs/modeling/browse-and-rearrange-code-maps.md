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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3b3a751a25d65560a85d853e083a4bbdd33b91ac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921675"
---
# <a name="browse-and-rearrange-code-maps"></a>Procházení a změna uspořádání map kódu

Změna uspořádání položek na mapách kódu, aby se daly snadněji číst a vylepšit jejich výkon.

Přizpůsobení map kódu bez ovlivnění základního kódu v řešení. To je užitečné, pokud chcete zaměřit na kód elementy nebo sdělovat nápady týkající kód. Například pro zvýraznění zajímavých oblastí, můžete vybrat prvky kódu na mapě filtrovat je, změnit styl prvky kódu a odkazy, skrýt nebo odstranit prvky kódu a uspořádat prvky kódu pomocí vlastností, kategorií nebo skupin.

 **Požadavky**

-   K vytvoření kódových map, musíte mít Visual Studio Enterprise.

-   Můžete zobrazit map kódu a provádění omezené úprav map kódu v aplikaci Visual Studio Professional.

##  <a name="ManageLargeGraphs"></a> Začít pracovat pomocí map kódu

Vytvořte mapu kódu (viz [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md) další podrobnosti). Pokud nechcete čekat na mapě dokončení generování, klikněte na tlačítko **zrušit** odkaz kdykoli zastavit proces vytváření. Podrobnosti o všech závislostí a odkazy, ale nezobrazí, pokud to provedete.

Jakmile vygenerujete na mapě, vám umožní začněte tyto tipy pro revizi kódu:

-   Podívejte se na clustery přirozené závislosti v kódu. Na panelu nástrojů Mapa **rozložení**, **rychlé seskupení**![rychlé clustery tlačítko na panelu nástrojů grafu](../modeling/media/quickclustersicon.gif). Zobrazit [změnit rozložení mapy](#Selecting).

     ![Graf závislosti &#45; rychlé clustery](../modeling/media/dependencygraph_quickclusters.png)

-   Uspořádání mapy do menších oblasti seskupením souvisejících uzlů. Tyto skupiny sbalte a zobrazit pouze intergroup závislosti, které se zobrazí automaticky. Zobrazit [seskupit uzly](#OrganizeGroups).

-   Použití filtrů k zjednodušení mapy a zaměřit se na typy uzlů a propojení, které vás zajímají. Zobrazit [filtrovat uzlům a propojením](#FilterNodes).

-   Maximalizujte výkon, velké map. Zobrazit [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md) Další informace. Například zapnutí **přeskočení buildu** na panelu nástrojů Mapa tak, že Visual Studio nebude znovu sestavte své řešení při aktualizaci položky na mapě.

##  <a name="Selecting"></a> Změnit rozložení mapy

|**k**|**Proveďte tyto kroky**|
|-|-|
|Zařídit celou mapu v konkrétní směr toku závislostí. To vám může pomoci zjistit vrstvy architektury v kódu.|Na panelu nástrojů Mapa **rozložení**a pak:<br /><br /> -   **Shora dolů** ![shora tlačítko dolního grafu](../modeling/media/topbottomgraphbutton.gif)<br />-   **Zdola nahoru** ![dole tlačítko horního grafu](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Zleva doprava** ![zleva doprava rozložení tlačítko](../modeling/media/leftrightgraphbutton.gif)<br />-   **Zprava doleva** ![přímo do grafu levé tlačítko](../modeling/media/rightleftgraphbutton.gif)|
|Podívejte se na clustery přirozené závislosti v kódu s nejvíce závislé uzly v centru clusterů a nejméně závislé uzlů v mimo tyto clustery.|Na panelu nástrojů Mapa **rozložení**a potom **rychlé seskupení**![rychlé clustery tlačítko na panelu nástrojů grafu](../modeling/media/quickclustersicon.gif).|
|Vyberte jeden nebo více uzly na mapě.|Klikněte na uzel vyberte. Zaškrtněte nebo zrušte výběr více než jeden uzel, podržte **CTRL** při kliknutí na.<br /><br /> Klávesnice: stiskněte **kartu** nebo pomocí kláves se šipkami tečkovaná obdélník přesunout do uzlu a stiskněte klávesu **místo** ji vyberte. Stisknutím klávesy **CTRL** + **místo** vyberte nebo zrušte výběr uzlů.|
|Konkrétní uzly přesuňte na mapě.|Přetáhnout uzly přesouvat. Přesunout dalších uzlů a propojení eliminuje přetahování uzlů, stiskněte a podržte **SHIFT** klíč.<br /><br /> Klávesnice: stiskněte a podržte **CTRL** a stisknutím klávesy se šipkami.|
|Změna rozložení uvnitř skupiny nezávisle na ostatních uzlech a skupiny na mapě.|Vyberte uzel a otevřete místní nabídku. Zvolte **rozložení** a vyberte styl rozložení.<br /><br /> - nebo -<br /><br /> Vyberte uzel a rozbalit a zobrazit podřízené uzly. Klikněte na název uzlu zobrazit panel nástrojů místní skupiny a otevřete **změnit styl rozložení skupiny**![graf závislosti &#45; nástrojů skupiny &#45; rozložení](../modeling/media/dependencygraph_grouptoolbar.gif) seznamu. Vyberte rozložení stromové struktury **rychlé seskupení**, nebo **zobrazení seznamu** (který uspořádá obsah skupiny do seznamu).<br /><br /> Zobrazit [seskupit uzly](#OrganizeGroups) další podrobnosti.|
|Vrátit zpět akce v objektu map.|Stisknutím klávesy **CTRL** + **Z** nebo pomocí sady Visual Studio **zpět** příkazu.|

##  <a name="Explore"></a> Přejděte na mapě

|**k**|**Proveďte tyto kroky**|
|-|-|
|Kontrola na mapě.|Vede libovolným směrem pomocí myši přetáhněte na mapě.<br /><br /> - nebo -<br /><br /> Uložení **SHIFT** a otočení kolečka myši vodorovně posouvat. Uložení **SHIFT** + **CTRL** a otočení kolečka myši vodorovně posouvat.|
|Přiblížení nebo oddálení mapy v.|Otočení kolečka myši.<br /><br /> - nebo -<br /><br /> Použití **přiblížení** rozevíracího seznamu na panelu nástrojů mapy kódu.<br /><br /> - nebo -<br /><br /> Používání klávesových zkratek. Chcete-li zvětšit, stiskněte **CTRL + SHIFT +.** (tečka). Horizonální oddálení, stiskněte klávesu **CTRL + SHIFT +,** (čárka).|
|Přibližte konkrétní oblasti pomocí myši.|Pravé tlačítko myši podržte při kreslení obdélníku kolem této oblasti, které vás zajímají.|
|Změna velikosti a v okně mapu přizpůsobit velikosti.|Zvolte **přizpůsobit zobrazení** z **přiblížení** seznamu na panelu nástrojů mapy kódu.<br /><br /> - nebo -<br /><br /> Klikněte na tlačítko **přizpůsobit** ikonu ![ikona přiblížení na panelu nástrojů Mapa](../modeling/media/almcodemapzoomicon.png) na panelu nástrojů mapy kódu. Klávesnice: stiskněte **CTRL + 0** (nula).|
|Najdete uzel na mapě, podle názvu. **Tip:** tento postup funguje jenom pro položky na mapě. Chcete-li najít položky ve vašem řešení, ale ne na mapě, je v Najít **Průzkumníka řešení**a přetáhněte je do mapy. (Přetáhněte váš výběr, nebo **Průzkumníku řešení** nástrojů, klikněte na tlačítko **zobrazit na mapě kódu**).|1.  Zvolte **najít** ikonu ![ikonu hledání na panelu nástrojů Mapa](../modeling/media/almcodemapfindicon.png) na panelu nástrojů mapy kódu (klávesnice: stiskněte **CTRL + F**) zobrazíte do vyhledávacího pole v pravém horním rohu mapy.<br />2.  Zadejte název a stiskněte klávesu **vrátit** nebo klikněte na ikonu "Lupa". První položka, které odpovídají zadanému hledání: zobrazovat jako vybraný na mapě.<br />3.  Přizpůsobení vyhledávání, otevřete rozevírací seznam a zvolte možnost hledání. Možnosti jsou **najít další**, **najít předchozí**, a **Vybrat vše**. Klikněte na odpovídající tlačítko vedle textového pole hledání.<br />     ![Vyhledávání možnosti přetažení&#45;seznamu dolů](../modeling/media/almcodemapssearchdropdown.png)<br />     Můžete také pomocí klávesnice: stiskněte **F3** vybrat další odpovídající uzel nebo **SHIFT + F3** vybrat v předchozím odpovídající uzlu.<br />4.  Vyberte některou z možností, které určují způsob zpracování hledané termíny kliknutím na ikony pod textové pole pro hledání.<br />     ![Možnosti hledání shody](../modeling/media/almcodemapssearchmatchicons.png)<br />     Možnosti jsou zleva doprava, citlivé odpovídající malá a velká, Hledat pouze celá slova, používají syntaxi regulárního výrazu .NET, automaticky skupiny rozbalit a zobrazit shody uzavřené položek. **Důležité:** do vyhledávacího pole můžete použít k vyhledání shody v sbalené skupiny pouze v případě, že tyto skupiny byly rozbaleny dříve. Najít tyto shody a rozšiřovat své nadřazené skupiny automaticky, vyberte tuto možnost pod vyhledávacím polem.|
|Výběr všech nevybraných uzlů.|Otevřete místní nabídku zvolených uzlů. Zvolte **vyberte**, **Invertovat výběr**.|
|Zvolte Další uzly, které odkazují vybraných.|Otevřete místní nabídku zvolených uzlů. Zvolte **vyberte** a jedna z následujících:<br /><br /> – Chcete-li zvolit další uzly, které jsou propojeny přímo do vybraného uzlu, zvolte **příchozí závislosti**.<br />– Chcete-li zvolit další uzly, které jsou propojeny přímo ze zvoleného uzlu, zvolte **odchozí závislosti**.<br />– Chcete-li zvolit další uzly, které jsou propojeny přímo do a ze zvoleného uzlu, zvolte **obě**.<br />– Chcete-li vybrat všechny uzly, které jsou propojeny do a ze zvoleného uzlu, zvolte **připojený Podgraf**.<br />– Chcete-li vybrat všechny podřízené objekty vybraného uzlu, zvolte **podřízené**.|

##  <a name="FilterNodes"></a> Filtrování uzlů a propojení

|**k**|**Proveďte tyto kroky**|
|-|-|
|Umožňuje zobrazit nebo skrýt podokno filtry.|Zvolte **filtry** tlačítko na panelu nástrojů mapy kódu. **Filtry** podokně se zobrazí jako stránka s kartami v **Průzkumníka řešení**, ve výchozím nastavení.|
|Filtrovat typy uzlů, které jsou zobrazeny na mapě.|Nastavení nebo zrušte zaškrtnutí políček v **prvky kódu** seznamu v podokně filtry.|
|Filtrovat typy odkazů, které jsou zobrazeny na mapě.|Nastavení nebo zrušte zaškrtnutí políček v **vztahy** seznamu v podokně filtry.|
|Zobrazí nebo skryje testovací projekt uzly na mapě.|Nastavit nebo zrušit **testovací prostředky** zaškrtávací políčko ve **různé** seznamu v podokně filtry.|

Ikony se zobrazí na panelu legendy mapy, aby odrážely nastavení, které provedete v seznamu. Chcete-li zobrazit nebo skrýt panel legendy, klikněte na tlačítko **legendy** tlačítko na panelu nástrojů mapy kódu.

##  <a name="Inspect"></a> Prozkoumejte uzlům a propojením

Mapy kódu zobrazit tyto druhy odkazů:

-   Jednotlivé odkazy představují jeden vztah mezi dvěma uzly.

-   Propojení mezi skupinami znázorňuje vztah mezi dvěma uzly v různých skupinách.

-   Souhrnným odkazem představuje všechny vztahy, které odkazují ve stejném směru mezi dvěma skupinami.

> [!TIP]
> Ve výchozím nastavení zobrazuje propojení mezi skupinami pouze pro vybrané uzly na mapě. Chcete-li změnit toto chování můžete zobrazit nebo skrýt souhrnná propojení mezi skupinami, klikněte na tlačítko **rozložení** na kód mapování nástrojů a vyberte **Upřesnit**, pak **zobrazit všechny odkazy napříč skupinami** nebo **Skrýt všechny odkazy napříč skupinami**. Zobrazit [skrýt nebo zobrazit uzlům a propojením](#HidingShowing) další podrobnosti.

|**k**|**Proveďte tyto kroky**|
|-|-|
|Zobrazit další informace o uzlu nebo propojení.|Přesuňte ukazatel myši nad uzel nebo propojení, dokud se popisek nezobrazí.<br /><br /> Popisek pro agregované odkaz uvádí jednotlivé závislosti, které představuje.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro uzel nebo propojení. Zvolte **upravit**, **vlastnosti**.|
|Umožňuje zobrazit nebo skrýt obsah skupiny.|– Chcete-li rozbalit skupinu, otevřete místní nabídku pro uzel a zvolte **skupiny**, **Rozbalit**.<br />     - nebo -<br />     Přesuňte ukazatel myši nad uzel, dokud se nezobrazí tlačítko s dvojitou šipkou (šipku). Kliknutím na toto tlačítko rozbalte skupinu. Klávesnice: Chcete-li rozbalit nebo sbalit vybrané skupiny, stiskněte **PLUS** klíč (**+**) nebo **MINUS** klíč (**-**).<br />– Chcete-li sbalit skupinu, otevřete místní nabídku pro uzel a zvolte **skupiny**, **sbalit**.<br />     - nebo -<br />     Přesuňte ukazatel myši nad skupinu, dokud se nezobrazí tlačítko s dvojitou šipkou (nahoru šipka). Kliknutím na toto tlačítko Sbalit skupiny.<br />– Chcete-li rozbalit všechny skupiny, stiskněte **CTRL** + **A** vybrat na všech uzlech. Otevřete místní nabídku pro mapy a zvolte **skupiny**, **Rozbalit**. **Poznámka:** tento příkaz není k dispozici v případě, že rozšíření všech skupin generuje nepoužitelný mapy nebo problémy s pamětí. Doporučuje se rozšířit mapu pouze na úrovni podrobností, které vás zajímají.<br />-– Chcete li sbalit všechny skupiny, otevřete místní nabídku pro uzel nebo pro mapu. Zvolte **skupiny**, **Sbalit vše**.|
|Zobrazit definici kódu pro obor názvů, typ nebo člen.|Otevřete místní nabídku pro uzel a vyberte **přejít k definici**.<br /><br /> -nebo-<br /><br /> Dvojitým kliknutím na uzel. Rozšířené skupiny poklepejte na záhlaví ve skupině.<br /><br /> -nebo-<br /><br /> Vyberte uzel a stiskněte klávesu **F12**.<br /><br /> Příklad:<br /><br /> -Pro obor názvů obsahující jednu třídu otevře se soubor kódu pro třídu zobrazíte definici této třídy. V ostatních případech **výsledky hledáni symbolu** okno zobrazuje seznam souborů s kódem. **Poznámka:** při provádění této úlohy v oboru názvů jazyka Visual Basic nelze otevřít soubor kódu za obor názvů. Tento problém také vyvolá se v případě provedení této úlohy ve skupině vybraných uzlů, které obsahují obor názvů jazyka Visual Basic. Chcete-li tento problém obejít, přejděte na soubor kódu za obor názvů ručně nebo vynechejte uzel oboru názvů z výběru.<br />-Pro třídu nebo částečné třídy otevře soubor kódu pro danou třídu zobrazíte definici třídy.<br />-Pro metodu otevře soubor kódu pro nadřazené třídu zobrazíte definice metody.|
|Prozkoumejte závislostí a položek, které jsou součástí celkového propojení.|Vyberte odkazy zajímá a otevřete místní nabídku pro váš výběr. Zvolte **zobrazit přispívající vazby** nebo **zobrazit přispívající vazby na nové mapě kódu**.<br /><br /> Visual Studio rozbalí skupiny na obou koncích spojení a zobrazí pouze položky a závislosti, které se účastní odkazu. **Poznámka:** při zkoumání závislosti mezi položkami v částečné skupinách, může se zobrazit toto chování: <ul><li>Odkazy na položky, které nejsou součástí vašeho zkoumání zmizí z mapy, i když tyto odkazy stále existují.</li><li>Předpokládejme, že zkontrolujte odkaz na položku v částečné skupiny a poté zkontrolovat jiným propojením na stejnou položku. Během vašeho zkoumání druhý částečné cílová skupina zobrazuje pouze položky z prvního zkoumání. Odkazy a cílí na položky, které nebyly účastnit prvního zkoumání, ale součástí druhé zkoumání nejsou zobrazeny.</li></ul> Chcete-li zobrazit chybějící položky ze skupiny, zvolte **znovu načíst podřízené**![znovu načíst podřízené položky ikonu](../modeling/media/dependencygraph_deletednodesicon.png) (což znamená, že ne všechny členy skupiny se zobrazí na mapě). Můžete také zkusit vaše akce vrácení zpět (klávesnice: stiskněte **CTRL + Z**) a prozkoumejte závislostí na mapu s novým.|
|Prozkoumejte závislosti napříč několika uzly v různých skupinách.|Rozbalte skupiny, abyste si mohli zobrazit jeho podřízené položky. Vybere všechny uzly, které vás zajímat, včetně jejich podřízené prvky. Na mapě ukazuje propojení mezi skupinami mezi vybrané uzly.<br /><br /> Chcete-li vybrat všechny uzly ve skupině, stiskněte a podržte **SHIFT** a levé tlačítko myši při kreslení obdélníku kolem této skupiny. Chcete-li vybrat všechny uzly na mapě, stiskněte **CTRL**+**A**. **Tip:** zobrazení propojení mezi skupinami po celou dobu, zvolte **rozložení** na panelu nástrojů Mapa **Upřesnit**, **zobrazit všechny odkazy napříč skupinami**.|
|Zobrazit položky, které odkazuje na uzlu nebo propojení.|Otevřete místní nabídku pro uzel a vyberte **najít všechny odkazy**. **Poznámka:** to platí pouze tehdy, když `Reference` atribut je nastaven pro uzel nebo propojení v souboru .dgml na mapě. Chcete-li přidat odkazy na položky z uzlů a propojení, naleznete v tématu [mapy kódu přizpůsobit úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

##  <a name="HidingShowing"></a> Skrytí nebo zobrazení uzlů a propojení

Skrytí uzlů umožňuje vynechat tyto uzly při použití algoritmů rozložení. Ve výchozím nastavení jsou propojení mezi skupinami skryta. Propojení mezi skupinami jsou jednotlivá propojení, která spojují uzly mezi skupinami. Pokud jsou skupiny sbaleny, mapy agreguje všechny odkazy napříč skupinami do jediného propojení mezi skupinami. Pokud skupinu rozbalíte a vyberete v ní uzly, zobrazí se propojení mezi skupinami, která znázorňují závislosti v této skupině.

> [!CAUTION]
> Než budete sdílet mapy, který byl vytvořen v sadě Visual Studio Enterprise s uživateli používajícími systém Visual Studio Professional, ujistěte se, že chcete zobrazit všechny uzly nebo propojení mezi skupinami, které chcete, aby viděli i ostatní. V opačném případě uživatelé nebudou moci tyto položky zobrazit.

### <a name="to-hide-or-show-nodes"></a>Skrytí nebo zobrazení uzlů

|**k**|**Proveďte tyto kroky**|
|-|-|
|Skrytí vybraných uzlů.|1.  Vyberte uzly, které chcete skrýt.<br />2.  Otevřete místní nabídku zvolených uzlů nebo mapy. Zvolte **vyberte**, **skrýt vybrané**.|
|Skrytí nevybraných uzlů.|1.  Vyberte uzly, které mají zůstat viditelné.<br />2.  Otevřete místní nabídku zvolených uzlů nebo mapy. Zvolte **vyberte**, **Skrýt nevybrané**.|
|Zobrazit skryté uzly.|– Chcete-li zobrazit všechny skryté uzly ve skupině, nejdřív zkontrolujte, zda že je skupina rozbalena. Otevřete místní nabídku a zvolte **vyberte**, **odkrýt podřízené**.<br />     - nebo -<br />     Klikněte na tlačítko **odkrýt podřízené**![odkrýt podřízené položky ikonu](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) ikony v levém horním rohu skupiny (to je viditelná pouze v případě, že jsou skryté podřízené uzly).<br />– Chcete-li zobrazit všechny skryté uzly, otevřete místní nabídku pro mapy nebo uzlu a zvolte **vyberte**, **zobrazit všechny**.|

### <a name="to-hide-or-show-links"></a>Skrýt nebo zobrazit odkazy

|**k**|**Na panelu nástrojů Mapa zvolte rozložení, pokročilé a klikněte na tlačítko**|
|-|-|
|Zobrazení propojení mezi skupinami za všech okolností.|**Zobrazit všechny odkazy napříč skupinami**. Tím budou skryta souhrnná propojení mezi skupinami.|
|Skrytí propojení mezi skupinami za všech okolností.|**Skrýt všechny odkazy napříč skupinami**|
|Zobrazit pouze odkazy napříč skupinami pro vybrané uzly.|**Zobrazit odkazy napříč skupinami pro vybrané uzly**|
|Skryjte všechny odkazy.|**Skrýt všechny odkazy**. Chcete-li znovu zobrazit odkazy, zvolte jeden z výše uvedených možností.|

##  <a name="OrganizeGroups"></a> Seskupování uzlů

|**k**|**Proveďte tyto kroky**|
|-|-|
|Zobrazit uzly kontejneru jako uzlů skupin nebo listových uzlů.|Chcete-li zobrazit uzly kontejneru jako listové: vyberte uzly, otevřete místní nabídku pro váš výběr a zvolte **skupiny**, **převést do listu**.<br /><br /> Chcete-li zobrazit uzly kontejneru jako uzly skupiny: vyberte uzly, otevřete místní nabídku pro váš výběr a zvolte **skupiny**, **převést do skupiny**.|
|Změna rozložení uvnitř skupiny.|Vyberte skupinu, otevřete místní nabídku, vyberte **rozložení**a vyberte požadovaný styl rozložení.<br /><br /> - nebo -<br /><br /> 1.  Vyberte skupinu a ujistěte se, že je rozbalený.<br />2.  Znovu klikněte na záhlaví skupiny a zobrazí se panel nástrojů skupiny.<br />     ![Graf závislosti &#45; nástrojů skupiny](../modeling/media/dependencygraph_group.png)<br />3.  Otevřít **změnit styl rozložení skupiny** seznamu ![graf závislosti &#45; nástrojů skupiny &#45; rozložení](../modeling/media/dependencygraph_grouptoolbar.gif) a zvolte požadovaný styl rozložení.<br /><br /> **Zobrazení seznamu** mění uspořádání členů do seznamu. **Výchozí rozhraní Graph** obnoví do výchozího rozložení mapy rozložení skupiny. Další možnosti najdete v tématu [změnit rozložení mapy](#Selecting).|
|Přidáte uzel do skupiny.|Přetáhněte uzel do skupiny.<br /><br /> Při přetahování uzlu Visual Studio zobrazí indikátor zobrazíte, že přesouváte uzlu.<br /><br /> Uzly lze přetáhnout také mimo skupinu.|
|Přidání uzlu do uzlu bez skupiny.|Přetáhněte uzel na cílový uzel. Žádné cílový uzel do skupiny můžete převést tak, že přidáte uzly k němu.|
|Seskupte vybrané uzly.|1.  Vyberte uzly, které chcete seskupit. Rozbalovací panel nástrojů se zobrazí nad poslední uzel, který jste vybrali.<br />     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)<br />2.  Na panelu nástrojů zvolte ikonu čtvrtý **seskupit vybrané uzly** (Pokud je rozbalený uzel bude mít pět místo čtyři ikony). Zadejte název nové skupiny a stiskněte klávesu **vrátit**.<br />     - nebo -<br />     Vyberte uzly, které chcete seskupit a otevřete místní nabídku pro váš výběr. Zvolte **skupiny**, **přidat nadřazenou skupinu**, zadejte název nové skupiny a stiskněte klávesu **vrátit**.<br /><br /> Skupinu lze přejmenovat. Otevřete místní nabídku pro skupiny a zvolte **upravit**, **vlastnosti** otevřete okno vlastností Visual Studio. V **popisek** vlastnosti skupiny podle potřeby.|
|Odeberte skupiny.|Vyberte skupinu nebo skupiny, které mají být odstraněny. Otevřete místní nabídku pro váš výběr a zvolte **skupiny**, **odstranit skupinu**.|
|Odeberte uzly ze své nadřazené skupiny.|Vyberte uzly, které mají být odebrány. Otevřete místní nabídku pro váš výběr a zvolte **skupiny**, **odebrat z nadřazeného**. Tím uzly až na druhé úrovně nebo na mimo skupinu Pokud mají skupinu druhé úrovně.<br /><br /> - nebo -<br /><br /> Vyberte uzly a přetáhněte je ze skupiny.|

##  <a name="AddRemoveNodesLinks"></a> Přidat, odebrat nebo přejmenovat uzly, odkazy a komentáře

Pokud chcete procházet hierarchii nebo pro zjednodušení mapy, můžete zobrazit více nebo méně položek na mapě. Můžete také přejmenovat položky a přidání komentářů do položky.

> [!CAUTION]
> Než budete sdílet mapy, která byla vytvořena pomocí sady Visual Studio Enterprise s těmi, kteří používají Visual Professional, ujistěte se, že všechny prvky kódu, který chcete, aby viděli i ostatní jsou viditelné na mapě. V opačném případě nebudou tito uživatelé se nepovedlo načíst prvky odstraněné kódu.

### <a name="add-a-node-for-a-code-element"></a>Přidat uzel pro prvek kódu

|**k**|**Proveďte tyto kroky**|
|-|-|
|Přidáte nový obecný uzel na aktuální pozici ukazatele myši.|1.  Přesuňte ukazatel myši na místo na mapě ve které chcete vložit nový prvek kódu a stiskněte klávesu **vložit**.<br />     - nebo -<br />     Otevřete místní nabídku pro mapy a zvolte **upravit**, **přidat**, **obecný uzel**.<br />2.  Zadejte název pro nový uzel a stiskněte klávesu **vrátit**.|
|Přidáte konkrétního typu uzlu element kódu na aktuální pozici ukazatele myši.|1.  Přesuňte ukazatel myši na místo na mapě ve které chcete vložit nový prvek kódu a otevřete místní nabídku pro mapu.<br />2.  Zvolte **upravit**, **přidat**a vyberte typ uzlu chcete.<br />3.  Zadejte název pro nový uzel a stiskněte klávesu **vrátit**.|
|Přidání obecného nebo konkrétního typu uzlu element kódu do skupiny.|1.  Vyberte uzel skupiny a otevřete místní nabídku.<br />2.  Zvolte **upravit**, **přidat**a vyberte typ uzlu chcete.<br />3.  Zadejte název pro nový uzel a stiskněte klávesu **vrátit**.|
|Přidat nový uzel stejného typu a odkazované z existující uzel.|1.  Vyberte element kódu. Rozbalovací panel nástrojů se zobrazí nad ním.<br />     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)<br />2.  Na panelu nástrojů zvolte druhou ikonu **vytvořit uzel se stejnou kategorií jako má tento uzel a přidat nový odkaz na něj**.<br />3.  Vyberte místo na mapě vložit nový prvek kódu a klikněte na tlačítko levé tlačítko myši.<br />4.  Zadejte název pro nový uzel a stiskněte klávesu **vrátit**.|
|Přidáte nový obecný uzel, který je propojený z existujícího prvku kódu, který má právě fokus.|1.  Pomocí klávesnice, stiskněte klávesu **kartu** dokud prvek kódu k propojení z má fokus (tečkovaná obdélník).<br />2.  Stisknutím klávesy **Alt**+**vložit**.<br />3.  Zadejte název pro nový uzel a stiskněte klávesu **vrátit**.|
|Přidáte nový obecný uzel, který odkazuje na existující prvek kódu, který má právě fokus.|1.  Pomocí klávesnice, stiskněte klávesu **kartu** dokud odkaz na prvek kódu má fokus (tečkovaná obdélník).<br />2.  Stisknutím klávesy **Alt**+**Shift**+**vložit**.<br />3.  Zadejte název pro nový uzel a stiskněte klávesu **vrátit**.|

|**Chcete-li přidat prvky kódu pro**|**Proveďte tyto kroky**|
|-|-|
|Prvky kódu v řešení.|1.  Najít element kódu v **Průzkumníka řešení**. Použití **Průzkumníka řešení** vyhledávacího pole nebo řešení procházejte. **Tip:** najít prvky kódu, které mají závislosti na typu nebo člena, otevřete místní nabídku pro typ nebo člen v **Průzkumníka řešení**. Vyberte vztah, který vás zajímá. **Průzkumník řešení** zobrazuje pouze prvky kódu se zadanými závislostmi.<br />2.  Přetáhněte prvky kódu, které vás zajímají mapy povrchu. Můžete také přetáhnout prvky kódu ze zobrazení tříd nebo prohlížeči objektů.<br />     - nebo -<br />     V **Průzkumníka řešení**, vyberte prvky kódu, které chcete propojit. Potom na **Průzkumníka řešení** nástrojů, klikněte na tlačítko **zobrazit na mapě kódu**.<br /><br /> Ve výchozím nastavení hierarchie nadřazeného kontejneru pro nové prvky kódu se zobrazí na mapě. Použití **zahrnout nadřazené položky** tlačítko na panelu nástrojů mapy kódu ke změně tohoto chování. Při vypnuté, pouze kód elementu samotného je přidán do mapování. Chcete stornovat toto chování pro pouze jednu přetáhněte přetažení akce, když stisknete a podržíte **CTRL** klíče při přetažení prvků kódu do mapy.<br /><br /> Visual Studio přidá prvky kódu pro elementy kódu nejvyšší úrovně ve výběru. Pokud chcete zobrazit, pokud prvek kódu obsahuje další prvky kódu, přesuňte ukazatel myši nad prvek kódu tak, aby zobrazil na dvojitou šipku (šipku). Kliknutím na dvojitou šipku a rozbalte prvek kódu. Chcete-li rozbalit všechny prvky kódu, stiskněte **CTRL**+**A** vybrat všechny elementy, otevřete místní nabídku pro mapy a zvolte **skupiny**, **Expand** . Tento příkaz není k dispozici, pokud že rozšíření všech skupin by vytvořit mapu nepoužitelná nebo způsobit nedostatek problémy s pamětí.|
|Prvky kódu související s prvky kódu na mapě.|Klikněte na tlačítko **zobrazit související** tlačítko na panelu nástrojů Mapa kódu a zvolte typ související položky, které vás zajímají.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro prvek kódu. Vyberte jednu z **zobrazení...**  položky nabídky v závislosti na druh vztahu, který vás zajímá. Můžete například zobrazit položky, které odkazuje na aktuální položky, položky, které odkazují na aktuální položku, základní a odvozené typy pro třídy, volající metodě a obsahující třídy, obory názvů a sestavení.<br /><br /> Další podrobnosti najdete v tématu [v tomto tématu](../modeling/map-dependencies-across-your-solutions.md).|
|Zkompilovaná sestavení .NET (.dll nebo .exe) nebo binární soubory.|Přetáhněte sestavení nebo binární soubory z mimo sadu Visual Studio do mapy.<br /><br /> Můžete přetáhnout z Průzkumníka Windows nebo Průzkumníka souborů pouze v případě, že spustíte ho a sady Visual Studio na stejné úrovni oprávnění řízení přístupu uživatele (UAC). Například pokud je zapnutý nástroj Řízení uživatelských účtů a používáte Visual Studio jako správce, Průzkumník Windows nebo Průzkumníka souborů zablokuje možnost přetahování.|

###  <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Přidání propojení mezi stávající elementy kódu

1. Vyberte požadovaný prvek zdrojového kódu. Panel nástrojů se zobrazí nad prvek kódu.

    ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2. Na panelu nástrojů zvolte ikonu první **vytvořit nové propojení z tohoto uzlu na který následně uzel, který můžete kliknout na další**.

3. Vyberte cílový prvek kódu. Zobrazí se propojení mezi elementy dvou kódu.

**OR**

1. Vyberte požadovaný prvek zdrojového kódu na mapě.

2. Pokud máte nainstalovaný myš, přesuňte ukazatel myši mimo hranice mapy.

3. Otevřete místní nabídku prvku kódu a zvolte **upravit** > **přidat** > **obecný odkaz**.

4. Na kartě a vyberte cílový prvek kódu pro odkaz.

5. Stisknutím klávesy **zadejte**.

###  <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Přidání komentáře k existující uzel na mapě

1.  Vyberte element kódu. Panel nástrojů se zobrazí nad ním.

     ![Panel nástrojů grafu závislostí](../modeling/media/depedencygraph_toolbar.png)

2.  Na panelu nástrojů zvolte ikonu třetí **vytvořit nový uzel komentáře s novým propojením na vybraný uzel**.

     \- nebo –

     Otevřete místní nabídku pro prvek kódu a zvolte **upravit** > **nový komentář**.

3.  Zadejte komentáře. Chcete-li zadat na nový řádek, stiskněte **Shift** + **Enter**.

#### <a name="add-a-comment-to-the-map-itself"></a>Přidat komentář do samotného mapy

1.  Otevřete místní nabídku pro mapy a zvolte **upravit** > **nový komentář**.

2.  Zadejte komentáře. Chcete-li zadat na nový řádek, stiskněte **Shift** + **Enter**.

###  <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Přejmenovat element kódu nebo odkaz

1.  Vyberte prvek kódu nebo odkaz, který chcete přejmenovat.

2.  Stisknutím klávesy **F2**, nebo otevřete místní nabídku a zvolte **upravit** > **přejmenovat**.

3.  Když se zobrazí textové pole na mapě, přejmenujte na prvek kódu nebo odkaz.

**OR**

1.  Otevřete místní nabídku a zvolte **upravit** > **vlastnosti**.

2.  Upravit **popisek** vlastností v okně vlastností Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Odebere prvek kódu nebo odkaz z mapy

1.  Vyberte prvek kódu nebo odkaz a stiskněte klávesu **odstranit** klíč.

     \- nebo –

     Otevřete místní nabídku pro prvek kódu nebo odkaz a zvolte **upravit** > **odebrat**.

2.  Pokud odkaz na element je součástí skupiny, **znovu načíst podřízené** tlačítko ![znovu načíst podřízené položky ikonu](../modeling/media/dependencygraph_deletednodesicon.png) se zobrazí uvnitř skupiny. Klepnutím na toto tlačítko Načíst chybějící prvky a odkazy.

-   Prvky kódu a odkazy můžete odebrat z mapy bez ovlivnění původního kódu. Pokud je odstraníte, jejich definice odebrány ze souboru DGML (.dgml).

-   Mapy vytvořeny úpravou DGML, přidáním prvky nedefinované kódu nebo s použitím některých starších verzích sady Visual Studio nepodporují tuto funkci.

#### <a name="flag-a-code-element-for-follow-up"></a>Příznak prvek kódu pro zpracování

1.  Vyberte prvek kódu nebo odkaz, který chcete označit, že pro zpracování.

2.  Otevřete místní nabídku a zvolte **upravit** > **nastavit příznak pro zpracování**.

-   Ve výchozím nastavení získá prvek kódu červená na pozadí. Vezměte v úvahu [přidáte komentář](#AddComments) přes příslušné zpracování informace.

-   Změna barvy pozadí elementu nebo zrušte příznak pro zpracování výběrem **upravit** > **jiné barvy příznak**.

##  <a name="ChangeStyleCodeOrLink"></a> Změnit styl kódu elementu nebo propojení

Můžete změnit ikony na prvky kódu a barvy prvky kódu a propojení pomocí předdefinované ikony a barvy. Můžete například zvolit barvu pro zvýraznění prvky kódu a odkazy, které mají určité kategorie nebo vlastnost. To vám umožní identifikovat a zaměřit se na konkrétní oblasti na mapě. Můžete zadat vlastní ikony a barvy úpravou souboru .dgml na mapě. Zobrazit [mapy kódu přizpůsobit úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Použít předdefinované barvy nebo ikony pro prvky kódu nebo propojení s konkrétní kategorií nebo vlastností

1.  Na panelu nástrojů Mapa **legendy**.

2.  V **legendy** pole, podívejte se, pokud kód element kategorie nebo vlastnost již zobrazuje v seznamu.

3.  Pokud seznam neobsahuje kategorii ani vlastnost, zvolte **+** v **legendy** pole a pak zvolte **vlastnost uzlu**, **kategorie uzlu** , **Vlastnost propojení**, nebo **propojit kategorie**. Zvolte vlastnost nebo kategorie. Kategorie nebo vlastnost se teď zobrazí v **legendy** pole.

    > [!NOTE]
    > Chcete-li vytvořit a přiřadit kategorie nebo vlastnosti pro prvek kódu, můžete upravit na mapě souboru .dgml. Zobrazit [mapy kódu přizpůsobit úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4.  V **legendy** pole, klikněte na ikonu vedle kategorie nebo vlastnosti, které jste přidali nebo chcete změnit.

5.  Pro výběr stylu, který chcete změnit, použijte následující tabulku:

    |**Chcete-li změnit**|**Zvolte**|
    |-|-|
    |Barvu pozadí|**Na pozadí**|
    |Barva obrysu|**Tahu**|
    |Barva textu (zobrazení výsledků se zobrazí písmeno "f")|**Popředí**|
    |Ikona|**Ikony**|

     **Výběr sady barev** nebo **výběr sady ikon** zobrazí se dialogové okno pro výběr barvy nebo ikony.

6.  V **výběr sady barev** nebo **výběr sady ikon** dialogové okno, proveďte jednu z následujících akcí:

    |**Chcete-li použít**|**Proveďte tyto kroky**|
    |-|-|
    |Sada barvy nebo ikony|Otevřít **vyberte barvu** (nebo **ikonu**) **nastavit** seznamu. Vyberte sadu barev nebo ikon.|
    |Určité barvy nebo ikony|Otevřete seznam hodnot kategorií nebo vlastností. Výběr barvy nebo ikony.|

    > [!NOTE]
    > Změna uspořádání, odstranit nebo dočasně zakázat styly **legendy** pole. Zobrazit [úprava pole Legenda](#ModifyLegend).

##  <a name="ModifyLegend"></a> Úprava pole Legenda

Změna uspořádání, odstranit nebo dočasně zakázat styly **legendy** pole:

1.  Otevřete místní nabídku pro styl v **legendy** pole.

2.  Proveďte některou z následujících úloh:

    |**k**|**Zvolte**|
    |-|-|
    |Deaktivovat prvek kódu|**Zakázat**|
    |Odstranit prvek kódu|**Delete**|
    |Přesunutí stylu nahoru|**Posunout nahoru**|
    |Dolů na prvek kódu|**Přesunout dolů**|

##  <a name="CopyLegend"></a> Kopírování stylů z jednoho do jiného

1.  Ujistěte se, že **legendy** pole se zobrazí na mapě zdroje. Pokud není zobrazená, na panelu nástrojů mapy, klikněte na tlačítko **legendy**.

2.  Otevřete místní nabídku **legendy** pole. Zvolte **kopírovat legendu**.

3.  Vložte legendu do cílového mapy.

##  <a name="MergeMaps"></a> Sloučit map kódu

Maps můžete sloučit zkopírováním a vložením prvky kódu mezi mapy. Pokud se shodují identifikátory prvek kódu, pak funkce vkládání kódu prvky, jako jsou operace sloučení. Pro usnadnění tohoto úkolu vložte všechna sestavení nebo binární soubory, které chcete zobrazit ve stejné složce, takže úplná cesta každého sestavení nebo binární soubor je stejný pro každé mapování, které chcete sloučit.

Alternativně můžete přetáhnout těchto sestavení nebo binární soubory do stejné mapy, z této složky.

## <a name="see-also"></a>Viz také

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Referenční dokumentace jazyka přímého značení grafů (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
