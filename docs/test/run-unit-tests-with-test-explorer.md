---
title: Spuštění, sestavení a ladění testů jednotek pomocí Průzkumníka testů
description: Zjistěte, jak chcete provozovat testy pomocí Exlorer testu v sadě Visual Studio. Toto téma popisuje, jak povolit automatické testy po sestavení, zobrazit výsledky testů, skupiny a filtrovat seznam testů, vytvořit seznam stop, ladit testy a použít klávesové zkratky testu.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: dc918adb6a66f64cdcda46ea535cd0ab017c0676
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939512"
---
# <a name="run-unit-tests-with-test-explorer"></a>Spouštění testů jednotek pomocí Průzkumníka testů

Použití **Průzkumníka testů** spouštění testů jednotek sady Visual Studio nebo projektů testování jednotky třetí strany. Můžete také použít **Průzkumníka testů** seskupte testy do kategorií, filtrovat seznam testů a vytvořte, uložte a spusťte seznamy stop testů. Můžete ladit testy a analyzovat pokrytí testu výkonu a kódu.

Visual Studio obsahuje rozhraní testování částí Microsoft pro spravovaný i nativní kód. Ale **Průzkumníka testů** můžete taky spustit libovolné jednotky rozhraní testování, který zavedl adaptér Test Explorer. Další informace o instalaci rozhraní pro testování jednotky třetí strany, naleznete v tématu [nainstalovat rozhraní pro testování jednotky třetí strany](../test/install-third-party-unit-test-frameworks.md)

