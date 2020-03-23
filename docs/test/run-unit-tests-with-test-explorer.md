---
title: Spuštění a ladění testů částí pomocí Průzkumníka testů
description: Přečtěte si, jak spustit testy pomocí Průzkumníka testů v sadě Visual Studio. Toto téma popisuje, jak povolit automatické spuštění testů po sestavení, zobrazit výsledky testů, seskupit a filtrovat seznam testů, vytvořit seznamy stop, ladit testy a používat testovací zkratky.
ms.date: 07/29/2019
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b183c1939ed48351bc15dacff31c85af46286ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278518"
---
# <a name="run-unit-tests-with-test-explorer"></a>Spouštění testů částí pomocí Průzkumníka testů

Pomocí Průzkumníka testů spusťte testy částí z visual studia nebo projektů testování částí jiných výrobců. Průzkumník testů můžete také použít k seskupení testů do kategorií, filtrování seznamu testů a vytváření, ukládání a spouštění seznamů stop testů. Můžete ladit testy a analyzovat výkon testu a pokrytí kódu.

Visual Studio obsahuje rozhraní pro testování částí Microsoft pro spravovaný i nativní kód. Průzkumník testů však můžete také spustit libovolné rozhraní testování částí, který implementoval adaptér Průzkumníka testů. Další informace o instalaci rozhraní pro testování částí jiných výrobců naleznete v [tématu Instalace architektur testování částí jiných výrobců.](../test/install-third-party-unit-test-frameworks.md)

