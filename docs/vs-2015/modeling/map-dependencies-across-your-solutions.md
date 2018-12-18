---
title: Mapování závislostí napříč vaším řešením | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 20122a1b254eee15efb557b5899e59fc914fda3a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740053"
---
# <a name="map-dependencies-across-your-solutions"></a>Mapování závislostí napříč vaším řešením
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete pochopit závislosti ve vašem kódu, Vizualizujte si je vytvořením map kódu. Díky tomu můžete zjistit, jak zapadá kód společně bez přečtení soubory a řádky kódu.  
  
 ![Zobrazení závislostí napříč vaším řešením](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
 **Tady jsou některé videa**:  
  
-   [Pochopení závislostí kódu pomocí vizualizace](http://go.microsoft.com/fwlink/?LinkID=252065)  
  
-   [Vizualizujte dopad změny](http://go.microsoft.com/fwlink/?LinkID=252068)  
  
-   [Porozumění komplexnímu kódu pomocí map kódu](http://go.microsoft.com/fwlink/?LinkID=259869)  
  
##  <a name="GetStarted"></a> Začínáme s map kódu  
 **Použití map kódu musíte buď**:  
  
-   Visual Studio Enterprise: Vytváření map kódu z editoru kódu, Průzkumník řešení, zobrazení tříd nebo prohlížeči objektů.  
  
-   Visual Studio Professional: Otevření kódových map, provádění omezené úprav a vyhledání kódu.  
  
> [!WARNING]
>  Než budete sdílet mapy vytvořené v sadě Visual Studio Enterprise s jinými uživateli, kteří používají Visual Studio Professional, ujistěte se, že všechny položky na mapě (jako jsou skryté položky, rozšířené skupiny a propojení mezi skupinami) jsou nastavena jako viditelná.  
  
 **Můžete namapovat závislostí pro kód v těchto jazycích**:  
  
- Visual C# .NET nebo Visual Basic .NET v řešení nebo sestavení (.dll nebo .exe)  
  
- Nativní nebo spravovaný kód C nebo C++ v projektech Visual C++, soubory hlaviček (.h nebo `#include`), nebo binární soubory  
  
- Projekty X ++ a sestavení z modulů .NET pro aplikace Microsoft Dynamics AX  
  
  **Poznámka:** pro projekty než C# nebo Visual Basic .NET, jsou méně možností pro spuštění mapy kódu nebo při přidávání položek do existující mapy kódu. Nelze například klikněte pravým tlačítkem na objekt v textovém editoru projekt jazyka C++ a přidejte ho do mapy kódu. Můžete však přetáhněte a umístěte kód jednotlivé prvky nebo soubory z Průzkumníka řešení, zobrazení tříd a prohlížeče objektů.  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>K zobrazení celkové závislostí ve vašem řešení  
  
1.  Otevřít **architektura** nabídky.  
  
2.  Pokud právě otevřeli řešení a nebyly dosud sestaven, nebo pokud váš kód se změnil od posledního jste sestavili, zvolte **Generovat mapu kódu pro řešení**.  
  
3.  Pokud váš kód nebyl změněn od posledního vytvořené, vyberte **Generovat mapu kódu pro řešení bez vytváření** získat vyšší výkon při vytváření mapy.  
  
4.  [Zobrazit celkové závislosti](#SeeOverviewSource) pochopit, jak můžete map kódu k zobrazení celkového závislostí ve vašem řešení.  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>Pokud chcete zobrazit konkrétní závislosti v rámci vašeho řešení  
  
1.  V rámci řešení pro načtení, otevřete **Průzkumníka řešení**.  
  
2.  Vyberte všechny projekty, odkazy na sestavení, složky, soubory, typy nebo členy, které chcete propojit.  
  
3.  Na **Průzkumníka řešení** nástrojů, zvolte **zobrazit na mapě kódu**![vytvořit nový graf z vybrané uzly tlačítko](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). Nebo otevřete místní nabídku a zvolte **zobrazit na mapě kódu**. Můžete také přetáhnout položky ze zobrazení tříd nebo prohlížeči objektů do nové nebo existující mapy kódu.  
  
4.  [Zobrazit konkrétní závislosti](#SeeSpecificSource) pochopit, jak můžete map kódu k zobrazení určitých závislostí v rámci vašeho řešení.  
  
###  <a name="CreateEmptyMap"></a> Chcete-li přidat mapu s novým prázdný kód do vašeho řešení  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel nejvyšší úrovně řešení. Zvolte **přidat** klikněte na tlačítko **nová položka**.  
  
2.  V části **nainstalováno**, zvolte **Obecné**.  
  
3.  V pravém podokně vyberte **dokument orientovaného grafu** a klikněte na tlačítko **přidat**.  
  
     Teď máte prázdné mapy, která se zobrazí ve vašem řešení **položky řešení** složky.  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Chcete-li vytvořit mapu s novým prázdný kód bez jeho přidání do řešení  
  
1.  Otevřít **architektura** nabídku a zvolte **novou mapu kódu**.  
  
     \- nebo –  
  
2.  Otevřít **souboru** nabídku a zvolte **nový** klikněte na tlačítko **souboru**.  
  
3.  V části **nainstalováno**, zvolte **Obecné**.  
  
4.  V pravém podokně vyberte **dokument orientovaného grafu** a klikněte na tlačítko **otevřít**.  
  
     Teď máte prázdné mapy, která se nezobrazují v složky vašeho řešení.  
  
##  <a name="SeeOverviewSource"></a> Zobrazit celkové závislosti  
  
###  <a name="OverviewSource"></a> Zobrazení závislostí ve vašem řešení  
  
1. Na **architektura** nabídce zvolte **Generovat mapu kódu pro řešení**.  
  
    ![Generování příkazu mapy kódu](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
    Můžete získat mapu, která ukazuje sestavení nejvyšší úrovně a souhrnná propojení mezi nimi. Širší agregační odkaz, další závislosti představuje.  
  
2. Použití **legendy** položky kódu (jako jsou třídy, metody a vlastnosti) a typy vztahů (například dědí z tlačítka na panelu nástrojů mapy kódu zobrazit nebo skrýt seznam ikony typu projektu (například testování, webové a projektu Phone), Implementuje a volání).  
  
    ![Horní&#45;grafu závislostí na úrovni sestavení](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
    Tento příklad řešení obsahuje složky řešení (**testy** a **součásti**), projekty testů, webové projekty a sestavení. Ve výchozím nastavení, zobrazí všechny vztahy členství ve skupině jako *skupiny*, které můžete rozbalit nebo sbalit. **Externích typů** skupina obsahuje všechno mimo řešení, včetně závislostí platformy. Externí sestavení obsahuje pouze položky, které jsou používány. Ve výchozím nastavení jsou na mapě přehlednost skryté systému základní typy.  
  
3. Chcete přejít k podrobnostem do objektu map, rozbalte skupiny, které představují projekty a sestavení. Můžete rozbalit vše, co stisknutím kombinace kláves **CTRL + A** vybrat všechny uzly a poté výběrem **skupiny**, **Rozbalit** z místní nabídky.  
  
    ![Že rozšíření všech skupin v mapě kódu](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4. To však nemusí být užitečná pro velká řešení. Ve skutečnosti pro komplexní řešení, omezení paměti může bránit že rozšíření všech skupin. Místo toho pokud chcete zobrazit uvnitř jednotlivých uzlů, rozbalte ho. Přesuňte ukazatel myši nad uzel a potom klikněte na dvojitou šipku (šipku) jakmile se zobrazí.  
  
    ![Rozbalení uzlu na mapě kódu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
    Nebo pomocí klávesnice podle pak vyberete požadovanou položku a pak stisknete klávesu plus (**+**). Prozkoumat hlubší úrovně kódu, totéž proveďte pro obory názvů, typy a členy.  
  
   > [!TIP]
   >  Další informace o práci s kódem mapuje pomocí myši, klávesnice a dotykového ovládání, naleznete v tématu [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).  
  
5. Pro zjednodušení mapy a zaměřte se na jednotlivé části, zvolte **filtry** na panelu nástrojů Mapa kódu a vyberte jenom typy uzlů a propojení se zajímáte. Lze například skrýt kontejnery složku řešení a sestavení.  
  
    ![Zjednodušení mapy pomocí filtrování kontejnery](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
    Na mapě můžete také zjednodušit skryjete nebo odebrání jednotlivých skupin a položek z mapy, bez ovlivnění původního kódu řešení.  
  
6. Pokud chcete zobrazit vztahy mezi položkami, vyberte je v objektu map. Barvy odkazy označují typů vztahu, jak je znázorněno **legendy** podokně.  
  
    ![Zobrazení závislostí napříč vaším řešením](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
    V tomto příkladu fialové odkazy jsou volání tečkovaná odkazy jsou odkazy a světle modrá odkazy jsou přístup k poli. Zelená může se jednat o dědičnosti, nebo může být *agregovat odkazy* označující více než jeden typ vztahu (nebo *kategorie*).  
  
   > [!TIP]
   >  Pokud se zobrazí zelená propojení, nemusí to znamenat, že není právě vztah dědičnosti. Může také být volání metody, ale ty jsou skryta vztah dědičnosti. Pokud chcete zobrazit konkrétní typy odkazů, pomocí zaškrtávacích políček v **filtry** podokně typy nepotřebujete.  
  
7. Pokud chcete získat další informace o položce nebo propojení, přesuňte ukazatel myši dojde k jeho zvýraznění její popisek. Zobrazí podrobnosti o prvek kódu nebo kategorií, které představuje odkaz.  
  
    ![Zobrazení kategorií relace](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8. Chcete-li zkontrolovat položky závislosti reprezentované souhrnným odkazem, nejprve vyberte odkaz a pak otevřete místní nabídku. Zvolte **zobrazit přispívající vazby** (nebo **zobrazit přispívající vazby na nové mapě kódu**). To rozbalí skupiny na obou koncích spojení a zobrazí pouze položky a závislosti, které se účastní v odkazu.  
  
9. Chcete-li se zaměřit na konkrétní části mapy, můžete nadále odebrat položky, které nepotřebujete. Například zobrazit podrobné informace o zobrazení tříd a členů, jednoduše filtrovat všechny uzly oboru názvů v **filtry** podokně.  
  
     ![Procházení na úrovni třídy a člena](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. Dalším způsobem, abyste se mohli zaměřit na mapě komplexní řešení je Generovat mapu s novým obsahující vybrané položky z existujícího mapování. Uložení **CTRL** při výběru položky, měli byste se zaměřit na, otevřete místní nabídku a zvolte **nový graf z výběru**.  
  
     ![Zobrazit vybrané položky na mapu s novým kódem](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. Obsahující kontext se přenesou na novou mapu. Skrýt složky řešení a všechny kontejnery, které nechcete zjistit, **filtry** podokně.  
  
     ![Filtrovat kontejnery pro zjednodušení zobrazení](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. Rozbalit skupiny a vyberte položky v objektu map, chcete-li zobrazit vztahy.  
  
     ![Vyberte položky, které chcete zobrazit vztahy](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
    Viz také:  
  
-   [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
-   Vyhledávání potenciálních problémů v kódu podle [spuštěna analyzátor](../modeling/find-potential-problems-using-code-map-analyzers.md).  
  
###  <a name="OverviewCompiled"></a> Zobrazit závislosti mezi sestavení nebo binární soubory  
  
1.  [Vytvořte mapu kódu prázdný](#GetStarted), nebo otevřete existující mapy kódu (soubor .dgml).  
  
2.  Přetáhněte sestavení nebo binární soubory, které chcete namapovat mimo aplikaci Visual Studio do mapy. Například přetáhněte sestavení nebo binární soubory z Průzkumníka Windows nebo Průzkumníka souborů.  
  
> [!NOTE]
>  Sestavení nebo binární soubory můžete přetáhnout z Průzkumníka Windows nebo Průzkumníka souborů pouze v případě, že spustíte ho a sady Visual Studio na stejné úrovni oprávnění řízení přístupu uživatele (UAC). Například pokud je zapnutý nástroj Řízení uživatelských účtů a používáte Visual Studio jako správce, Průzkumník Windows nebo Průzkumníka souborů zablokuje možnost přetahování. Chcete-li tento problém obejít, ujistěte se, jak běží se stejnou úrovní oprávnění, nebo vypněte nástroj Řízení uživatelských účtů.  
  
##  <a name="SeeSpecificSource"></a> Zobrazit konkrétní závislosti  
 Předpokládejme například, že máte přezkoumání kódu provést některé soubory s probíhající změny. Zobrazení závislostí v tyto změny, můžete vytvořit mapu kódu z těchto souborů.  
  
 ![Zobrazit konkrétní závislosti v mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>Zobrazit specifické závislosti ve vašem řešení  
  
1.  Otevřít **Průzkumníka řešení**. Vyberte projekty, odkazy na sestavení, složky, soubory, typy a členy, které vás zajímají. Chcete-li najít položky se závislostmi na typech nebo členech, otevřete typ nebo člena nabídku z **Průzkumníka řešení**. Vyberte typ závislosti a pak vyberte výsledky.  
  
2.  Mapování položek a jejich členy. Na **Průzkumníka řešení** klikněte na panel nástrojů **zobrazit na mapě kódu**![vytvořit nový graf z vybrané uzly tlačítko](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![Vyberte položky, které chcete namapovat](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3.  Mapa zobrazuje vybrané položky v rámci jeho obsahujícího sestavení.  
  
     ![Vybrané položky zobrazené jako skupiny na mapě](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     Můžete také přetáhnout položky z Průzkumníku řešení, zobrazení tříd nebo prohlížeči objektů na prázdnou hodnotu nebo existující mapy kódu. Chcete-li vytvořit prázdné mapování, naleznete v tématu [vytvořit mapu prázdný kód](#GetStarted). Chcete-li zahrnout nadřízenou hierarchii pro vaše položky, stiskněte a podržte **CTRL** klávesu můžete přetáhnout položky, nebo použít **zahrnout nadřazené položky** tlačítko na panelu nástrojů mapy kódu k určení výchozí akci.  
  
    > [!NOTE]
    >  Když přidáváte položky z projektu, který je sdílen napříč více aplikacemi, jako jsou Windows Phone nebo Windows Store, tyto položky se zobrazí na mapě s aktuálně aktivním projektem aplikace. Pokud změníte kontext na jiný projekt aplikace a přidáte další položky ze sdíleného projektu, tyto položky se nyní zobrazí s nově aktivním projektem aplikace. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.  
  
4.  Chcete-li procházet položky, je rozbalte. Přesuňte ukazatel myši nad položku a pak klikněte na ikonu dvojité šipky (šipka) dolů, když se objeví.  
  
     ![Rozbalení uzlu na mapě kódu](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     Chcete-li rozbalit všechny položky, vyberte je pomocí **CTRL + A**, otevřete místní nabídku pro mapy a zvolte **skupiny**, **Rozbalit**. Ale tato možnost není k dispozici v případě, že rozšíření všech skupin vytvoří mapu nepoužitelná nebo problémy s pamětí.  
  
5.  Rozbalte položky, které vás zajímají, přímo na úrovni třídy a člena v případě potřeby i nadále.  
  
     ![Rozbalit skupiny na úrovni třídy a člena](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     Členové, kteří jsou v kódu, ale nejsou zobrazeny na mapě zobrazíte kliknutím **znovu načíst podřízené** ikonu ![znovu načíst podřízené položky ikonu](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") v horní části levém horním rohu skupiny.  
  
6.  Pokud chcete zobrazit další položky související s nastavením na mapu, vyberte jeden a zvolte **zobrazit související** na panelu nástrojů Mapa kódu, vyberte typ související položky a přidejte do mapy. Můžete také vybrat jednu nebo více položek, otevřete místní nabídku a klikněte na tlačítko **zobrazení...** možnost typu související položky pro přidání do mapy. Příklad:  
  
     Pro **sestavení**, zvolte možnost:  
  
    |||  
    |-|-|  
    |**Zobrazit odkazovaná sestavení**|Přidejte sestavení, na které odkazuje toto sestavení. Externí sestavení se zobrazí v **externích typů** skupiny.|  
    |**Zobrazit sestavení odkazující se na toto**|Přidejte sestavení do řešení, která odkazují na toto sestavení.|  
  
     Pro **obor názvů**, zvolte **zobrazit obsahující sestavení**, pokud není viditelná.  
  
     Pro **třídy** nebo **rozhraní**, zvolte možnost:  
  
    |||  
    |-|-|  
    |**Zobrazit základní typy**|V případě třídy přidejte základní třídu a implementovaná rozhraní.<br /><br /> V rámci rozhraní přidejte základní rozhraní.|  
    |**Zobrazit odvozené typy**|V případě třídy přidejte odvozené třídy.<br /><br /> V rámci rozhraní přidejte odvozené rozhraní a implementaci tříd nebo struktur.|  
    |**Zobrazit odkazované typy**|Přidejte všechny třídy a jejich členy, které tato třída používá.|  
    |**Zobrazit typy odkazující se na toto**|Přidejte všechny třídy a jejich členy, které tuto třídu používají.|  
    |**Zobrazit obsahující Namespace**|Přidáte nadřazený obor názvů.|  
    |**Zobrazit obsahující Namespace a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|  
    |**Zobrazit všechny základní typy**|Přidejte rekurzivně hierarchii základní třídy nebo rozhraní.|  
    |**Zobrazit všechny odvozené typy**|V případě třídy přidejte všechny odvozené třídy rekurzivně.<br /><br /> V rámci rozhraní přidejte rekurzivně veškerá odvozená rozhraní a implementaci tříd nebo struktur.|  
  
     Pro **metoda**, zvolte možnost:  
  
    |||  
    |-|-|  
    |**Zobrazit volané metody**|Přidejte metody, které tato metoda volá.|  
    |**Ukázat odkazovaná pole**|Přidejte pole, na která odkazuje tato metoda.|  
    |**Zobrazit obsahující typ**|Přidáte nadřazeného typu.|  
    |**Zobrazit obsahující typ, Namespace a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|  
    |**Zobrazit přepsané metody**|V případě metody, která přepíše jiné metody nebo implementuje metodu rozhraní, přidejte všechny abstraktní nebo virtuální metody základních tříd, které jsou přepsány, a případně metodu rozhraní, které je implementováno.|  
  
     Pro **pole** nebo **vlastnost**, zvolte možnost:  
  
    |||  
    |-|-|  
    |**Zobrazit obsahující typ**|Přidáte nadřazeného typu.|  
    |**Zobrazit obsahující typ, Namespace a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|  
  
     ![Zobrazit metody volané tento člen](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7.  Mapa znázorňuje vztahy. V tomto příkladu volá metody `Find` metoda a jejich umístění v řešení nebo externě.  
  
     ![Zobrazit konkrétní závislosti v mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8.  Pro zjednodušení mapy a zaměřte se na jednotlivé části, zvolte **filtry** na panelu nástrojů Mapa kódu a vyberte jenom typy uzlů a propojení se zajímáte. Například vypněte zobrazení složek řešení, sestavení a obory názvů.  
  
     ![Pomocí podokna filtru pro zjednodušení zobrazení](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
##  <a name="SeeSourceHeader"></a> Zobrazení závislostí mezi zdrojovými soubory C a C++ a soubory hlaviček  
 Pokud chcete vytvořit podrobnější mapy pro projekty C++, nastavte možnost Procházet informace kompilátoru (**/FR**) na těchto projektech. Zobrazit [/FR, /Fr (vytvořit. Soubor SBR)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). Jinak se objeví zpráva s dotazem, zda chcete tuto možnost nastavit. Pokud vyberete **OK**, tím se nastaví možnost pouze aktuální mapování. Můžete skrýt zprávu pro všechny pozdější mapy. Pokud je skrýt tuto zprávu, můžete si je znovu zobrazí. Nastavte následující klíč registru na `0` nebo klíč odstraňte:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider : AutoEnableSbr**  
  
 Když otevřete řešení, které obsahuje projekty Visual C++, může trvat nějakou dobu, než se aktualizuje databáze technologie IntelliSense. Během této doby nebudete moct vytváření map kódu pro záhlaví (.h nebo `#include`) soubory, dokud se nedokončí aktualizace databáze IntelliSense. Na stavovém řádku v dolní části sady Visual Studio můžete sledovat průběh aktualizace. Chcete-li vyřešit problémy nebo zprávy, které jsou zobrazeny, protože jsou zakázány některá nastavení technologie IntelliSense, přečtěte si téma [Poradce při potížích s mapování pro kód jazyka C a C++](#Troubleshooting).  
  
-   Zobrazení závislostí mezi všechny zdrojové soubory a soubory hlaviček ve vašem řešení na **architektura** nabídce zvolte **Generovat graf vložených souborů**.  
  
     ![Graf závislosti pro nativní kód](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")  
  
-   Pokud chcete zobrazit závislosti mezi aktuálně otevřený soubor a související zdrojové soubory a soubory hlaviček, otevřete zdrojový soubor nebo soubor hlaviček. Otevřete místní nabídku souboru kdekoli v souboru. Zvolte **Generovat graf souborů zahrnutí**.  
  
     ![První&#45;grafu závislostí na úrovni souboru .h](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
###  <a name="Troubleshooting"></a> Řešení potíží s mapování pro kód jazyka C a C++  
 Tyto položky nejsou podporovány pro kód jazyka C a C++:  
  
- Základní typy se nezobrazují na mapách, které obsahují nadřazené hierarchie.  
  
- Většina **zobrazit** položky nabídky není k dispozici pro kód jazyka C a C++.  
  
  Tyto problémy může dojít při vytváření map kódu pro kód jazyka C a C++:  
  
|**Problém**|**Možná příčina**|**Řešení**|  
|---------------|------------------------|--------------------|  
|Generovat mapu kódu se nezdařilo.|V řešení nebyly úspěšně sestaveny žádné projekty.|Opravte chyby sestavení, ke kterým došlo a potom znovu vytvořte mapu.|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přestane reagovat při pokusu o generování mapy kódu z **architektura** nabídky.|Soubor databáze programů (.pdb) může být poškozen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|Znovu sestavte řešení a potom akci opakujte.|  
|Určitá nastavení pro databázi procházení IntelliSense jsou zakázána.|Určitá nastavení IntelliSense můžou být zakázané v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **možnosti** dialogové okno.|Chcete-li tato nastavení povolit, zapněte je.<br /><br /> Zobrazit [možnosti, textový Editor, C/C++, Upřesnit](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|Zpráva **neznámé metody** se zobrazí v uzlu metody.<br /><br /> K tomuto problému dochází, protože nelze vyřešit název metody.|Binární soubor nemusí mít základní tabulku přemístění.|Zapnout **/fixed: No** v linkeru možnost.<br /><br /> Zobrazit [/fixed (pevná základní adresa)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|  
||Soubor databáze programů (.pdb) nemusí být vytvořen.<br /><br /> Soubor .pdb ukládá informace o ladění, jako je typ, metoda a informace zdrojového souboru.|Zapnout **/DEBUG** v linkeru možnost.<br /><br /> Zobrazit [/DEBUG (generování ladicích informací)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|  
||V očekávaných umístěních nelze otevřít nebo najít soubor .pdb.|Ujistěte se, že v předpokládaném umístění existuje soubor .pdb.|  
||Informace o ladění byly ze souboru .pdb odstraněny.|Pokud **/PDBSTRIPPED** byla v nástroji linker použita možnost, místo toho zahrňte kompletní soubor .pdb.<br /><br /> Zobrazit [/PDBSTRIPPED (odstranění privátních symbolů)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
||Volající není funkcí a je převodní rutinou v binárním souboru nebo ukazatelem v datové sekci.|Pokud je volající převodní rutinou, zkuste použít `_declspec(dllimport)` aby se zabránilo jiné bitové šířce.<br /><br /> Další informace:<br /><br /> -   [Obecná pravidla a omezení](http://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [Import volání funkcí pomocí deklarace __declspec(dllimport)](http://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport, dllimport](http://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|  
  
##  <a name="RenderMoreQuickly"></a> Ujistěte se, kód, který rychleji vykreslení mapy  
 Při prvním generování mapu, Visual Studio indexuje všechny závislosti, které nalezne. Tento proces může trvat nějakou dobu, zvláště pro velká řešení, ale zlepší výkon později. Pokud se změní kód, sada Visual Studio znovu indexuje pouze aktualizovaný kód. Chcete-li minimalizovat čas potřebný pro mapování na dokončení vykreslování, zvažte následující:  
  
- [Mapování závislostí, které vás zajímají.](#SeeSpecificSource)  
  
- Před generováním mapy pro kompletní řešení snižte Rozsah řešení.  
  
- Vypnout automatické sestavení pro řešení s **přeskočení buildu** tlačítko na panelu nástrojů mapy kódu.  
  
- Vypnout automatické přidávání nadřazených položek s **zahrnout nadřazené položky** tlačítko na panelu nástrojů mapy kódu.  
  
- Upravte soubor mapy kódu přímo na odebrání uzlů a odkazů, které nepotřebujete. Změna mapování neovlivní základní kód. V tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
  ![Tlačítka pro přeskočení buildu a zahrnout nadřazené položky](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
  I když Visual Studio můžete spustit s 1 GB paměti, doporučujeme, že váš počítač měl alespoň 2 GB paměti pro zabránilo dlouhým prodlevám, když Visual Studio vytváří index kódu a generuje mapy.  
  
  Může trvat déle vytvářet mapy nebo přidávat položky do mapy z Průzkumníku řešení, když položka projektu **kopírovat do výstupního adresáře** je nastavena na **vždy Kopírovat**. To může způsobit problémy s přírůstkovým sestavením a opakovaným sestavením projektu aplikací Visual Studio. Chcete-li zvýšit výkon, změňte tuto vlastnost na **kopírovat, pokud je novější** nebo `PreserveNewest`. Zobrazit [přírůstková sestavení](../msbuild/incremental-builds.md).  
  
  Dokončení mapování se zobrazí závislosti pouze pro kód úspěšně sestaven. Pokud dojde k chybám sestavení některých součástí, tyto chyby se zobrazí na mapě. Ujistěte se, že součást skutečně sestaví a má závislosti, než provedete rozhodnutí o architektuře založené na mapě.  
  
##  <a name="SavingExporting"></a> Sdílet mapy kódu  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>Sdílet mapu s ostatními uživateli aplikace Visual Studio  
 Použití **souboru** nabídky Uložit na mapě.  
  
 -nebo-  
  
 Chcete-li uložit mapy jako součást určitého projektu, na panelu nástrojů mapy, zvolte **sdílenou složku**, **přesunout** \< *CodeMapName*>**.dgml do**a pak zvolte projekt, kam chcete uložit na mapě.  
  
 ![Přesunout do jiného projektu mapu](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 Visual Studio uloží jako soubor .dgml, které můžete sdílet s ostatními uživateli aplikace Visual Studio Enterprise a Visual Studio Professional na mapě.  
  
> [!NOTE]
>  Než budete sdílet mapu s uživateli, kteří používají Visual Studio Professional, ujistěte se, že chcete-li rozbalit všechny skupiny, zobrazit skryté uzly a odkazy křížové skupiny a načíst všechny odstraněné uzly, které mají jiní uživatelé vidět na mapě. Jinak ostatní uživatelé nebudou moci tyto položky zobrazit.  
>   
>  Při ukládání mapu, která je v projektu modelování nebo byl zkopírován z projektu modelování do jiného umístění, může dojít k následující chybě:  
>   
>  "Nelze uložit *fileName* mimo adresář projektu. Propojené položky nejsou podporovány.“  
>   
>  Aplikace Visual Studio zobrazí chybu, ale přesto vytvoří uloženou verzi. Aby se zabránilo chybě, vytvořte mapu mimo projekt modelování. Potom jej můžete uložit do požadovaného umístění. Nebude fungovat, pokud budete chtít soubor pouze zkopírovat do jiného umístění v řešení a potom jej uložit.  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Exportovat mapu jako bitovou kopii, aby jej bylo možné zkopírovat do jiných aplikací, jako je například Microsoft Word nebo PowerPoint  
  
1.  Na panelu nástrojů Mapa kódu, zvolte **sdílenou složku**, **e-mailu jako obrázek** nebo **Kopírovat obrázek**.  
  
2.  Vložte obrázek do jiné aplikace.  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Exportovat mapu jako souboru XPS, abyste viděli v XML nebo XAML prohlížeče jako třeba Internet Explorer  
  
1.  Na panelu nástrojů Mapa kódu, zvolte **sdílenou složku**, **e-mailu jako přenosný formát XPS** nebo **uložit jako přenosný formát XPS**.  
  
2.  Přejděte na požadované místo pro uložení souboru.  
  
3.  Název mapy kódu. Ujistěte se, že **uložit jako typ** pole nastavena na **soubory XPS (\*XPS)**. Zvolte **Uložit**.  
  
## <a name="what-else-can-i-do"></a>Co dalšího mohu udělat?  
  
-   [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
-   [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
-   [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)



