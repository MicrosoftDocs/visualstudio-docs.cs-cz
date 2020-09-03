---
title: Spuštění testů jednotek pro aplikace pro Store
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b70e3a24cd4cb05dc1a28ff855498496f5665ddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542854"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Spuštění testů jednotek pro aplikace pro Store v aplikaci Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak spustit testy jednotek pomocí Průzkumníka testů v Microsoft Visual Studio

> [!NOTE]
> Témata v této části popisují funkčnost Visual Studio Express pro systém Windows 8. Visual Studio Community, Enterprise a Professional poskytují další funkce pro testování částí.
>
> - Použijte libovolné rozhraní pro testování částí třetích stran nebo open source jednotky, které vytvořilo adaptér doplňku pro Microsoft Test Explorer. Můžete také analyzovat a zobrazit informace o pokrytí kódu pro vaše testy.
>   - Spusťte testy po každém sestavení. Můžete také použít Microsoft napodobeniny, izolační rozhraní pro spravovaný kód pro zaměření testů na vlastní kód nahrazením testovacího kódu pro systém a funkce třetích stran.
>
>   Další informace najdete v tématu [testování částí kódu](../test/unit-test-your-code.md) v knihovně MSDN.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
 [Architektury testování částí a projekty testů](#BKMK_Unit_test_frameworks_and_test_projects)

 [Spouštění testů v Průzkumníku testů](#BKMK_Running_tests_in_Test_Explorer)

- [Spouštění testů](#BKMK_Running_tests)

  [Zobrazení výsledků testu](#BKMK_Viewing_test_results)

- [Zobrazení podrobností testu](#BKMK_Viewing_test_details)

- [Zobrazení zdrojového kódu testovací metody](#BKMK_Viewing_the_source_code_of_a_test_method)

  [Uspořádání seznamu testů](#BKMK_Organizing_the_test_list)

- [Seskupení testů](#BKMK_Grouping_tests)

- [Hledání a filtrování seznamu testů](#BKMK_Searching_and_filtering_the_test_list)

  [Ladění testů jednotek](#BKMK_Debugging_unit_tests)

## <a name="unit-test-frameworks-and-test-projects"></a><a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Architektury testování částí a projekty testů
 Visual Studio Express pro aplikace pro Windows Store obsahuje rozhraní pro testování částí společnosti Microsoft pro spravované a pro nativní kód jazyka C++. Průzkumník testů může spustit testy z více projektů testů v řešení a z testovacích tříd, které jsou součástí projektů produkčního kódu. Testovací projekty mohou být libovolnou kombinací Visual C++ nebo rozhraní Visual C# a Visual Basicch testů jednotek. Při zápisu testovaného kódu pro .NET Framework může být testovací projekt napsán v jakémkoli .NET Framework jazyce bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ musí být testovány pomocí rozhraní pro testování částí v jazyce C++.

## <a name="running-tests-in-test-explorer"></a><a name="BKMK_Running_tests_in_Test_Explorer"></a> Spouštění testů v Průzkumníku testů
 Při sestavování testovacího projektu se testy zobrazí v Průzkumníku testů. Pokud není Průzkumník testů viditelný, zvolte možnost **test** v nabídce aplikace Visual Studio, zvolte možnost **Windows**a pak zvolte možnost **Průzkumník testů**.

 ![Průzkumník testů jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Při spuštění, zápisu a opětovném spuštění testů se v Průzkumníku testů zobrazí výsledky ve výchozích skupinách **neúspěšných testů**, **Úspěšné testy**, **přeskočené testy** a **nespouštějí se testy**. Můžete změnit způsob, jakým Průzkumník testů seskupí testy.

 Na panelu nástrojů Průzkumníka testů můžete provádět spoustu práce při hledání, uspořádání a spouštění testů.

 ![Spustit testy z panelu nástrojů Průzkumníka testů](../test/media/ute-toolbar.png "UTE_ToolBar")

### <a name="running-tests"></a><a name="BKMK_Running_tests"></a> Spouštění testů
 Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte jednu z následujících akcí:

- Chcete-li spustit všechny testy v řešení, vyberte možnost **Spustit vše**.

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte možnost **Spustit...** a poté vyberte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete místní nabídku pro vybraný test a pak zvolte možnost **Spustit vybrané testy**.

  V horní části okna Průzkumníka testů je animovaný řádek Pass/selhat, protože testy jsou spouštěny. Při uzavírání testovacího běhu se pruh úspěch/selhání změní na zelený, pokud všechny testy proběhly úspěšně, nebo pokud dojde k selhání testu na červenou.

## <a name="viewing-test-results"></a><a name="BKMK_Viewing_test_results"></a> Zobrazení výsledků testu
 Když spouštíte, píšete a znovu spustíte testy, Průzkumník testů zobrazí výsledky ve skupinách **neúspěšných testů**, **úspěšných testů**, **přeskočených testů** a **nespustí testy**. Podokno podrobností v dolní části Průzkumníka testů zobrazuje souhrn testovacího běhu.

### <a name="viewing-test-details"></a><a name="BKMK_Viewing_test_details"></a> Zobrazení podrobností testu
 Chcete-li zobrazit podrobnosti o jednotlivých testech, vyberte test.

 V podokně podrobností testu se zobrazí následující informace:

- Název zdrojového souboru a číslo řádku testovací metody.

- Stav testu.

- Uplynulý čas, po který trvalo spuštění testovací metody.

  Pokud se test nezdařil, podokno podrobností také obsahuje:

- Zpráva vrácená jednotkou testu jednotek pro test.

- Trasování zásobníku v době, kdy se test nezdařil.

### <a name="viewing-the-source-code-of-a-test-method"></a><a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Zobrazení zdrojového kódu testovací metody
 Chcete-li zobrazit zdrojový kód testovací metody v editoru sady Visual Studio, vyberte test a pak zvolte možnost **Otevřít test** v místní nabídce (klávesnice: F12).

## <a name="organizing-the-test-list"></a><a name="BKMK_Organizing_the_test_list"></a> Uspořádání seznamu testů

### <a name="grouping-tests"></a><a name="BKMK_Grouping_tests"></a> Seskupení testů
 Ve výchozím nastavení zobrazí Průzkumník testů testy jako podřízené uzly **neúspěšných testů**, **Úspěšné testy**, **přeskočené testy** a **nespustí testy**.

|Image|Popis|
|-|-|
|![Tlačítko skupiny Průzkumníka testů](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Chcete-li seskupit testy podle času, kdy je provedena, otevřete seznam **Seskupit podle** a vyberte možnost **Doba trvání**. Zvolením možnosti **Výstup testu** přepnete na původní seskupení.|

### <a name="searching-and-filtering-the-test-list"></a><a name="BKMK_Searching_and_filtering_the_test_list"></a> Hledání a filtrování seznamu testů
 Pokud máte velký počet testů, můžete zadat do vyhledávacího pole Průzkumníka testů, abyste seznam vyfiltroval podle zadaného řetězce. Filtr můžete omezit na konkrétní typy řetězců tak, že před zadáním hledaného řetězce vyberete ze seznamu filtru.

 ![Kategorie vyhledávacích filtrů](../test/media/ute-searchfilter.png "UTE_SearchFilter")

## <a name="debugging-unit-tests"></a><a name="BKMK_Debugging_unit_tests"></a> Ladění testů jednotek
 Pomocí Průzkumníka testů můžete spustit ladicí relaci pro testy. Krokování kódu pomocí ladicího programu sady Visual Studio plynule přebírá mezi testy jednotek a testovaným projektem zpět. Spuštění ladění:

1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metodách, které chcete ladit.

   > [!NOTE]
   > Vzhledem k tomu, že testovací metody lze spustit v libovolném pořadí, nastavte zarážky ve všech testovacích metodách, které chcete ladit.

2. V Průzkumníku testů vyberte testovací metody a pak zvolte možnost **ladit vybrané testy** v místní nabídce.

   Další informace o ladicím programu naleznete v tématu [ladění v aplikaci Visual Studio](../debugger/debugging-in-visual-studio.md).
