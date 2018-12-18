---
title: Spouštění testů jednotek pomocí Průzkumníka testů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 29
ms.author: gewarren
manager: douge
ms.openlocfilehash: f4c5a8a4d090a7603f83f6fb3c3d9deb0c67d5f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846834"
---
# <a name="run-unit-tests-with-test-explorer"></a>Spouštění testů jednotek pomocí Průzkumníka testů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li spustit testy jednotky ze sady Visual Studio nebo projektů testování jednotky třetí strany, seskupte testy do kategorií, filtrovat seznam testů a vytvořit, uložit a spusťte seznamy stop testů pomocí nástroje Test Explorer. Můžete také ladit testy a analyzovat pokrytí testu výkonu a kódu.  
  
##  <a name="BKMK_Contents"></a> Obsah  
 [Rozhraní pro testování částí a Testovací projekty](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Spustit testy v Průzkumníku testů](#BKMK_Run_tests_in_Test_Explorer)  
  
 [Zobrazení výsledků testu](#BKMK_View_test_results)  
  
 [Seskupit a filtrovat seznam testů](#BKMK_Group_and_filter_the_test_list)  
  
 [Vytvořit vlastní seznamy skladeb](#BKMK_Create_custom_playlists)  
  
 [Ladění a analýza testů jednotek](#BKMK_Debug_and_analyze_unit_tests)  
  
 [Externí prostředky](#BKMK_External_resources)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Rozhraní pro testování částí a Testovací projekty  
 Visual Studio obsahuje rozhraní testování částí Microsoft pro spravovaný i nativní kód. Ale Průzkumníku testů můžete také spustit libovolné jednotky rozhraní testování, který zavedl adaptér Test Explorer. Další informace o instalaci rozhraní pro testování jednotky třetí strany, naleznete v tématu [nainstalovat rozhraní pro testování jednotky třetí strany](../test/install-third-party-unit-test-frameworks.md)  
  
 Průzkumník testů může spouštět testy z více zkušebních projektů v řešení a z testů tříd, které jsou součástí výroby kódu projektů. Projekty testů mohou použít jiné jednotky rozhraní testování. Pokud testovaný kód je určené pro rozhraní .NET Framework, testovací projekt lze zapsat v libovolném jazyce, který také cílí na rozhraní .NET Framework, bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ musí být testovány pomocí rozhraní testování částí C++.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Run_tests_in_Test_Explorer"></a> Spustit testy v Průzkumníku testů  
 [Spuštění testů](#BKMK_Run_tests) **&#124;** [spouštět testy po každém sestavení](#BKMK_Run_tests_after_every_build)  
  
 Když sestavíte testovací projekt, testy se zobrazí v Průzkumníku testů. Pokud se nezobrazí Průzkumník testů, zvolte **testovací** v nabídce sady Visual Studio, zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.  
  
 ![Průzkumník testu jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Jak spustit, zápis a znovu spouštěny, zobrazuje Průzkumník testů výsledky ve výchozích skupinách **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a  **Nespuštěné testy**. Můžete změnit způsob, jakým Průzkumník testů seskupuje vaše testy.  
  
 Můžete provádět většinu práce hledání, uspořádání a spuštění testů z panelu nástrojů Test Explorer.  
  
 ![Spuštění testů z panelu nástrojů Průzkumník testování](../test/media/ute-toolbar.png "UTE_ToolBar")  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests"></a> Spuštění testů  
 Spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které jste vybrali. Proveďte jednu z těchto akcí:  
  
- Chcete-li spustit všechny testy v řešení, zvolte **spustit všechny**.  
  
- Chcete-li spustit všechny testy ve výchozí skupině, zvolte **spuštění...**  a pak vyberte skupinu v nabídce.  
  
- Vyberte jednotlivé testy, které chcete spustit, otevřete kontextovou nabídku pro vybraný test a pak zvolte **spustit vybrané testy**.  
  
- Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute-parallelicon-small.png "UTE_parallelicon malé") přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.  
  
  Panel úspěšný/selhání v horní části okna Průzkumníka testů je animovaný během spuštění testů. V závěru testovacího běhu panel úspěšný/selhání se změní na zelenou Pokud všechny testy předat, nebo zčervená, pokud některé testy selhaly.  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests_after_every_build"></a> Spustit testy po každém sestavení  
  
> [!WARNING]
>  Spuštění testů jednotky po každém sestavení je podporováno v sadě Visual Studio Enterprise.  
  
|||  
|-|-|  
|![Spustit po sestavení](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Chcete-li spouštět testy jednotek po každém místním sestavení, zvolte **testovací** ve standardní nabídce a klikněte na tlačítko **spustit testy po sestavení** na panelu nástrojů Průzkumník testů.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_View_test_results"></a> Zobrazení výsledků testu  
 [Zobrazit podrobnosti o testu](#BKMK_View_test_details) **&#124;** [zobrazit zdrojový kód testovací metody](#BKMK_View_the_source_code_of_a_test_method)  
  
 Jak spustit, zápis a znovu spouštěny, zobrazuje Průzkumník testů výsledky ve skupinách **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a **není spuštěn Testy**. V podokně podrobností v dolní části Průzkumníku testů zobrazí shrnutí testu spusťte.  
  
###  <a name="BKMK_View_test_details"></a> Zobrazit podrobnosti o testu  
 Chcete-li zobrazit podrobnosti o konkrétním testu, vyberte test.  
  
 ![Podrobnosti o spuštění testu](../test/media/ute-testdetails.png "UTE_TestDetails")  
  
 Podokno podrobností testu zobrazí následující informace:  
  
- Název zdrojového souboru a číslo řádku zkušební metody.  
  
- Stav testu.  
  
- Uplynulý čas trvalo spuštění zkušební metody.  
  
  Pokud se test nezdaří, zobrazí se také v podokně podrobností:  
  
- Zprávy vrácené jednotkou testovacího rozhraní pro test.  
  
- Trasování zásobníku v době testu se nezdařilo.  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_View_the_source_code_of_a_test_method"></a> Zobrazit zdrojový kód testovací metody  
 Chcete-li zobrazit zdrojový kód pro testovací metodu v editoru sady Visual Studio, vyberte test a zvolte **otevřít Test** v kontextové nabídce (klávesnice: F12).  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Group_and_filter_the_test_list"></a> Seskupit a filtrovat seznam testů  
 [Seskupení seznamu testů](#BKMK_Grouping_the_test_list) **&#124;** [Seskupit podle vlastností](#BKMK_Group_by_traits) **&#124;** [vyhledávání a filtrování seznamu testů](#BKMK_Search_and_filter_the_test_list)  
  
 Test Explorer umožňuje seskupit testy do předdefinovaných kategorií. Většina prostředí testování jednotek, které běží v Průzkumníku testů, umožňuje definovat vlastní kategorie a dvojice kategorie/hodnota pro seskupení testů. Seznam testů můžete také filtrovat porovnáním řetězců s vlastnostmi testů.  
  
###  <a name="BKMK_Grouping_the_test_list"></a> Seskupení seznamu testů  
 Chcete-li změnit způsob uspořádání testů, zvolte šipku dolů vedle **Group** tlačítko ![tlačítko skupiny Průzkumníka testů](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn") a vyberte Nová seskupení kritéria.  
  
 ![Seskupte testy podle kategorie v Průzkumníku testů](../test/media/ute-groupbycategory.png "UTE_GroupByCategory")  
  
### <a name="test-explorer-groups"></a>Skupiny Průzkumníka testů  
  
|Skupina|Popis|  
|-----------|-----------------|  
|**Doba trvání**|Seskupí testy podle času spuštění: **rychlé**, **střední**, a **pomalá**.|  
|**Výsledek**|Seskupí testy podle výsledků spuštění: **neúspěšné testy**, **přeskočené testy**, **úspěšné testy**.|  
|**Osobnostní rysy**|Seskupí testy podle kategorie nebo párových hodnot, které definujete. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|  
|**Projekt**|Seskupí testy podle názvů projektů.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Group_by_traits"></a> Seskupit podle vlastností  
 Vlastnost je obvykle dvojice název/hodnota kategorie, ale může být také jednu kategorii. Vlastnosti mohou být přiřazeny metodám, které jsou označeny jako testovací metody testovacím rozhraním jednotky. Rámce jednotkových testů můžete definovat kategorií vlastností. Chcete-li definovat vlastní dvojice název/hodnota kategorie do kategorií vlastností můžete přidat hodnoty. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.  
  
 **Vlastnosti v testování části Microsoft Framework pro spravovaný kód**  
  
 V rámci Microsoft testovacího rozhraní jednotky pro spravované aplikace, můžete definovat vlastnost název / hodnota v <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atribut. Testovací rozhraní obsahuje také tyto předdefinované vlastnosti:  
  
|Vlastnost|Popis|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategorie vlastník je definována testovacím rozhraním jednotky a vyžaduje poskytnutí řetězce hodnoty vlastníka.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategorie Priorita je definována testovacím rozhraním jednotky a vyžaduje poskytnutí celočíselné hodnoty priority.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atribut TestCategory umožňuje zadat kategorii bez hodnoty. Kategorie definované atributu TestCategory může být také kategorie atribut TestProperty.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atribut TestProperty umožňuje definovat pár vlastností kategorie/hodnota.|  
  
 **Vlastnosti v testování části Microsoft Framework pro C++**  
  
 Chcete-li definovat vlastnost, použijte `TEST_METHOD_ATTRIBUTE` – makro. Například pro definici znaku s názvem `TEST_MY_TRAIT`:  
  
```cpp  
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)  
```  
  
 Použití definované vlastnosti v testech jednotek:  
  
```  
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
    TEST_OWNER(L"OwnerName")  
    TEST_PRIORITY(1)  
    TEST_MY_TRAIT(L"thisTraitValue")  
END_TEST_METHOD_ATTRIBUTE()  
  
TEST_METHOD(Method1)  
{     
    Logger::WriteMessage("In Method1");  
    Assert::AreEqual(0, 0);  
}  
```  
  
### <a name="c-trait-attribute-macros"></a>Atributy a makra C++ vlastností  
  
|– Makro|Popis|  
|-----------|-----------------|  
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Chcete-li definovat vlastnost, použijte makro TEST_METHOD_ATTRIBUTE.|  
|`TEST_OWNER(ownerAlias)`|Použijte předdefinovanou vlastnost Owner k zadání vlastníka testovací metody.|  
|`TEST_PRIORITY(priority)`|Pomocí předdefinované vlastnosti Priority přiřaďte relativní priority testovacím metodám.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Search_and_filter_the_test_list"></a> Hledat a filtrovat seznam testů  
 Filtry Průzkumníka testování filtrů můžete použít k omezení zkušebních metod v projektech, které můžete zobrazit a spustit.  
  
 Zadejte řetězec do vyhledávacího pole Průzkumníka testů a zvolte ENTER, seznam testů je filtrován a zobrazuje pouze testy, jejichž plně kvalifikované názvy obsahují řetězec.  
  
 Filtrovat podle různých kritérií:  
  
1. Otevřete rozevírací seznam napravo od vyhledávacího pole.  
  
2. Zvolte Nová kritéria.  
  
3. Mezi uvozovkami zadejte hodnotu filtru.  
  
   ![Filtruje testy v Průzkumníku testů](../test/media/ute-filtertestlist.png "UTE_FilterTestList")  
  
> [!NOTE]
>  Hledání jsou malá a velká písmena a odpovídají libovolné části hodnoty kritérií zadaného řetězce.  
  
|Kvalifikátor|Popis|  
|---------------|-----------------|  
|**Vlastnost**|Hledá odpovídající vlastnosti kategorie a hodnoty pro shody. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|  
|**Projekt**|Vyhledá názvy projektů testů pro shody.|  
|**Chybová zpráva**|Hledání uživatelem definované chybové zprávy vrácené selháním výrazů pro shody.|  
|**Cesta k souboru**|Hledá plně kvalifikovaný název zdrojové soubory testů pro shody.|  
|**Plně kvalifikovaný název**|Hledá plně kvalifikovaný název testovací obory názvů, tříd a metod pro shody.|  
|**Output**|Prohledá uživatelem definované chybové zprávy, které jsou zapsány do standardního výstupního (stdout) nebo standardní chyby (stderr). Syntaxe pro určení výstupních zpráv je definována v rámci testovacího rozhraní jednotky.|  
|**Výsledek**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **neúspěšné testy**, **přeskočené testy**, **úspěšné testy**.|  
  
 K vyloučení části výsledků filtru, použijte následující syntaxi:  
  
```  
FilterName:"Criteria" -FilterName:"SubsetCriteria"  
```  
  
 Například  
  
```  
FullName:"MyClass" - FullName:"PerfTest"  
```  
  
 Vrátí všechny testy, které zahrnují "MyClass" v názvu s výjimkou takových zkoušek, které zahrnují také "PerfTest" v názvu.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Create_custom_playlists"></a> Vytvořit vlastní seznamy skladeb  
 Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam stop, testy v seznamu se zobrazí Průzkumník testů. Test můžete přidat k více než jednoho seznamu stop a všechny testy ve vašem projektu jsou k dispozici, když zvolíte výchozí **všechny testy** seznamu testů.  
  
 ![Zvolte seznam stop](../test/media/ute-playlist.png "UTE_Playlist")  
  
 **Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v aplikaci Průzkumník testů. V místní nabídce zvolte **přidat do seznamu testů**, **NewPlaylist**. Uložte soubor s názvem a umístění, které zadáte **vytvořit nový seznam testů** dialogové okno.  
  
 **Chcete-li přidat testy do seznamu stop**, vyberte jeden nebo více testů v aplikaci Průzkumník testů. V místní nabídce zvolte **přidat do seznamu testů**a pak zvolte seznam testů, které chcete přidat testy.  
  
 **Chcete-li otevřít seznam skladeb**, zvolte Test, seznam skladeb v nabídce sady Visual Studio a zvolte ze seznamu naposledy použitých seznamů stop nebo zvolte možnost Otevřít seznam stop, chcete-li určit název a umístění seznamu stop.  
  
 Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute-parallelicon-small.png "UTE_parallelicon malé") přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Debug_and_analyze_unit_tests"></a> Ladění a analýza testů jednotek  
 [Ladění testů jednotky](#BKMK_Debug_unit_tests) **&#124;** [diagnostikovat problémy s výkonem metod testu](#BKMK_Diagnose_test_method_performance_issues) **&#124;** [analyzovat pokrytí kódem jednotkového testu](#BKMK_Analyzeunit_test_code_coverage)  
  
###  <a name="BKMK_Debug_unit_tests"></a> Ladění testů jednotky  
 Průzkumník testů můžete použít ke spuštění relace ladění pro testy. Krokování kódu s ladicím programem Visual Studio bez problémů přejdete vpřed a zpět mezi testováním částí a testovaný projekt. Spuštění ladění:  
  
1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metod, které chcete ladit.  
  
   > [!NOTE]
   >  Vzhledem k tomu, že zkušební metody lze spustit v libovolném pořadí, nastavte zarážky v všechny testovací metody, které chcete ladit.  
  
2. V Průzkumníku testů vyberte testovací metody a pak zvolte **ladit vybrané testy** v místní nabídce.  
  
   Další informace o ladicím programu, najdete v části [ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Diagnose_test_method_performance_issues"></a> Diagnostika problémů s výkonem test – metoda  
 Chcete-li diagnostikovat, proč testovací metoda trvá příliš dlouho, v Průzkumníku testů vyberte metodu a zvolte profil v místní nabídce. Zobrazit [prohlížeč výkonu](../profiling/performance-explorer.md).  
  
###  <a name="BKMK_Analyzeunit_test_code_coverage"></a> Analyzovat pokrytí kódem jednotkového testu  
  
> [!NOTE]
>  Pokrytí kódem jednotkového testu je k dispozici pouze v sadě Visual Studio Enterprise.  
  
 Můžete určit množství kódu produktu, který je skutečně testován prostřednictvím testů jednotky pomocí nástroje pokrytí kódu sady Visual Studio. Můžete spustit pokrytí kódem u vybraných testů nebo u všech testů v řešení.  
  
 Pokud chcete spustit pokrytí kódu pro testovací metody v řešení:  
  
1. Zvolte **testy** v nabídce sady Visual Studio a klikněte na tlačítko **analyzovat pokrytí kódu**.  
  
2. Z podnabídky zvolte jeden z následujících příkazů:  
  
   -   **Vybrané testy** spouští testovací metody, které jste vybrali v aplikaci Test Explorer.  
  
   -   **Všechny testy** spustí všechny testovací metody v řešení.  
  
   Okno výsledky pokrytí kódu zobrazuje procento bloků kódu produktu, které byly vykonány podle řádku, funkce, třídy, oboru názvů a modulu.  
  
   Další informace najdete v tématu [pomocí pokrytí kódu k určení jak mnohem kódu je právě testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_External_resources"></a> Externí prostředky  
  
###  <a name="BKMK_Guidance"></a> Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Viz také  
 [Testování částí kódu](../test/unit-test-your-code.md)   
 [Spuštění testování částí v podobě 64bitového procesu](../test/run-a-unit-test-as-a-64-bit-process.md)



