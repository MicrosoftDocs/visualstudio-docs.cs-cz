---
title: Mapování závislostí napříč vašimi řešeními | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d70016229ad9599c7ededbefaf08744f2bb6f351
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548080"
---
# <a name="map-dependencies-across-your-solutions"></a>Mapování závislostí napříč vaším řešením
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete pochopit závislosti napříč vaším kódem, Vizualizujte si je vytvořením map kódu. To vám pomůže zjistit, jak se kód vejde do společné bez čtení souborů a řádků kódu.

 ![Zobrazení závislostí napříč vaším řešením](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

 **Tady jsou některá videa**:

- [Pochopení závislostí kódu pomocí vizualizace](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)

- [Vizualizace dopadu změny](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)

- [Porozumění komplexnímu kódu pomocí map kódu](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understanding-complex-code-with-Code-Map-ENU)

## <a name="get-started-with-code-maps"></a><a name="GetStarted"></a> Začínáme s mapami kódu
 Pokud **chcete použít mapy kódu, budete potřebovat jednu z těchto**akcí:

- Visual Studio Enterprise: vytváření map kódu z editoru kódu, Průzkumník řešení, Zobrazení tříd nebo Prohlížeč objektů.

- Visual Studio Professional: Otevřete mapy kódu, udělejte omezené úpravy a přejděte do kódu.

> [!WARNING]
> Před sdílením map vytvořených v Visual Studio Enterprise s jinými uživateli, kteří používají Visual Studio Professional, se ujistěte, že jsou viditelné všechny položky na mapě (například skryté položky, rozšířené skupiny a odkazy křížové skupiny).

 **Závislosti pro kód můžete mapovat v těchto jazycích**:

- Visual C# .NET nebo Visual Basic .NET v řešení nebo sestaveních (. dll nebo. exe)

- Nativní nebo spravovaný kód jazyka C nebo C++ v Visual C++ projekty, soubory hlaviček (. h nebo `#include` ) nebo binární soubory

- Projekty X + + a sestavení vytvořená z modulů .NET pro Microsoft Dynamics AX

  **Poznámka:** Pro jiné projekty než C# nebo Visual Basic .NET existuje méně možností pro spuštění mapy kódu nebo přidávání položek do existující mapy kódu. Například nelze kliknout pravým tlačítkem myši na objekt v textovém editoru projektu jazyka C++ a přidat jej do mapy kódu. Jednotlivé prvky nebo soubory kódu však lze přetáhnout z Průzkumník řešení, Zobrazení tříd a Prohlížeč objektů.

#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Zobrazení celkových závislostí napříč vaším řešením

1. Otevřete nabídku **architektury** .

2. Pokud jste řešení právě otevřeli a ještě jste ho nesestavili nebo pokud se váš kód od jeho posledního vytvoření změnil, vyberte **pro řešení vygenerovat mapu kódu**.

3. Pokud se váš kód od posledního sestavení nezměnil, vyberte možnost **Generovat mapu kódu pro řešení bez sestavení** , abyste při vytváření mapy dosáhli rychlejšího výkonu.

4. [Podívejte se na celkové závislosti](#SeeOverviewSource) , které vám pomohou pochopit, jak můžete použít mapy kódu k zobrazení celkových závislostí napříč vaším řešením.

#### <a name="to-see-specific-dependencies-within-your-solution"></a>Zobrazení specifických závislostí ve vašem řešení

1. Když je vaše řešení načtené, otevřete **Průzkumník řešení**.

2. Vyberte všechny projekty, odkazy na sestavení, složky, soubory, typy nebo členy, které chcete namapovat.

3. Na panelu nástrojů **Průzkumník řešení** klikněte na tlačítko **Zobrazit na mapě kódu**![vytvořit nový graf z vybraných uzlů](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton"). Nebo otevřete místní nabídku a vyberte možnost **Zobrazit na mapě kódu**. Můžete také přetáhnout položky z Zobrazení tříd nebo Prohlížeč objektů do nového nebo existujícího mapování kódu.

4. [Viz konkrétní závislosti](#SeeSpecificSource) , které vám pomohou pochopit, jak můžete pomocí map kódu zobrazit konkrétní závislosti ve vašem řešení.

### <a name="to-add-a-new-empty-code-map-to-your-solution"></a><a name="CreateEmptyMap"></a> Přidání nového prázdného mapování kódu do řešení

1. V **Průzkumník řešení**otevřete místní nabídku uzlu řešení nejvyšší úrovně. Zvolte **Přidat** a pak zvolte **Nová položka**.

2. V části **nainstalováno**vyberte možnost **Obecné**.

3. V pravém podokně vyberte možnost **dokument orientovaného grafu** a pak klikněte na tlačítko **Přidat**.

     Nyní máte prázdnou mapu, která se zobrazí ve složce **položky řešení** vašeho řešení.

#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Chcete-li vytvořit novou prázdnou mapu kódu bez přidání do vašeho řešení

1. Otevřete nabídku **Architektura** a vyberte možnost **Nová mapa kódu**.

     \- ani

2. Otevřete nabídku **soubor** a zvolte položku **Nový** a zvolte možnost **soubor**.

3. V části **nainstalováno**vyberte možnost **Obecné**.

4. V pravém podokně vyberte možnost **dokument orientovaného grafu** a pak zvolte možnost **otevřít**.

     Nyní máte prázdnou mapu, která se nezobrazí ve složkách vašeho řešení.

## <a name="see-overall-dependencies"></a><a name="SeeOverviewSource"></a> Zobrazit celkové závislosti

### <a name="see-dependencies-across-your-solution"></a><a name="OverviewSource"></a> Zobrazení závislostí napříč vaším řešením

1. V nabídce **Architektura** vyberte možnost **Generovat mapu kódu pro řešení**.

    ![Vytvoření mapy kódu – příkaz](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")

    Získáte mapu, která zobrazuje sestavení nejvyšší úrovně a agregované odkazy mezi nimi. Širší agregovaný odkaz, který představuje více závislostí.

2. Použijte tlačítko **Legenda** na panelu nástrojů mapa kódu k zobrazení nebo skrytí seznamu ikon typu projektu (například testovací, webové a telefonní projekty), položek kódu (například tříd, metod a vlastností) a typů vztahů (například dědění z, Implements a Calls).

    ![Graf závislosti nejvyšší úrovně&#45;sestavení](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")

    Tento příklad řešení obsahuje složky řešení (**testy** a **komponenty**), projekty testů, webové projekty a sestavení. Ve výchozím nastavení se všechny vztahy zahrnutí zobrazí jako *skupiny*, které můžete rozbalit nebo sbalit. Skupina **externals** obsahuje cokoli mimo vaše řešení, včetně závislostí platformy. Externí sestavení obsahuje pouze položky, které jsou používány. Ve výchozím nastavení jsou systémové základní typy na mapě skryté, aby se snížila přehlednost.

3. Chcete-li přejít k podrobnostem o mapě, rozbalte skupiny, které reprezentují projekty a sestavení. Můžete rozbalit vše stisknutím **kombinace kláves CTRL + a** a vybrat všechny uzly a pak vybrat **skupinu**a **Rozbalit** z místní nabídky.

    ![Rozbalování všech skupin v mapě kódu](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")

4. To však nemusí být užitečné pro velké řešení. V případě složitých řešení vám možná omezení paměti brání v rozšiřování všech skupin. Místo toho, abyste viděli v rámci jednotlivého uzlu, rozbalte ho. Přesuňte ukazatel myši nad uzel a pak klikněte na dvojitou šipku (šipka dolů), když se objeví.

    ![Rozbalení uzlu v mapě kódu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

    Nebo použijte klávesnici tak, že vyberete položku a stisknete klávesu plus ( **+** ). Chcete-li prozkoumat hlubší úrovně kódu, proveďte stejný pro obory názvů, typy a členy.

   > [!TIP]
   > Další podrobnosti o práci s mapami kódu pomocí myši, klávesnice a dotykového ovládání najdete v tématu [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

5. Chcete-li zjednodušit mapu a soustředit se na jednotlivé části, zvolte možnost **filtry** na panelu nástrojů mapa kódu a vyberte pouze typy uzlů a odkazy, které vás zajímají. Můžete například skrýt všechny složky řešení a kontejnery sestavení.

    ![Zjednodušení mapy filtrováním kontejnerů](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")

    Mapu můžete také zjednodušit skrytím nebo odebráním jednotlivých skupin a položek z mapy, aniž by to ovlivnilo základní kód řešení.

6. Chcete-li zobrazit vztahy mezi položkami, vyberte je na mapě. Barvy odkazů označují typy vztahů, jak je znázorněno v podokně **Legenda** .

    ![Zobrazení závislostí napříč vaším řešením](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

    V tomto příkladu fialové odkazy jsou voláním, tečkované odkazy jsou odkazy a světle modré odkazy jsou přístup k poli. Zelené odkazy mohou být děděny nebo mohou být *agregované odkazy* , které označují více než jeden typ vztahu (nebo *kategorie*).

   > [!TIP]
   > Pokud vidíte zelený odkaz, nemusí to znamenat pouze vztah dědičnosti. Může to být také volání metody, ale vztah dědičnosti je skrytý. Chcete-li zobrazit konkrétní typy odkazů, můžete pomocí zaškrtávacích políček v podokně **filtry** skrýt typy, které vás zajímají.

7. Chcete-li získat další informace o položce nebo propojení, přesuňte ukazatel nad něj, dokud se nezobrazí popisek. To ukazuje podrobnosti prvku kódu nebo kategorií, které odkaz představuje.

    ![Zobrazit kategorie vztahu](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")

8. Chcete-li prošetřit položky a závislosti reprezentované agregovaným odkazem, nejprve vyberte odkaz a pak otevřete místní nabídku. Vyberte **Zobrazit přispívající odkazy** (nebo **Zobrazit přispívající odkazy na nové mapě kódu**). Tím se rozbalí skupiny na obou koncích propojení a zobrazí se jenom položky a závislosti, které se účastní odkazu.

9. Pokud se chcete zaměřit na konkrétní části mapy, můžete i nadále odebírat položky, které vás zajímají. Chcete-li například přejít k zobrazení tříd a členů, jednoduše vyfiltrujte všechny uzly oboru názvů v podokně **filtry** .

     ![Přechod na úroveň třídy a člena](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")

10. Dalším způsobem, jak se zaměřit na složitou mapu řešení, je vytvoření nové mapy obsahující vybrané položky z existující mapy. Podržte stisknutou **klávesu CTRL** a vyberte položky, na kterých se chcete zaměřit, otevřete místní nabídku a zvolte možnost **Nový graf z výběru**.

     ![Zobrazit vybrané položky na nové mapě kódu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

11. Obsažený kontext je převedený na novou mapu. Pomocí podokna **filtry** skryjte složky řešení a další kontejnery, které nechcete zobrazit.

     ![Filtrování kontejnerů pro zjednodušení zobrazení](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")

12. Rozbalením skupin a výběrem položek v mapě zobrazíte relace.

     ![Vyberte položky pro zobrazení vztahů](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")

    Viz také:

- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)

- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

- Vyhledejte potenciální problémy v kódu [spuštěním analyzátoru](../modeling/find-potential-problems-using-code-map-analyzers.md).

### <a name="see-dependencies-across-assemblies-or-binaries"></a><a name="OverviewCompiled"></a> Zobrazit závislosti mezi sestaveními nebo binárními soubory

1. [Vytvořte prázdnou mapu kódu](#GetStarted)nebo otevřete existující mapu kódu (soubor. dgml).

2. Přetáhněte sestavení nebo binární soubory, které chcete namapovat mimo Visual Studio na mapu. Například přetáhněte sestavení nebo binární soubory z Průzkumníka Windows nebo Průzkumníka souborů.

> [!NOTE]
> Sestavení nebo binární soubory můžete přetáhnout z Průzkumníka Windows nebo Průzkumníka souborů jenom v případě, že je spouštíte a Visual Studio na stejné úrovni oprávnění User Access Control (UAC). Pokud je například zapnutý nástroj řízení uživatelských účtů a používáte aplikaci Visual Studio jako správce, Průzkumník Windows nebo Průzkumník souborů zablokuje operaci přetažení. Pokud chcete tento problém obejít, ujistěte se, že obě jsou spuštěné se stejnou úrovní oprávnění, nebo vypněte nástroj řízení uživatelských účtů.

## <a name="see-specific-dependencies"></a><a name="SeeSpecificSource"></a> Zobrazit konkrétní závislosti
 Předpokládejme například, že máte revizi kódu, který se provede v některých souborech s probíhajícími změnami. Chcete-li zobrazit závislosti v těchto změnách, můžete z těchto souborů vytvořit mapu kódu.

 ![Zobrazit konkrétní závislosti na mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

### <a name="see-specific-dependencies-in-your-solution"></a>Zobrazit konkrétní závislosti ve vašem řešení

1. Otevřete **Průzkumník řešení**. Vyberte projekty, odkazy na sestavení, složky, soubory, typy a členy, které vás zajímají. Chcete-li najít položky, které mají závislosti na typech nebo členech, otevřete místní nabídku typu nebo člena z **Průzkumník řešení**. Zvolte typ závislosti a pak vyberte výsledky.

2. Namapujte položky a jejich členy. Na panelu nástrojů **Průzkumník řešení** klikněte na tlačítko **Zobrazit na mapě kódu**![vytvořit nový graf z vybraných uzlů](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").

     ![Vyberte položky, které chcete namapovat.](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")

3. Mapa zobrazuje vybrané položky v rámci jejich obsahující sestavení.

     ![Vybrané položky zobrazené jako skupiny na mapě](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")

     Můžete také přetáhnout položky z Průzkumník řešení, Zobrazení tříd nebo Prohlížeč objektů do prázdné nebo do existující mapy kódu. Chcete-li vytvořit prázdnou mapu, přečtěte si téma [Vytvoření prázdného mapování kódu](#GetStarted). Chcete-li zahrnout nadřazenou hierarchii pro vaše položky, stiskněte a podržte klávesu **CTRL** při přetahování položek nebo použijte tlačítko **Zahrnout nadřazené** položky na panelu nástrojů mapa kódu a určete výchozí akci.

    > [!NOTE]
    > Když přidáváte položky z projektu, který je sdílen napříč více aplikacemi, jako jsou Windows Phone nebo Windows Store, tyto položky se zobrazí na mapě s aktuálně aktivním projektem aplikace. Pokud změníte kontext na jiný projekt aplikace a přidáte další položky ze sdíleného projektu, tyto položky se nyní zobrazí s nově aktivním projektem aplikace. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.

4. Chcete-li prozkoumat položky, rozbalte je. Přesuňte ukazatel myši nad položku a potom po zobrazení klikněte na ikonu s dvojitou šipkou (šipka dolů).

     ![Rozbalení uzlu v mapě kódu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

     Chcete-li rozbalit všechny položky, vyberte je pomocí **kombinace kláves CTRL + a**, otevřete místní nabídku pro mapu a zvolte možnost **Skupina**a **rozbalte položku**. Tato možnost není k dispozici, pokud rozšíření všech skupin vytvoří nepoužitou mapu nebo problémy s pamětí.

5. V případě potřeby dál Rozšiřte položky, které vás zajímají, na úrovni třídy a člena.

     ![Rozbalení skupin na úrovni třídy a člena](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")

     Chcete-li zobrazit členy, kteří jsou v kódu, ale nezobrazují se na mapě, klikněte na ![ikonu znovu](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") **načíst podřízené** položky v levém horním rohu skupiny.

6. Chcete-li zobrazit další položky týkající se těch na mapě, vyberte je a zvolte možnost **Zobrazit související** na panelu nástrojů mapa kódu a pak vyberte typ souvisejících položek, které chcete přidat do mapy. Případně vyberte jednu nebo více položek, otevřete místní nabídku a klikněte na tlačítko **Zobrazit...** možnost pro typ souvisejících položek, které mají být přidány do mapy. Příklad:

     V případě **sestavení**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit sestavení s odkazy**|Přidejte sestavení, na které odkazuje toto sestavení. Externí sestavení se zobrazí ve skupině **externí** typy.|
    |**Zobrazit sestavení odkazující na tuto**|Přidejte sestavení do řešení, která odkazují na toto sestavení.|

     V případě **oboru názvů**vyberte možnost **Zobrazit obsahující sestavení**, pokud není viditelná.

     Pro **třídu** nebo **rozhraní**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit základní typy**|V případě třídy přidejte základní třídu a implementovaná rozhraní.<br /><br /> V rámci rozhraní přidejte základní rozhraní.|
    |**Zobrazit odvozené typy**|V případě třídy přidejte odvozené třídy.<br /><br /> V rámci rozhraní přidejte odvozené rozhraní a implementaci tříd nebo struktur.|
    |**Zobrazit typy těchto odkazů**|Přidejte všechny třídy a jejich členy, které tato třída používá.|
    |**Zobrazit typy odkazující na tuto**|Přidejte všechny třídy a jejich členy, které tuto třídu používají.|
    |**Zobrazit obsahující obor názvů**|Přidejte nadřazený obor názvů.|
    |**Zobrazit obsahující obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazit všechny základní typy**|Přidejte rekurzivně hierarchii základní třídy nebo rozhraní.|
    |**Zobrazit všechny odvozené typy**|V případě třídy přidejte všechny odvozené třídy rekurzivně.<br /><br /> V rámci rozhraní přidejte rekurzivně veškerá odvozená rozhraní a implementaci tříd nebo struktur.|

     Pro **metodu**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit metody tato volání**|Přidejte metody, které tato metoda volá.|
    |**Zobrazit pole s odkazy**|Přidejte pole, na která odkazuje tato metoda.|
    |**Zobrazit obsahující typ**|Přidejte nadřazený typ.|
    |**Zobrazit obsahující typ, obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazit přepsané metody**|V případě metody, která přepíše jiné metody nebo implementuje metodu rozhraní, přidejte všechny abstraktní nebo virtuální metody základních tříd, které jsou přepsány, a případně metodu rozhraní, které je implementováno.|

     Pro **pole** nebo **vlastnost**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit obsahující typ**|Přidejte nadřazený typ.|
    |**Zobrazit obsahující typ, obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|

     ![Zobrazit metody volané tímto členem](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")

7. Mapa zobrazuje vztahy. V tomto příkladu metody volané `Find` metodou a jejich umístění v řešení nebo externě.

     ![Zobrazit konkrétní závislosti na mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

8. Chcete-li zjednodušit mapu a soustředit se na jednotlivé části, zvolte možnost **filtry** na panelu nástrojů mapa kódu a vyberte pouze typy uzlů a odkazy, které vás zajímají. Například vypněte zobrazení složek řešení, sestavení a oborů názvů.

     ![Zjednodušení zobrazení pomocí podokna filtru](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")

## <a name="see-dependencies-between-c-and-c-source-files-and-header-files"></a><a name="SeeSourceHeader"></a> Zobrazit závislosti mezi zdrojovými soubory C a C++ a hlavičkové soubory
 Pokud chcete vytvořit úplnější mapování pro projekty v jazyce C++, nastavte u těchto projektů možnost Procházet informace kompilátoru (**/fr**). Viz [/fr,/fr (Create. Soubor SBR)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). Jinak se objeví zpráva s dotazem, zda chcete tuto možnost nastavit. Pokud vyberete **OK**, tato možnost nastaví možnost pouze pro aktuální mapu. Můžete zvolit, že se má skrýt zpráva u všech pozdějších map. Pokud tuto zprávu skryjete, můžete ji znovu zobrazit. Nastavte následující klíč registru na `0` nebo odstraňte klíč:

 **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0\NativeProvider: AutoEnableSbr**

 Když otevřete řešení, které obsahuje projekty Visual C++, může trvat nějakou dobu, než se aktualizuje databáze technologie IntelliSense. Během této doby možná nebudete moci vytvořit mapy kódu pro soubory hlaviček (. h nebo `#include` ), dokud se nedokončí aktualizace databáze IntelliSense. Na stavovém řádku v dolní části sady Visual Studio můžete sledovat průběh aktualizace. Chcete-li vyřešit problémy nebo zprávy, které se zobrazí, protože některá nastavení technologie IntelliSense jsou zakázaná, přečtěte si téma [řešení potíží s mapováním pro kód C](#Troubleshooting)

- Chcete-li zobrazit závislosti mezi všemi zdrojovými soubory a hlavičkové soubory ve vašem řešení, v nabídce **Architektura** vyberte možnost **Generovat graf souborů zahrnutí**.

     ![Graf závislosti pro nativní kód](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")

- Chcete-li zobrazit závislosti mezi aktuálně otevřeným souborem a souvisejícími zdrojovými soubory a hlavičkou souborů, otevřete zdrojový soubor nebo soubor hlaviček. Otevřete místní nabídku souboru kdekoli v souboru. Vyberte možnost **Generovat graf souborů zahrnutí**.

     ![První graf závislosti na úrovni&#45;pro soubor. h](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")

### <a name="troubleshoot-maps-for-c-and-c-code"></a><a name="Troubleshooting"></a> Řešení potíží s mapami pro kód C a C++
 Tyto položky nejsou podporovány pro kód jazyka C a C++:

- Základní typy se nezobrazují na mapách, které zahrnují nadřazenou hierarchii.

- Většina položek nabídky **Zobrazit** není k dispozici pro kód C a C++.

  Tyto problémy se mohou vyskytnout při vytváření map kódu pro kód jazyka C a C++:

|**Problém**|**Možná příčina**|**Řešení**|
|---------------|------------------------|--------------------|
|Nepovedlo se vygenerovat mapu kódu.|V řešení nebyly úspěšně sestaveny žádné projekty.|Opravte chyby sestavení, k nimž došlo, a potom znovu vygenerujte mapu.|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přestane reagovat při pokusu o vygenerování mapy kódu z nabídky **Architektura** .|Soubor databáze programů (.pdb) může být poškozen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|Znovu sestavte řešení a potom akci opakujte.|
|Určitá nastavení pro databázi procházení IntelliSense jsou zakázána.|Některá nastavení IntelliSense můžou být v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dialogovém okně **Možnosti** zakázaná.|Chcete-li tato nastavení povolit, zapněte je.<br /><br /> Viz [Možnosti, textový editor, C/C++, Upřesnit](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Zpráva **neznámé metody** se zobrazí v uzlu metody.<br /><br /> K tomuto problému dochází, protože nelze vyřešit název metody.|Binární soubor nemusí mít základní tabulku přemístění.|V linkeru zapněte možnost **/fixed: No** .<br /><br /> Viz [/fixed (pevná základní adresa)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|
||Soubor databáze programů (.pdb) nemusí být vytvořen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|V linkeru zapněte možnost **/Debug** .<br /><br /> Viz [/Debug (generování informací o ladění)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|
||V očekávaných umístěních nelze otevřít nebo najít soubor .pdb.|Ujistěte se, že v předpokládaném umístění existuje soubor .pdb.|
||Informace o ladění byly ze souboru .pdb odstraněny.|Pokud se v linkeru použila možnost **/PDBSTRIPPED** , zahrňte místo toho úplný soubor. pdb.<br /><br /> Viz [/PDBSTRIPPED (proložení privátních symbolů)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|
||Volající není funkcí a je převodní rutinou v binárním souboru nebo ukazatelem v datové sekci.|Je-li volajícím převodem, zkuste použít příkaz, `_declspec(dllimport)` aby nedošlo k převodu.<br /><br /> Přečtěte si:<br /><br /> -   [Obecná pravidla a omezení](https://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [Import volání funkcí pomocí __declspec (dllimport)](https://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport, dllimport](https://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|

## <a name="make-code-maps-render-more-quickly"></a><a name="RenderMoreQuickly"></a> Rychlejší vykreslování map kódu
 Při prvním generování mapy aplikace Visual Studio indexuje všechny závislosti, které najde. Tento proces může určitou dobu trvat, zejména u velkých řešení, ale zvýší výkon později. Pokud se váš kód změní, Visual Studio znovu indexuje pouze aktualizovaný kód. Chcete-li minimalizovat čas potřebný k dokončení vykreslování mapy, vezměte v úvahu následující skutečnosti:

- [Namapujte pouze závislosti, které vás zajímají.](#SeeSpecificSource)

- Než vygenerujete mapu pro celé řešení, snižte Rozsah řešení.

- Vypněte automatické sestavení pro řešení pomocí tlačítka **Přeskočit sestavení** na panelu nástrojů mapa kódu.

- Vypněte automatické přidávání nadřazených položek pomocí tlačítka **Zahrnout nadřazené** položky na panelu nástrojů mapa kódu.

- Upravte soubor s mapou kódu přímo pro odebrání uzlů a propojení, které nepotřebujete. Změna mapy nemá vliv na podkladový kód. Další informace najdete v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

  ![Přeskočit sestavení a zahrnout nadřízených tlačítek](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")

  I když Visual Studio může běžet s 1 GB paměti, doporučujeme, aby váš počítač měl alespoň 2 GB paměti, aby se zabránilo dlouhým prodlevám, když Visual Studio vytváří index kódu a generuje mapu.

  Vytváření map nebo přidávání položek na mapu z Průzkumník řešení může trvat déle, pokud je vlastnost **Kopírovat do výstupního adresáře** položky projektu nastavena na hodnotu **vždy kopírovat**. To může způsobit problémy s přírůstkovým sestavením a opakovaným sestavením projektu aplikací Visual Studio. Chcete-li zvýšit výkon, změňte tuto vlastnost na **Kopírovat, pokud je novější** nebo `PreserveNewest` . Viz [přírůstková sestavení](../msbuild/incremental-builds.md).

  Dokončená mapa zobrazí závislosti pouze pro úspěšně sestavený kód. Pokud dojde k chybám sestavení u některých součástí, zobrazí se na mapě tyto chyby. Ujistěte se, že součást skutečně sestaví a má závislosti, než na základě mapy provedete rozhodování o architektuře.

## <a name="share-code-maps"></a><a name="SavingExporting"></a> Sdílet mapy kódu

### <a name="share-the-map-with-other-visual-studio-users"></a>Sdílet mapu s ostatními uživateli aplikace Visual Studio
 Uložte mapu pomocí nabídky **soubor** .

 -nebo-

 Chcete-li uložit mapu jako součást konkrétního projektu, na panelu nástrojů mapa zvolte možnost **sdílet**, **přesunout** \<*CodeMapName*> **. dgml do**a pak zvolte projekt, kam chcete mapu Uložit.

 ![Přesunout mapu do jiného projektu](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")

 Visual Studio uloží mapu jako soubor. dgml, který můžete sdílet s ostatními uživateli Visual Studio Enterprise a Visual Studio Professional.

> [!NOTE]
> Předtím, než nasdílíte mapu s uživateli, kteří používají Visual Studio Professional, je třeba rozbalit všechny skupiny, zobrazit skryté uzly a odkazy křížové skupiny a načíst všechny odstraněné uzly, které mají jiní uživatelé vidět na mapě. Jinak ostatní uživatelé nebudou moci tyto položky zobrazit.
>
> Při ukládání mapy, která je v projektu modelování nebo byla zkopírována z projektu modelování do jiného umístění, může dojít k následující chybě:
>
> "Nelze uložit *název souboru* mimo adresář projektu. Propojené položky nejsou podporovány.“
>
> Aplikace Visual Studio zobrazí chybu, ale přesto vytvoří uloženou verzi. Chcete-li se této chybě vyhnout, vytvořte mapu mimo projekt modelování. Potom jej můžete uložit do požadovaného umístění. Nebude fungovat, pokud budete chtít soubor pouze zkopírovat do jiného umístění v řešení a potom jej uložit.

### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Exportujte mapu jako obrázek, abyste ho mohli kopírovat do jiných aplikací, jako je například Microsoft Word nebo PowerPoint.

1. Na panelu nástrojů mapa kódu vyberte možnost **sdílet**, **e-mail jako obrázek** nebo **Kopírovat obrázek**.

2. Vložte obrázek do jiné aplikace.

### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Exportujte mapu jako soubor XPS, abyste ho viděli v prohlížečích XML nebo XAML, jako je Internet Explorer.

1. Na panelu nástrojů mapa kódu vyberte možnost **sdílet**, **e-mail jako přenosný formát XPS** nebo **Uložit jako přenosný formát XPS**.

2. Přejděte do umístění, kam chcete soubor uložit.

3. Pojmenujte mapu kódu. Ujistěte se, že je pole **Uložit jako typ** nastaveno na **soubory XPS ( \* . XPS)**. Klikněte na tlačítko **Uložit**.

## <a name="what-else-can-i-do"></a>Co dalšího mohu udělat?

- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)

- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)

- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)

- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