**Průzkumník testů** můžete spouštět testy z více zkušebních projektů v řešení a z testů tříd, které jsou součástí výroby kódu projektů. Projekty testů mohou použít jiné jednotky rozhraní testování. Pokud testovaný kód je určené pro rozhraní .NET Framework, testovací projekt lze zapsat v libovolném jazyce, který také cílí na rozhraní .NET Framework, bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ musí být testovány pomocí rozhraní testování částí C++. Další informace najdete v tématu [zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Spustit testy v Průzkumníku testů

Když sestavíte testovací projekt, testy se zobrazí v Průzkumníku testů. Pokud se nezobrazí Průzkumník testů, zvolte **testovací** v nabídce sady Visual Studio, zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.

![Průzkumník testu jednotek](../test/media/ute_failedpassednotrunsummary.png)

Jak spustit, zápis a znovu spouštěny, zobrazuje Průzkumník testů výsledky ve výchozích skupinách **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a  **Nespuštěné testy**. Můžete změnit způsob, jakým Průzkumník testů seskupuje vaše testy.

Můžete provádět většinu práce hledání, uspořádání a spouštění testů z **Průzkumník testů** nástrojů.

![Spuštění testů z panelu nástrojů Průzkumníka testů](../test/media/ute_toolbar.png)

### <a name="run-tests"></a>Spouštění testů

Spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které jste vybrali. Proveďte jednu z těchto akcí:

- Chcete-li spustit všechny testy v řešení, zvolte **spustit všechny**.

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte **spustit** a pak vyberte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete kontextovou nabídku pro vybraný test a pak zvolte **spustit vybrané testy**.

- Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.

**Panel úspěšný/selhání** v horní části **Průzkumník testů** okna je animovaný ke spuštění testů. V závěru testovacího běhu **panel úspěšný/selhání** se změní na zelenou, pokud všechny testy proběhly úspěšně, nebo zčervená, pokud některé testy selhaly.

### <a name="run-tests-after-every-build"></a>Spustit testy po každém sestavení

|Tlačítko|Popis|
|-|-|
|![Spustit po sestavení](../test/media/ute_runafterbuild_btn.png)|Chcete-li spouštět testy jednotek po každém místním sestavení, zvolte **testovací** ve standardní nabídce a klikněte na tlačítko **spustit testy po sestavení** na **Průzkumníka testů** nástrojů.|

## <a name="view-test-results"></a>Zobrazení výsledků testu

Jak spustit, zápis a znovu spouštěny, zobrazuje Průzkumník testů výsledky ve skupinách **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a **není spuštěn Testy**. V podokně podrobností v dolní části Průzkumníku testů zobrazí shrnutí testu spusťte.

### <a name="view-test-details"></a>Zobrazit podrobnosti o testu

Chcete-li zobrazit podrobnosti o konkrétním testu, vyberte test.

![Podrobnosti spuštění testu](../test/media/ute_testdetails.png)

Podokno podrobností testu zobrazí následující informace:

- Název zdrojového souboru a číslo řádku zkušební metody.

- Stav testu.

- Uplynulý čas trvalo spuštění zkušební metody.

Pokud se test nezdaří, zobrazí se také v podokně podrobností:

- Zprávy vrácené jednotkou testovacího rozhraní pro test.

- Trasování zásobníku v době testu se nezdařilo.

### <a name="view-the-source-code-of-a-test-method"></a>Zobrazit zdrojový kód testovací metody

 Chcete-li zobrazit zdrojový kód pro testovací metodu v editoru sady Visual Studio, vyberte test a zvolte **otevřít Test** v kontextové nabídce (klávesnice: **F12**).

## <a name="group-and-filter-the-test-list"></a>Seskupit a filtrovat seznam testů

Test Explorer umožňuje seskupit testy do předdefinovaných kategorií. Většina prostředí testování jednotek, které běží v Průzkumníku testů, umožňuje definovat vlastní kategorie a dvojice kategorie/hodnota pro seskupení testů. Seznam testů můžete také filtrovat porovnáním řetězců s vlastnostmi testů.

### <a name="group-tests-in-the-test-list"></a>Skupinu testů v seznamu testů

 Chcete-li změnit způsob uspořádání testů, zvolte šipku dolů vedle **Group** tlačítko ![tlačítko skupiny Průzkumníka testů](../test/media/ute_groupby_btn.png) a vyberte nová kritéria seskupení.

 ![Skupinu testů podle kategorií v Průzkumníku testů](../test/media/ute_groupbycategory.png)

### <a name="test-explorer-groups"></a>Skupiny Průzkumníka testů

|Skupina|Popis|
|-|-----------------|
|**Doba trvání**|Seskupí testy podle času spuštění: **rychlé**, **střední**, a **pomalá**.|
|**Výsledek**|Seskupí testy podle výsledků spuštění: **neúspěšné testy**, **přeskočené testy**, **úspěšné testy**.|
|**Osobnostní rysy**|Seskupí testy podle kategorie nebo párových hodnot, které definujete. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|
|**Projekt**|Seskupí testy podle názvů projektů.|

### <a name="group-by-traits"></a>Seskupit podle vlastností

 Vlastnost je obvykle dvojice název/hodnota kategorie, ale může být také jednu kategorii. Vlastnosti mohou být přiřazeny metodám, které jsou označeny jako testovací metody testovacím rozhraním jednotky. Rámce jednotkových testů můžete definovat kategorií vlastností. Chcete-li definovat vlastní dvojice název/hodnota kategorie do kategorií vlastností můžete přidat hodnoty. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.

 **Vlastnosti v testování části Microsoft Framework pro spravovaný kód**

 V rámci Microsoft testovacího rozhraní jednotky pro spravované aplikace, můžete definovat vlastnost název / hodnota v <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atribut. Testovací rozhraní obsahuje také tyto předdefinované vlastnosti:

|Vlastnost|Popis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategorie vlastník je definována testovacím rozhraním jednotky a vyžaduje poskytnutí řetězce hodnoty vlastníka.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategorie Priorita je definována testovacím rozhraním jednotky a vyžaduje poskytnutí celočíselné hodnoty priority.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atribut TestCategory umožňuje zadat kategorii bez hodnoty. Kategorie definované atributu TestCategory může být také kategorie atribut TestProperty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atribut TestProperty umožňuje definovat pár vlastností kategorie/hodnota.|

 **Vlastnosti v Microsoft Unit Testing Framework pro C++** naleznete v tématu [použití Microsoft Unit Testing Framework pro C++](how-to-use-microsoft-test-framework-for-cpp.md).

### <a name="search-and-filter-the-test-list"></a>Hledat a filtrovat seznam testů

Filtry Průzkumníka testování filtrů můžete použít k omezení zkušebních metod v projektech, které můžete zobrazit a spustit.

Pokud zadáte řetězec **Průzkumníka testů** vyhledávací pole a tlačítko **Enter**, seznam testů je filtrován a zobrazuje pouze testy, jejichž plně kvalifikované názvy obsahují řetězec.

Filtrovat podle různých kritérií:

1. Otevřete rozevírací seznam napravo od vyhledávacího pole.

2. Zvolte Nová kritéria.

3. Mezi uvozovkami zadejte hodnotu filtru.

![Filtruje testy v Průzkumníku testů](../test/media/ute_filtertestlist.png)

> [!NOTE]
> Hledání jsou malá a velká písmena a odpovídají libovolné části hodnoty kritérií zadaného řetězce.

|Kvalifikátor|Popis|
|-|-----------------|
|**Vlastnost**|Hledá odpovídající vlastnosti kategorie a hodnoty pro shody. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|
|**Projekt**|Vyhledá názvy projektů testů pro shody.|
|**Chybová zpráva**|Hledání uživatelem definované chybové zprávy vrácené selháním výrazů pro shody.|
|**Cesta k souboru**|Hledá plně kvalifikovaný název zdrojové soubory testů pro shody.|
|**Plně kvalifikovaný název**|Hledá plně kvalifikovaný název testovací obory názvů, tříd a metod pro shody.|
|**Output**|Prohledá uživatelem definované chybové zprávy, které jsou zapsány do standardního výstupního (stdout) nebo standardní chyby (stderr). Syntaxe pro určení výstupních zpráv je definována v rámci testovacího rozhraní jednotky.|
|**Výsledek**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **neúspěšné testy**, **přeskočené testy**, **úspěšné testy**.|

K vyloučení části výsledků filtru, použijte následující syntaxi:

```cpp
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Například `FullName:"MyClass" - FullName:"PerfTest"` vrátí všechny testy, které zahrnují "MyClass" v názvu, s výjimkou případů, testy, které zahrnují také "PerfTest" v názvu.

## <a name="create-custom-playlists"></a>Vytvořit vlastní seznamy skladeb

 Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam stop, testy v seznamu se zobrazí v Průzkumníku testů. Test můžete přidat k více než jednoho seznamu stop a všechny testy ve vašem projektu jsou k dispozici, když zvolíte výchozí **všechny testy** seznamu testů.

 ![Zvolte seznam stop](../test/media/ute_playlist.png)

 **Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v aplikaci Průzkumník testů. V místní nabídce zvolte **přidat do seznamu testů** > **NewPlaylist**. Uložte soubor s názvem a umístění, které zadáte **vytvořit nový seznam testů** dialogové okno.

 **Chcete-li přidat testy do seznamu stop**, vyberte jeden nebo více testů v aplikaci Průzkumník testů. V místní nabídce zvolte **přidat do seznamu testů**a pak zvolte seznam testů, které chcete přidat testy.

 **Chcete-li otevřít seznam skladeb**, zvolte **testovací** > **stop** v nabídce sady Visual Studio a buď zvolte ze seznamu naposledy použitých seznamů stop nebo zvolte **otevřete Seznam testů** zadat název a umístění seznamu stop.

 Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.

## <a name="debug-and-analyze-unit-tests"></a>Ladění a analýza testů jednotek

### <a name="debug-unit-tests"></a>Ladění testů jednotky

Průzkumník testů můžete použít ke spuštění relace ladění pro testy. Krokování kódu s ladicím programem Visual Studio bez problémů přejdete vpřed a zpět mezi testováním částí a testovaný projekt. Spuštění ladění:

1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metod, které chcete ladit.

    > [!NOTE]
    > Vzhledem k tomu, že zkušební metody lze spustit v libovolném pořadí, nastavte zarážky v všechny testovací metody, které chcete ladit.

2. V Průzkumníku testů vyberte testovací metody a pak zvolte **ladit vybrané testy** v místní nabídce.

   Další informace o ladicím programu, najdete v části [ladit v sadě Visual Studio](../debugger/debugging-in-visual-studio.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnostika problémů s výkonem test – metoda

 Chcete-li diagnostikovat, proč testovací metoda trvá příliš dlouho, v Průzkumníku testů vyberte metodu a zvolte **profilu** v místní nabídce. Zobrazit [prohlížeč výkonu](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Analyzovat pokrytí kódem jednotkového testu

Můžete určit množství kódu produktu, který je skutečně testován prostřednictvím testů jednotky pomocí nástroje pokrytí kódu sady Visual Studio. Můžete spustit pokrytí kódem u vybraných testů nebo u všech testů v řešení.

Pokud chcete spustit pokrytí kódu pro testovací metody v řešení:

1. Zvolte **testy** v nabídce sady Visual Studio a klikněte na tlačítko **analyzovat pokrytí kódu**.

2. Z podnabídky zvolte jeden z následujících příkazů:

    - **Vybrané testy** spouští testovací metody, které jste vybrali v aplikaci Test Explorer.

    - **Všechny testy** spustí všechny testovací metody v řešení.

**Výsledky pokrytí kódu** okno zobrazuje procento bloků kódu produktu, které byly vykonány podle řádku, funkce, třídy, oboru názvů a modulu.

Další informace najdete v tématu [použití pokrytí kódu k určení, kolik kódu je právě testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Testování klávesové zkratky

Testy můžete spustit z **Průzkumníka testů**, tak, že kliknete pravým tlačítkem v editoru kódu v testu a vyberete **spuštění testu**, nebo s použitím výchozí [zástupce Průzkumník testů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) v Visual Studio. Některé zkratky jsou založené na kontextu. To znamená, že spustit nebo ladit testy založené na to, kde je kurzor v editoru kódu. Pokud ukazatel myši nachází uvnitř testovací metoda, která testovacích běhů metoda. Pokud je kurzor na úrovni třídy a poté spusťte všechny testy v dané třídě. To je stejný pro úroveň oboru názvů.

|Časté příkazy| Klávesové zkratky|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**CTRL**+**R**, **Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**CTRL**+**R**, **T**|

> [!NOTE]
> Nelze spustit test v abstraktní třídě, protože testy jsou definována pouze v abstraktní třídy a není vytvořena instance. Pro spouštění testů z abstraktní třídy, vytvořte třídu, která dědí z abstraktní třídy.

## <a name="see-also"></a>Viz také:

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Spuštění testování částí v podobě 64bitového procesu](../test/run-a-unit-test-as-a-64-bit-process.md)
