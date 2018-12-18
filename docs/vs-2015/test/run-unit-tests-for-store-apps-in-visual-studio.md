---
title: Spouštění testů jednotek pro aplikace pro Store
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: 9496a41d3eadd91112579b54250a6022bd6484e5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050918"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Spuštění testů jednotek pro aplikace pro Store v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak spustit testování částí pomocí Průzkumníka testů v sadě Microsoft Visual Studio

> [!NOTE]
>  Témata v této části popisují funkce Visual Studio Express pro Windows 8. Visual Studio Community, Enterprise a Professional poskytují další funkce pro testování částí.
>
> - Použijte libovolné rozhraní testování částí třetích stran nebo open zdroj, který byl vytvořen adaptér doplněk pro aplikaci Microsoft Test Explorer. Můžete také analyzovat a zobrazit informace o pokrytí kódu pro vaše testy.
>   -   Spusťte testy po každém sestavení. Můžete také použít Microsoft Fakes, izolované rozhraní pro spravovaný kód testy zaměřit se na váš vlastní kód nahrazením testovací kód pro systém a funkce třetích stran.
>
>   Další informace najdete v tématu [svůj kód testu jednotek](../test/unit-test-your-code.md) v knihovně MSDN.

##  <a name="BKMK_In_this_topic"></a> V tomto tématu
 [Rozhraní pro testování částí a Testovací projekty](#BKMK_Unit_test_frameworks_and_test_projects)

 [Spouštění testů v Průzkumníku testů](#BKMK_Running_tests_in_Test_Explorer)

- [Spouštění testů](#BKMK_Running_tests)

  [Zobrazení výsledků testu](#BKMK_Viewing_test_results)

- [Zobrazení Podrobnosti o testu](#BKMK_Viewing_test_details)

- [Zobrazení zdrojového kódu testovací metody](#BKMK_Viewing_the_source_code_of_a_test_method)

  [Uspořádání seznamu testů](#BKMK_Organizing_the_test_list)

- [Seskupení testů](#BKMK_Grouping_tests)

- [Vyhledávání a filtrování seznamu testů](#BKMK_Searching_and_filtering_the_test_list)

  [Ladění testů jednotek](#BKMK_Debugging_unit_tests)

##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Rozhraní pro testování částí a Testovací projekty
 Visual Studio Express for Windows Store Apps obsahuje rozhraní testování částí Microsoft pro spravovaný a nativní kód C++. Průzkumník testů může spouštět testy z více zkušebních projektů v řešení a z testů tříd, které jsou součástí výroby kódu projektů. Projekty testů může být libovolná kombinace Visual C++ nebo rozhraní testování částí Visual C# a Visual Basic. Pokud testovaný kód je určené pro rozhraní .NET Framework, testovací projekt lze zapsat v libovolném jazyce rozhraní .NET Framework, bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ musí být testovány pomocí rozhraní testování částí C++.

##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Spouštění testů v Průzkumníku testů
 Když sestavíte testovací projekt, testy se zobrazí v Průzkumníku testů. Pokud se nezobrazí Průzkumník testů, zvolte **testovací** v nabídce sady Visual Studio, zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.

 ![Průzkumník testu jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Jak spustit, zápis a znovu spouštěny, zobrazuje Průzkumník testů výsledky ve výchozích skupinách **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a  **Nespuštěné testy**. Můžete změnit způsob, jakým Průzkumník testů seskupuje vaše testy.

 Můžete provádět většinu práce hledání, uspořádání a spuštění testů z panelu nástrojů Test Explorer.

 ![Spuštění testů z panelu nástrojů Průzkumník testování](../test/media/ute-toolbar.png "UTE_ToolBar")

###  <a name="BKMK_Running_tests"></a> Spouštění testů
 Spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které jste vybrali. Proveďte jednu z těchto akcí:

- Chcete-li spustit všechny testy v řešení, zvolte **spustit všechny**.

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte **spuštění...**  a pak vyberte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete místní nabídku pro vybraný test a pak zvolte **spustit vybrané testy**.

  Panel úspěšný/selhání v horní části okna Průzkumníka testů je animovaný během spuštění testů. V závěru testovacího běhu panel úspěšný/selhání se změní na zelenou Pokud všechny testy předat, nebo zčervená, pokud některé testy selhaly.

##  <a name="BKMK_Viewing_test_results"></a> Zobrazení výsledků testu
 Jak spustit, zápis a znovu spouštěny, zobrazuje Průzkumník testů výsledky ve skupinách **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a **není spuštěn Testy**. V podokně podrobností v dolní části Průzkumníku testů zobrazí shrnutí testu spusťte.

###  <a name="BKMK_Viewing_test_details"></a> Zobrazení Podrobnosti o testu
 Chcete-li zobrazit podrobnosti o konkrétním testu, vyberte test.

 Podokno podrobností testu zobrazí následující informace:

- Název zdrojového souboru a číslo řádku zkušební metody.

- Stav testu.

- Uplynulý čas trvalo spuštění zkušební metody.

  Pokud se test nezdaří, zobrazí se také v podokně podrobností:

- Zprávy vrácené jednotkou testovacího rozhraní pro test.

- Trasování zásobníku v době testu se nezdařilo.

###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Zobrazení zdrojového kódu testovací metody
 Chcete-li zobrazit zdrojový kód pro testovací metodu v editoru sady Visual Studio, vyberte test a zvolte **otevřít Test** v místní nabídce (klávesnice: F12).

##  <a name="BKMK_Organizing_the_test_list"></a> Uspořádání seznamu testů

###  <a name="BKMK_Grouping_tests"></a> Seskupení testů
 Ve výchozím nastavení, zobrazuje Průzkumník testů testy jako podřízené uzly **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a **nespuštěné testy**.

|||
|-|-|
|![Tlačítko Test Explorer skupiny](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Pro seskupení testů časem potřebným ke spuštění je, otevřete **Group** seznam a zvolte **doba trvání**. Zvolte **výsledek testu** přepněte do původní seskupení.|

###  <a name="BKMK_Searching_and_filtering_the_test_list"></a> Vyhledávání a filtrování seznamu testů
 Pokud máte velký počet testů, můžete zadat do vyhledávacího pole Průzkumníka testů můžete filtrovat seznam podle zadaného řetězce. Filtr můžete omezit na konkrétní typy řetězců výběrem ze seznamu filtru před zadejte hledaný řetězec.

 ![Hledat filtr kategorií](../test/media/ute-searchfilter.png "UTE_SearchFilter")

##  <a name="BKMK_Debugging_unit_tests"></a> Ladění testů jednotek
 Průzkumník testů můžete použít ke spuštění relace ladění pro testy. Krokování kódu s ladicím programem Visual Studio bez problémů přejdete vpřed a zpět mezi testováním částí a testovaný projekt. Spuštění ladění:

1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metod, které chcete ladit.

   > [!NOTE]
   >  Vzhledem k tomu, že zkušební metody lze spustit v libovolném pořadí, nastavte zarážky v všechny testovací metody, které chcete ladit.

2. V Průzkumníku testů vyberte testovací metody a pak zvolte **ladit vybrané testy** v místní nabídce.

   Další informace o ladicím programu, najdete v části [ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md).
