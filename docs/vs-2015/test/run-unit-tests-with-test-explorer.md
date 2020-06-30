---
title: Spuštění testů jednotek pomocí Průzkumníka testů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6c6ebe39cf0d32480aee1019aa5ea47496bd793
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548132"
---
# <a name="run-unit-tests-with-test-explorer"></a>Spouštění testů částí pomocí Průzkumníka testů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí Průzkumníka testů můžete spouštět testy jednotek ze sady Visual Studio nebo projektů testování částí třetích stran, seskupit testy do kategorií, filtrovat seznam testů a vytvářet, ukládat a spouštět seznamy testů. Můžete také ladit testy a analyzovat výkon testu a pokrytí kódu.

## <a name="contents"></a><a name="BKMK_Contents"></a>Obsah
 [Architektury testování částí a projekty testů](#BKMK_Unit_test_frameworks_and_test_projects)

 [Spustit testy v Průzkumníku testů](#BKMK_Run_tests_in_Test_Explorer)

 [Zobrazit výsledky testu](#BKMK_View_test_results)

 [Seskupení a filtrování seznamu testů](#BKMK_Group_and_filter_the_test_list)

 [Vytváření vlastních seznamů testů](#BKMK_Create_custom_playlists)

 [Ladit a analyzovat testy jednotek](#BKMK_Debug_and_analyze_unit_tests)

 [Externí zdroje](#BKMK_External_resources)

## <a name="unit-test-frameworks-and-test-projects"></a><a name="BKMK_Unit_test_frameworks_and_test_projects"></a>Architektury testování částí a projekty testů
 Visual Studio obsahuje rozhraní pro testování částí společnosti Microsoft pro spravovaný i nativní kód. Nicméně Průzkumník testů může také spustit libovolné rozhraní testování částí, které implementovalo adaptér Průzkumníka testů. Další informace o instalaci rozhraní pro testování částí třetích stran najdete v tématu [instalace rozhraní pro testování částí třetích stran](../test/install-third-party-unit-test-frameworks.md) .

 Průzkumník testů může spustit testy z více projektů testů v řešení a z testovacích tříd, které jsou součástí projektů produkčního kódu. Testovací projekty mohou používat různé architektury testování částí. Při zápisu testovaného kódu pro .NET Framework lze testovací projekt zapsat v jakémkoli jazyce, který také cílí na .NET Framework, bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ musí být testovány pomocí rozhraní pro testování částí v jazyce C++.

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

## <a name="run-tests-in-test-explorer"></a><a name="BKMK_Run_tests_in_Test_Explorer"></a>Spustit testy v Průzkumníku testů
 [Spustit testy](#BKMK_Run_tests) **&#124;** [Spustit testy po každém sestavení](#BKMK_Run_tests_after_every_build)

 Při sestavování testovacího projektu se testy zobrazí v Průzkumníku testů. Pokud není Průzkumník testů viditelný, zvolte možnost **test** v nabídce aplikace Visual Studio, zvolte možnost **Windows**a pak zvolte možnost **Průzkumník testů**.

 ![Průzkumník testů jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Při spuštění, zápisu a opětovném spuštění testů se v Průzkumníku testů zobrazí výsledky ve výchozích skupinách **neúspěšných testů**, **Úspěšné testy**, **přeskočené testy** a **nespouštějí se testy**. Můžete změnit způsob, jakým Průzkumník testů seskupí testy.

 Na panelu nástrojů Průzkumníka testů můžete provádět spoustu práce při hledání, organizování a spouštění testů.

 ![Spustit testy z panelu nástrojů Průzkumníka testů](../test/media/ute-toolbar.png "UTE_ToolBar")

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

### <a name="run-tests"></a><a name="BKMK_Run_tests"></a>Spustit testy
 Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte jednu z následujících akcí:

- Chcete-li spustit všechny testy v řešení, vyberte možnost **Spustit vše**.

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte možnost **Spustit...** a poté vyberte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete kontextovou nabídku pro vybraný test a pak zvolte možnost **Spustit vybrané testy**.

- Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů pomocí tlačítka ![ustit&#95;parallelicon&#45;malého](../test/media/ute-parallelicon-small.png "UTE_parallelicon – malý") přepínacího tlačítka na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.

  V horní části okna Průzkumníka testů je animovaný řádek Pass/selhat, protože testy jsou spouštěny. Při uzavírání testovacího běhu se pruh úspěch/selhání změní na zelený, pokud všechny testy proběhly úspěšně, nebo pokud dojde k selhání testu na červenou.

  ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

### <a name="run-tests-after-every-build"></a><a name="BKMK_Run_tests_after_every_build"></a>Spustit testy po každém sestavení

> [!WARNING]
> Spuštění testů jednotek po každém sestavení je podporováno v Visual Studio Enterprise.

|Image|Popis|
|-|-|
|![Spustit po sestavení](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Chcete-li spustit testy jednotek po každém místním sestavení, zvolte možnost **test** v nabídce Standard a pak zvolte možnost **Spustit testy po sestavení** na panelu nástrojů Průzkumníka testů.|

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

## <a name="view-test-results"></a><a name="BKMK_View_test_results"></a>Zobrazit výsledky testu
 [Zobrazení podrobností o testu](#BKMK_View_test_details) **&#124;** [zobrazení zdrojového kódu testovací metody](#BKMK_View_the_source_code_of_a_test_method)

 Když spouštíte, píšete a znovu spustíte testy, Průzkumník testů zobrazí výsledky ve skupinách **neúspěšných testů**, **úspěšných testů**, **přeskočených testů** a **nespustí testy**. Podokno podrobností v dolní části Průzkumníka testů zobrazuje souhrn testovacího běhu.

### <a name="view-test-details"></a><a name="BKMK_View_test_details"></a>Zobrazit podrobnosti testu
 Chcete-li zobrazit podrobnosti o jednotlivých testech, vyberte test.

 ![Podrobnosti spuštění testu](../test/media/ute-testdetails.png "UTE_TestDetails")

 V podokně podrobností testu se zobrazí následující informace:

- Název zdrojového souboru a číslo řádku testovací metody.

- Stav testu.

- Uplynulý čas, po který trvalo spuštění testovací metody.

  Pokud se test nezdařil, podokno podrobností také obsahuje:

- Zpráva vrácená jednotkou testu jednotek pro test.

- Trasování zásobníku v době, kdy se test nezdařil.

  ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

### <a name="view-the-source-code-of-a-test-method"></a><a name="BKMK_View_the_source_code_of_a_test_method"></a>Zobrazit zdrojový kód testovací metody
 Chcete-li zobrazit zdrojový kód testovací metody v editoru sady Visual Studio, vyberte test a pak zvolte možnost **Otevřít test** v místní nabídce (klávesnice: F12).

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

## <a name="group-and-filter-the-test-list"></a><a name="BKMK_Group_and_filter_the_test_list"></a>Seskupení a filtrování seznamu testů
 [Seskupení seznamu testů](#BKMK_Grouping_the_test_list) **&#124;** [skupin podle vlastností](#BKMK_Group_by_traits) **&#124;** [hledání a filtrování seznamu testů](#BKMK_Search_and_filter_the_test_list)

 Průzkumník testů umožňuje seskupit testy do předdefinovaných kategorií. Většina rozhraní testů jednotek, která běží v Průzkumníku testů, vám umožní definovat vlastní kategorie a páry kategorií a hodnot pro seskupení testů. Můžete také filtrovat seznam testů porovnáním řetězců s vlastnostmi testu.

### <a name="grouping-the-test-list"></a><a name="BKMK_Grouping_the_test_list"></a>Seskupení seznamu testů
 Chcete-li změnit způsob, jakým jsou testy uspořádány, zvolte šipku dolů vedle **tlačítka skupina pro tlačítko** ![test Průzkumníka](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn") a vyberte Nová kritéria seskupení.

 ![Seskupit testy podle kategorie v Průzkumníku testů](../test/media/ute-groupbycategory.png "UTE_GroupByCategory")

### <a name="test-explorer-groups"></a>Skupiny Průzkumníka testů

|Skupina|Popis|
|-----------|-----------------|
|**Doba trvání**|Seskupuje test podle doby spuštění: **rychlá**, **střední**a **pomalá**.|
|**Výsledek**|Seskupí testy podle výsledků spuštění: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**.|
|**Traits**|Seskupí testy podle párů kategorií/hodnot, které definujete. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|
|**Projekt**|Seskupí testy podle názvu projektů.|

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

### <a name="group-by-traits"></a><a name="BKMK_Group_by_traits"></a>Seskupit podle vlastností
 Vlastnost je obvykle dvojice název/hodnota kategorie, ale může to být také jedna kategorie. Vlastnostem lze přiřadit metody, které jsou identifikovány jako testovací metoda v rámci jednotkového testu. Rozhraní testování částí může definovat kategorie vlastností. Přidáním hodnot do kategorií vlastností můžete definovat vlastní páry název-hodnota kategorie. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.

 **Vlastnosti v rozhraní testování částí společnosti Microsoft pro spravovaný kód**

 V rozhraní Microsoft pro testování částí pro spravované aplikace definujete v atributu dvojici název/hodnota vlastnosti <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . Testovací rozhraní obsahuje také tyto předdefinované vlastnosti:

|Znak|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategorie vlastník je definována v rámci testovacího rozhraní jednotky a vyžaduje zadání řetězcové hodnoty vlastníka.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategorie priority je definována v rámci testovacího rozhraní jednotky a vyžaduje, abyste zadali celočíselnou hodnotu priority.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atribut TestCategory umožňuje zadat kategorii bez hodnoty. Kategorie definovaná atributem TestCategory může být také kategorií atributu TestProperty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atribut TestProperty umožňuje definovat vlastnost páru kategorie/hodnota.|

 **Vlastnosti v rozhraní Microsoft Unit Testing Framework pro C++**

 Pro definování vlastností použijte `TEST_METHOD_ATTRIBUTE` makro. Například pro definování vlastnosti s názvem `TEST_MY_TRAIT` :

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Použití definovaného vlastností při testování částí:

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

### <a name="c-trait-attribute-macros"></a>Makra atributů vlastností C++

|Podokně|Popis|
|-----------|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Pro definování vlastností použijte makro TEST_METHOD_ATTRIBUTE.|
|`TEST_OWNER(ownerAlias)`|Použijte předdefinovaný vlastnický vlastník a určete vlastníka testovací metody.|
|`TEST_PRIORITY(priority)`|Pomocí předdefinované vlastnosti priority můžete přiřadit relativní priority k testovacím metodám.|

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

### <a name="search-and-filter-the-test-list"></a><a name="BKMK_Search_and_filter_the_test_list"></a>Hledání a filtrování seznamu testů
 Filtry Průzkumníka testů můžete použít k omezení testovacích metod v projektech, které můžete zobrazit a spustit.

 Když zadáte řetězec do vyhledávacího pole Průzkumníka testů a kliknete na tlačítko ENTER, seznam testů je filtrován tak, aby zobrazoval pouze testy, jejichž plně kvalifikované názvy obsahují řetězec.

 Filtrování podle různých kritérií:

1. Otevřete rozevírací seznam napravo od vyhledávacího pole.

2. Vyberte Nová kritéria.

3. Zadejte hodnotu filtru mezi uvozovky.

   ![Filtrovat testy v Průzkumníku testů](../test/media/ute-filtertestlist.png "UTE_FilterTestList")

> [!NOTE]
> V hledání jsou rozlišována malá a velká písmena a odpovídají zadanému řetězci všem částem hodnoty kritérií.

|Kvalifikátor|Popis|
|---------------|-----------------|
|**Znak**|Vyhledá shody v kategorii a hodnotě vlastností. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|
|**Projekt**|Vyhledá shody v názvech projektů testů.|
|**Chybová zpráva**|Vyhledá shodu v uživatelsky definovaných chybových zprávách vrácených neúspěšnými kontrolními výrazy.|
|**Cesta k souboru**|Vyhledá shody v plně kvalifikovaném názvu souboru zdrojových souborů testu.|
|**Plně kvalifikovaný název**|Vyhledá plně kvalifikovaný název souboru testovacích oborů názvů, tříd a metod pro shody.|
|**Výstup**|Vyhledá chybové zprávy definované uživatelem, které jsou zapsány do standardního výstupu (stdout) nebo standardní chyby (stderr). Syntaxe pro určení výstupních zpráv je definována v rámci testovacího rozhraní jednotky.|
|**Výsledek**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**.|

 K vyloučení podmnožiny výsledků filtru použijte následující syntaxi:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

 Třeba

```
FullName:"MyClass" - FullName:"PerfTest"
```

 Vrátí všechny testy, které zahrnují "MyClass" v názvu, s výjimkou těchto testů, které také zahrnují "PerfTest" v názvu.

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

## <a name="create-custom-playlists"></a><a name="BKMK_Create_custom_playlists"></a>Vytváření vlastních seznamů testů
 Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam stop, testy v seznamu se zobrazí v Průzkumníku testů. Test můžete přidat do více než jednoho seznamu skladeb a všechny testy v projektu jsou k dispozici, když vyberete výchozí seznam **testů pro všechny testy** .

 ![Zvolit seznam testů](../test/media/ute-playlist.png "UTE_Playlist")

 **Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v Průzkumníku testů. V místní nabídce vyberte možnost **Přidat do seznamu**testů, **NewPlaylist**. Uložte soubor s názvem a umístěním, které zadáte v dialogovém okně **vytvořit nový seznam** testů.

 **Chcete-li přidat testy do seznamu stop**, vyberte jeden nebo více testů v Průzkumníku testů. V místní nabídce zvolte možnost **Přidat do seznamu skladeb**a pak zvolte seznam testů, do kterého chcete přidat testy.

 **Chcete-li otevřít seznam stop**, zvolte možnost test, seznam testů v nabídce aplikace Visual Studio a buď vyberte ze seznamu naposledy použitých seznamů stop, nebo zvolte možnost otevřít seznam stop a zadejte název a umístění seznamu skladeb.

 Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů pomocí tlačítka ![ustit&#95;parallelicon&#45;malého](../test/media/ute-parallelicon-small.png "UTE_parallelicon – malý") přepínacího tlačítka na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.

 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

## <a name="debug-and-analyze-unit-tests"></a><a name="BKMK_Debug_and_analyze_unit_tests"></a>Ladit a analyzovat testy jednotek
 [Ladit testy jednotek](#BKMK_Debug_unit_tests) **&#124;** [diagnostikovat problémy s výkonem testovacích metod](#BKMK_Diagnose_test_method_performance_issues) **&#124;** [Analyzovat pokrytí kódu jednotkového testu](#BKMK_Analyzeunit_test_code_coverage)

### <a name="debug-unit-tests"></a><a name="BKMK_Debug_unit_tests"></a>Ladit testy jednotek
 Pomocí Průzkumníka testů můžete spustit ladicí relaci pro testy. Krokování kódu pomocí ladicího programu sady Visual Studio plynule přebírá mezi testy jednotek a testovaným projektem zpět. Spuštění ladění:

1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metodách, které chcete ladit.

   > [!NOTE]
   > Vzhledem k tomu, že testovací metody lze spustit v libovolném pořadí, nastavte zarážky ve všech testovacích metodách, které chcete ladit.

2. V Průzkumníku testů vyberte testovací metody a pak zvolte možnost **ladit vybrané testy** v místní nabídce.

   Další informace o ladicím programu naleznete v tématu [ladění v aplikaci Visual Studio](../debugger/debugging-in-visual-studio.md).

   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

### <a name="diagnose-test-method-performance-issues"></a><a name="BKMK_Diagnose_test_method_performance_issues"></a>Diagnostika problémů s výkonem testovacích metod
 Chcete-li diagnostikovat, proč testovací metoda trvá příliš dlouho, vyberte metodu v Průzkumníku testů a pak zvolte možnost profil v místní nabídce. Viz [prohlížeč výkonu](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a><a name="BKMK_Analyzeunit_test_code_coverage"></a>Analýza pokrytí kódu testu jednotek

> [!NOTE]
> Pokrytí kódu testu jednotek je k dispozici pouze v Visual Studio Enterprise.

 Můžete určit množství kódu produktu, který je skutečně testován pomocí testu jednotek pomocí nástroje pokrytí kódu sady Visual Studio. Můžete spustit pokrytí kódu pro vybrané testy nebo pro všechny testy v řešení.

 Spuštění pokrytí kódu pro testovací metody v řešení:

1. Zvolte možnost **testy** v nabídce aplikace Visual Studio a pak zvolte možnost **Analyzovat pokrytí kódu**.

2. V podnabídce vyberte jeden z následujících příkazů:

   - **Vybrané testy** spouští testovací metody, které jste vybrali v Průzkumníku testů.

   - **Všechny testy** spustí všechny testovací metody v řešení.

   V okně výsledky pokrytí kódu se zobrazí procentuální podíl bloků kódu produktu, které byly uplatněny pomocí řádku, funkce, třídy, oboru názvů a modulu.

   Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)

## <a name="external-resources"></a><a name="BKMK_External_resources"></a>Externí prostředky

### <a name="guidance"></a><a name="BKMK_Guidance"></a>Směrné
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Viz také
 [Testování částí kódu](../test/unit-test-your-code.md) [Spusťte test jednotek jako 64 proces](../test/run-a-unit-test-as-a-64-bit-process.md) .