**Průzkumník testů** můžete spustit testy z více testovacích projektů v řešení a z testovacích tříd, které jsou součástí projektů produkčního kódu. Testovací projekty můžete použít různé rozhraní testování částí. Při kódování kódu je napsáno pro .NET, testovací projekt může být zapsán v libovolném jazyce, který také cíle .NET, bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ musí být testovány pomocí rozhraní testování částí jazyka C++. Další informace naleznete v [tématu Write testování částí pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Spuštění testů v Průzkumníkovi testů


Při vytváření testovacího projektu se testy zobrazí v Průzkumníku testů. Pokud Průzkumník testů není viditelný, zvolte **Testovat** v nabídce Visual Studio, zvolte **Windows**a pak zvolte **Test Explorer**.


::: moniker range="vs-2017"
![Průzkumník testování částí](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Průzkumník testů](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Při spuštění, zápisu a opětovném spuštění testů průzkumník testů zobrazí výsledky ve výchozích skupinách **neúspěšných testů**, **Předané testy**, **Přeskočené testy** a **Nespouštět testy**. Můžete změnit způsob, jakým Průzkumník testů seskupuje testy.
::: moniker-end
::: moniker range=">=vs-2019"
Při spouštění, psaní a opětovném spuštění testů průzkumník testů zobrazuje výsledky ve výchozím seskupení **aplikace Project**, **Namespace**a **Class**. Můžete změnit způsob, jakým Průzkumník testů seskupuje testy.
::: moniker-end

Většinu práce při hledání, uspořádání a spouštění testů můžete provádět na panelu nástrojů **Průzkumníka testů.**

::: moniker range="vs-2017"
![Spuštění testů z panelu nástrojů Průzkumníka testů](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Spuštění testů z panelu nástrojů Průzkumníka testů](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Spouštění testů

::: moniker range="vs-2017"
Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte jednu z těchto akcí:

- Chcete-li spustit všechny testy v řešení, zvolte **Spustit vše**.

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte **Spustit** a pak zvolte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete nabídku po kliknutí pravým tlačítkem myši pro vybraný test a pak zvolte **Spustit vybrané testy**.

- Pokud jednotlivé testy nemají žádné závislosti, které by bránily jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![UTE&#95;parallelicon&#45;malý](../test/media/ute_parallelicon-small.png) přepínat na panelu nástrojů. To může výrazně zkrátit dobu trvalou ke spuštění všech testů.

Panel **průchodu/selhání** v horní části okna **Průzkumníka testů** je animován při spuštění testů. Na konci testu se **pruh vyhovění/nevyhovění** změní na zelenou, pokud všechny testy proběhly nebo se změní na červenou, pokud se některý test nezdařil.
::: moniker-end
::: moniker range=">=vs-2019"
Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte jednu z těchto akcí:

- Chcete-li spustit všechny testy v řešení, zvolte ikonu **Spustit vše.**

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte ikonu **Spustit** a pak zvolte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete nabídku po kliknutí pravým tlačítkem myši pro vybraný test a pak zvolte **Spustit vybrané testy**.

- Pokud jednotlivé testy nemají žádné závislosti, které brání jejich spuštění v libovolném pořadí, zapněte paralelní spuštění testu v nabídce nastavení panelu nástrojů. To může výrazně zkrátit dobu trvalou ke spuštění všech testů.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Spuštění testů po každém sestavení
::: moniker range="vs-2017"
|Tlačítko|Popis|
|-|-|
|![Spustit po sestavení](../test/media/ute_runafterbuild_btn.png)|Chcete-li spustit testy částí po každém místním sestavení, zvolte **Testovat** ve standardní nabídce a pak zvolte **Spustit testy po sestavení** na panelu nástrojů **Průzkumníka testů.**|

> [!NOTE]
> Spuštění testů částí po každém sestavení vyžaduje Visual Studio 2017 Enterprise nebo Visual Studio 2019. V Sadě Visual Studio 2019 je součástí komunity a professional, stejně jako enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Chcete-li spustit testy částí po každém místním sestavení, otevřete ikonu nastavení na panelu nástrojů Průzkumníktestů a vyberte **spustit testy po sestavení**.
::: moniker-end

## <a name="view-test-results"></a>Zobrazit výsledky testů

Při spuštění, zápisu a opětovném spuštění testů průzkumník testů zobrazí výsledky ve skupinách **neúspěšných testů**, **Předané testy**, **Přeskočené testy** a **Nespouštět testy**. Podokno podrobností v dolní nebo boční části Průzkumníka testů zobrazí souhrn testovacího běhu.

### <a name="view-test-details"></a>Zobrazit podrobnosti testu

Chcete-li zobrazit podrobnosti o jednotlivých testech, vyberte test.

::: moniker range="vs-2017"
![Podrobnosti spuštění testu](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Podrobnosti spuštění testu](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

Podokno podrobností testu zobrazuje následující informace:

- Název zdrojového souboru a číslo řádku testovací metody.

- Stav testu.

- Uplynulý čas, který trvalo zkušební metody spustit.

Pokud se test nezdaří, zobrazí se také podokno podrobností:

- Zpráva vrácená rozhraní mj.

- Trasování zásobníku v době, kdy se test nezdařil.

### <a name="view-the-source-code-of-a-test-method"></a>Zobrazení zdrojového kódu testovací metody

Chcete-li zobrazit zdrojový kód testovací metody v editoru sady Visual Studio, vyberte test a pak zvolte **Otevřít test** v nabídce po kliknutí pravým tlačítkem myši (Klávesnice: **F12).**

## <a name="group-and-filter-the-test-list"></a>Seskupení a filtrování testovacího seznamu

Průzkumník testů umožňuje seskupit testy do předdefinovaných kategorií. Většina rámců testování částí, které běží v Průzkumníku testů, umožňuje definovat vlastní kategorie a dvojice kategorií a hodnot pro seskupení testů. Můžete také filtrovat seznam testů porovnáním řetězců s vlastnostmi testu.

### <a name="group-tests-in-the-test-list"></a>Skupinové testy v seznamu testů

::: moniker range="vs-2017"
Chcete-li změnit způsob uspořádání testů, zvolte **Group By** šipku ![dolů vedle](../test/media/ute_groupby_btn.png) tlačítka Skupina podle tlačítka Test Explorer a vyberte nová kritéria seskupení.

![Seskupit testy podle kategorie v Průzkumníkovi testů](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Průzkumník testů umožňuje seskupit testy do hierarchie. Výchozí seskupení hierarchie je **Project**, **Namespace**a then **Class**. Chcete-li změnit způsob uspořádání testů, zvolte tlačítko **Group By** ![](../test/media/ute_groupby_btn.png) Skupina podle tlačítka Test Explorer a vyberte nová kritéria seskupení.

![Seskupit testy podle kategorie v Průzkumníkovi testů](../test/media/vs-2019/test-explorer-groupby-162.png)

Můžete definovat vlastní úrovně hierarchie a skupiny podle **státu** a potom **třídy** například výběrem možnosti Seskupit podle v upřednostňovaném pořadí.

![Seskupit podle státu a potom třídy](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Skupiny Průzkumníka testů

::: moniker range="vs-2017"
|Skupina|Popis|
|-|-----------------|
|**Doba trvání**|Skupiny testují podle doby spuštění: **Rychlé**, **Střední**a **Pomalé**.|
|**Výsledek**|Seskupí testy podle výsledků spuštění: **Neúspěšné testy**, **Přeskočené testy**, **Předané testy**.|
|**Vlastnosti**|Skupiny testují podle dvojic kategorií a hodnot, které definujete. Syntaxe k určení kategorií vlastností a hodnot je definována rozhraním testování částí.|
|**Projektu**|Skupiny testují podle názvu projektů.|
::: moniker-end
::: moniker range=">=vs-2019"
|Skupina|Popis|
|-|-----------------|
|**Doba trvání**|Seskupí testy podle doby spuštění: **Rychlé**, **Střední**a **Pomalé**.|
|**Stav**|Skupiny testů podle výsledků spuštění: **Neúspěšné testy**, **Přeskočené testy**, **Předané testy**, **Nespuštěno**|
|**Cílová architektura** | Skupinové testy podle rámce, jehož cílem je cílit na |
|**Namespace**|Seskupí testy podle obsahujícího oboru názvů.|
|**Projektu**|Seskupí testy podle obsahujícího projektu.|
|**Třída**|Skupiny testy obsahující třídy.|
::: moniker-end

### <a name="traits"></a>Vlastnosti

Vlastnost je obvykle dvojice název/hodnota kategorie, ale může to být také jedna kategorie. Vlastnosti mohou být přiřazeny k metodám, které jsou identifikovány jako zkušební metoda rámci testování částí. Rozhraní testování částí můžete definovat kategorie vlastností. Do kategorií vlastností můžete přidat hodnoty a definovat tak vlastní dvojice názvů a hodnot kategorií. Syntaxe k určení kategorií vlastností a hodnot je definována rozhraním testování částí.

**Vlastnosti v rozhraní Microsoft Unit Testing Framework pro spravovaný kód**

V rozhraní testování částí microsoftu pro spravované aplikace definujete v <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atributu dvojici znaků a hodnot. Testovací rámec také obsahuje tyto předdefinované vlastnosti:

|Vlastnost|Popis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategorie Vlastník je definována rozhraním testování částí a vyžaduje, abyste zadali řetězcovou hodnotu vlastníka.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategorie Priority je definována rozhraním testování částí a vyžaduje, abyste zadali celou hodnotu priority.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory Atribut umožňuje zadat kategorii bez hodnoty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atribut TestProperty umožňuje definovat dvojici kategorií/hodnot vlastností.|


**Vlastnosti v rozhraní Microsoft Unit Testing Framework pro C++**

Informace naleznete [v tématu Jak používat rozhraní Microsoft Unit Testing Framework pro jazyk C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Vytvoření vlastních seznamů stop

::: moniker range="vs-2017"
Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam stop, testy v seznamu se zobrazí v Průzkumníkovi testů. Test můžete přidat do více než jednoho seznamu stop a všechny testy v projektu jsou k dispozici, když zvolíte výchozí seznam stop **Všechny testy.**

![Výběr seznamu stop](../test/media/ute_playlist.png)

**Chcete-li vytvořit seznam stop**, zvolte jeden nebo více testů v Průzkumníkovi testů. V nabídce pravým tlačítkem myši zvolte **Přidat do seznamu stop stop** > **.** Uložte soubor s názvem a umístěním, které zadáte v dialogovém okně **Vytvořit nový seznam stop.**

**Chcete-li přidat testy do seznamu stop**, zvolte jeden nebo více testů v Průzkumníkovi testů. V nabídce pravým tlačítkem myši zvolte **Přidat do seznamu stop**a pak zvolte seznam stop, do kterého chcete testy přidat.

**Chcete-li otevřít seznam stop**, zvolte **Testovat** > **seznam stop** z nabídky Visual Studio a buď zvolte ze seznamu naposledy použitých seznamů stop, nebo zvolte Otevřít seznam **stop,** abyste určili název a umístění seznamu stop.

Pokud jednotlivé testy nemají žádné závislosti, které by bránily jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![UTE&#95;parallelicon&#45;malý](../test/media/ute_parallelicon-small.png) přepínat na panelu nástrojů. To může výrazně zkrátit dobu trvalou ke spuštění všech testů.
::: moniker-end
::: moniker range=">=vs-2019"
Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam stop, testy v seznamu se zobrazí na nové kartě Průzkumník testů. Test můžete přidat do více než jednoho seznamu stop.

**Chcete-li vytvořit seznam stop**, zvolte jeden nebo více testů v Průzkumníkovi testů. V nabídce pravým tlačítkem myši zvolte **Přidat do seznamu stop** > **seznamu stop**.

![Vytvoření seznamu stop](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Seznam stop se otevře na nové kartě Průzkumník a test. Tento seznam stop můžete použít jednou a pak jej zahodit, nebo můžete klepnout na tlačítko **Uložit** v panelu nástrojů okna seznamu stop a pak vybrat název a umístění pro uložení seznamu stop.

![Seznam stop se otevře na samostatné kartě Průzkumník a test](../test/media/vs-2019/test-explorer-playlist-tab-16-2.png)

**Chcete-li vytvořit seznam stop**, zvolte jeden nebo více testů v Průzkumníkovi testů. Klikněte pravým tlačítkem myši a zvolte **Přidat do seznamu stop seznamu** > **stop**.

**Chcete-li otevřít seznam stop**, zvolte ikonu seznamu stop na panelu nástrojů sady Visual Studio a v nabídce vyberte dříve uložený soubor seznamu stop.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Sloupce Průzkumníka testů

[Skupiny](#test-explorer-groups) jsou také k dispozici jako sloupce v Průzkumníku testů, spolu s vlastností, trasování zásobníku, chybová zpráva a plně kvalifikovaný název. Většina sloupců není ve výchozím nastavení viditelná a můžete přizpůsobit, které sloupce se zobrazí, a pořadí, ve kterém se zobrazují.

![Seskupit podle státu a potom třídy](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtrování, řazení a změna uspořádání testovacích sloupců

Sloupce lze filtrovat, seřadit a přeuspořádat.
* Chcete-li filtrovat podle určitých znaků, klepněte na ikonu filtru v horní části sloupce Vlastnosti.

  ![Sloupec, filtr](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Chcete-li změnit pořadí sloupců, klikněte na záhlaví sloupce a přetáhněte ho doleva nebo doprava.

* Chcete-li seřadit sloupec, klikněte na záhlaví sloupce. Ne všechny sloupce lze seřadit. Můžete také řadit podle sekundárního sloupce podržením klávesy **Shift** a kliknutím na další záhlaví sloupce.

  ![Řazení sloupců](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Hledání a filtrování seznamu testů

Pomocí vyhledávacích filtrů Průzkumníka testů můžete také omezit testovací metody v projektech, které zobrazíte a spustíte.

Když zadáte řetězec do vyhledávacího pole **Průzkumníka testů** a **zvolíte Enter**, seznam testů se vyfiltruje tak, aby zobrazoval pouze ty testy, jejichž plně kvalifikované názvy obsahují řetězec.

Filtrování podle různých kritérií:

1. Otevřete rozevírací seznam napravo od vyhledávacího pole.

2. Zvolte nová kritéria.

3. Mezi uvozovky zadejte hodnotu filtru. Pokud chcete vyhledat přesnou shodu na řetězci namísto obsahující shody, použijte znaménko rovná se (=) místo dvojtečky (:).

::: moniker range="vs-2017"
![Testy filtrů v Průzkumníkovi testů](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Testy filtrů v Průzkumníkovi testů](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Hledání jsou malá a velká písmena a odpovídají zadanému řetězci libovolné části hodnoty kritéria.

::: moniker range="vs-2017"
|Kvalifikátor|Popis|
|-|-----------------|
|**Vlastnost**|Vyhledá kategorii vlastností i hodnotu shody. Syntaxe k určení kategorií vlastností a hodnot jsou definovány rozhraním testování částí.|
|**Projektu**|Vyhledá názvy testovacích projektů pro shody.|
|**Chybová zpráva**|Prohledá uživatelem definované chybové zprávy vrácené neúspěšnými nepodmíněnými výrazy pro shody.|
|**Cesta k souboru**|Vyhledá plně kvalifikovaný název souboru souborů testovacího zdroje pro shody.|
|**Plně kvalifikovaný název**|Prohledá plně kvalifikovaný název oborů názvů test, tříd a metod pro shody.|
|**Výstup**|Prohledává uživatelem definované chybové zprávy, které jsou zapsány do standardního výstupu (stdout) nebo standardní chyba (stderr). Syntaxe pro určení výstupních zpráv je definována rozhraním testování částí.|
|**Výsledek**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **Neúspěšné testy**, **Přeskočené testy**, **Předané testy**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Kvalifikátor|Popis|
|-|-----------------|
|**Stav**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **Neúspěšné testy**, **Přeskočené testy**, **Předané testy**.|
|**Vlastnosti**|Vyhledá kategorii vlastností i hodnotu shody. Syntaxe k určení kategorií vlastností a hodnot jsou definovány rozhraním testování částí.|
|**Plně kvalifikovaný název**|Prohledá plně kvalifikovaný název oborů názvů test, tříd a metod pro shody.|
|**Projektu**|Vyhledá názvy testovacích projektů pro shody.|
|**Cílová architektura**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **Neúspěšné testy**, **Přeskočené testy**, **Předané testy**.|
|**Namespace**|Vyhledá v oborech názvů test shody.|
|**Třída**|Vyhledá názvy testovacích tříd pro shody.|
::: moniker-end

Chcete-li vyloučit podmnožinu výsledků filtru, použijte následující syntaxi:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Například `FullName:"MyClass" - FullName:"PerfTest"` vrátí všechny testy, které obsahují "MyClass" v jejich názvu, s výjimkou testů, které také obsahují "PerfTest" v jejich názvu.

## <a name="debug-and-analyze-unit-tests"></a>Ladění a analýza testů částí

Průzkumník testů můžete použít ke spuštění relace ladění pro vaše testy. Krokování kódu s ladicím programem sady Visual Studio vás bez problémů přenese tam a zpět mezi testy částí a testovaného projektu. Zahájení ladění:

1. V editoru Visual Studio nastavte zarážku v jedné nebo více testovacích metod, které chcete ladit.

    > [!NOTE]
    > Vzhledem k tomu, že testovací metody lze spustit v libovolném pořadí, nastavte zarážky ve všech testovacích metod, které chcete ladit.

2. V Průzkumníkovi testů vyberte testovací metody a v nabídce po kliknutí pravým tlačítkem myši zvolte **Ladit vybrané testy.**

   Další informace o ladicím programu naleznete v tématu [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnostikovat problémy s výkonem zkušební metody

Chcete-li diagnostikovat, proč testovací metoda trvá příliš dlouho, vyberte metodu v Průzkumníkovi testů a v nabídce po kliknutí pravým tlačítkem myši zvolte **vybraný test** profilu. Viz [sestava profilování instrumentace](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).

### <a name="analyze-unit-test-code-coverage"></a>Analyzovat pokrytí kódu testování částí

Můžete určit množství kódu produktu, který je ve skutečnosti testován testy částí pomocí nástroje pokrytí kódu Sady Visual Studio, který je k dispozici v edici Visual Studio Enterprise. Pokrytí kódu můžete spustit na vybraných testech nebo na všech testech v řešení.

Spuštění pokrytí kódu pro testovací metody v řešení:

::: moniker range="vs-2017"

1. Na horním řádku nabídek zvolte **Testovat** a pak zvolte **Analyzovat pokrytí kódu**.

2. Z podnabídky vyberte jeden z následujících příkazů:

    - **Vybrané testy** spustí testovací metody, které jste vybrali v Průzkumníku testů.

    - **Všechny testy** spustí všechny zkušební metody v řešení.

::: moniker-end

::: moniker range=">=vs-2019"

* Klikněte pravým tlačítkem myši do Průzkumníka testů a vyberte **Analyzovat pokrytí kódu pro vybrané testy.**

::: moniker-end

Okno **Výsledky pokrytí kódu** zobrazuje procento bloků kódu produktu, které byly uplatněny podle řádku, funkce, třídy, oboru názvů a modulu.

Další informace naleznete [v tématu Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Testovat zkratky

Testy lze spustit z Průzkumníka testů kliknutím pravým tlačítkem myši v editoru kódu v testu a výběrem **spustit test** nebo pomocí [výchozích zástupců Průzkumníka testů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) v sadě Visual Studio. Některé zkratky jsou založeny na kontextu. To znamená, že spouštějí nebo ladí testy podle toho, kde je kurzor v editoru kódu. Pokud je kurzor uvnitř testovací metody, spustí se tato testovací metoda. Pokud je kurzor na úrovni třídy, spustí se všechny testy v této třídě. To je stejné i pro úroveň oboru názvů.

|Časté příkazy| Klávesové zkratky|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl**+**R**, **Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**Ctrl**+**R**, **T**|
|TestExplorer.RunAllTests|**Ctrl**+**R**, **A**|
|TestExplorer.RepeatLastRun|**Ctrl**+**R**, **L**|

> [!NOTE]
> Nelze spustit test v abstraktní třídě, protože testy jsou definovány pouze v abstraktnítřídy a není vytvořena instance. Chcete-li spustit testy v abstraktnítřídy, vytvořte třídu, která je odvozena z abstraktní třídy.

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Spuštění testování částí v podobě 64bitového procesu](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Průzkumník testů – nejčastější dotazy](test-explorer-faq.md)
