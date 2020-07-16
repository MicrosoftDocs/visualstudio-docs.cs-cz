---
title: Spouštění testů částí pomocí Průzkumníka testů
description: Naučte se spouštět testy pomocí Průzkumníka testů v aplikaci Visual Studio. V tomto tématu se dozvíte, jak povolit automatické testovací běhy po sestavení, zobrazení výsledků testů, seskupení a filtrování seznamu testů, vytvoření seznamů a používání testovacích zástupců.
ms.date: 07/14/2020
ms.topic: how-to
f1_keywords:
- vs.unittesting.testexplorer.overview
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2d7dc38f1a25826ba275738cd8e758a2ad5d90e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386638"
---
# <a name="run-unit-tests-with-test-explorer"></a>Spouštění testů částí pomocí Průzkumníka testů

Pomocí Průzkumníka testů spusťte testy jednotek ze sady Visual Studio nebo projektů testování částí třetích stran. Můžete také použít Průzkumníka testů k seskupení testů do kategorií, filtrování seznamu testů a vytváření, ukládání a spouštění seznamů testů. Můžete také analyzovat pokrytí kódu a [ladit testy jednotek](../test/debug-unit-tests-with-test-explorer.md).

**Průzkumník testů** může spustit testy z více projektů testů v řešení a z testovacích tříd, které jsou součástí projektů produkčního kódu. Testovací projekty mohou používat různé architektury testování částí. Při zápisu testovaného kódu pro rozhraní .NET může být testovací projekt napsán v jakémkoli jazyce, který také cílí na rozhraní .NET bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ musí být testovány pomocí rozhraní pro testování částí v jazyce C++.

## <a name="build-your-test-project"></a>Sestavení testovacího projektu

Pokud ještě nemáte projekt testů nastavený v řešení sady Visual Studio, musíte nejprve vytvořit a sestavit testovací projekt.

- [Začínáme s testováním částí (.NET)](../test/getting-started-with-unit-testing.md)
- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)

Visual Studio obsahuje rozhraní pro testování částí společnosti Microsoft pro spravovaný i nativní kód. Nicméně Průzkumník testů může také spustit libovolné rozhraní testování částí, které implementovalo adaptér Průzkumníka testů. Další informace o instalaci rozhraní pro testování částí třetích stran najdete v tématu [instalace rozhraní pro testování částí třetích stran](../test/install-third-party-unit-test-frameworks.md) .

## <a name="run-tests-in-test-explorer"></a>Spustit testy v Průzkumníku testů

Při sestavování testovacího projektu se testy zobrazí v Průzkumníku testů. Pokud není Průzkumník testů viditelný, zvolte možnost **test** v nabídce aplikace Visual Studio, zvolte možnost **Windows**a pak zvolte možnost **Průzkumník testů**.

::: moniker range="vs-2017"
![Průzkumník testů jednotek](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Průzkumník testů](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Při spuštění, zápisu a opětovném spuštění testů se v Průzkumníku testů zobrazí výsledky ve výchozích skupinách **neúspěšných testů**, **Úspěšné testy**, **přeskočené testy** a **nespouštějí se testy**. Můžete změnit způsob, jakým Průzkumník testů seskupí testy.
::: moniker-end
::: moniker range=">=vs-2019"
Při spuštění, zápisu a opětovném spuštění testů zobrazuje Průzkumník testů výsledky ve výchozím seskupení **projektu**, **oboru názvů**a **třídy**. Můžete změnit způsob, jakým Průzkumník testů seskupí testy.
::: moniker-end

Na panelu nástrojů **Průzkumníka testů** můžete provádět spoustu práce při hledání, organizování a spouštění testů.

::: moniker range="vs-2017"
![Spustit testy z panelu nástrojů Průzkumníka testů](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Spustit testy z panelu nástrojů Průzkumníka testů](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Spouštění testů

::: moniker range="vs-2017"
Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte jednu z následujících akcí:

- Chcete-li spustit všechny testy v řešení, vyberte možnost **Spustit vše**.

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte možnost **Spustit** a poté vyberte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete nabídku kliknutím pravým tlačítkem pro vybraný test a pak zvolte možnost **Spustit vybrané testy**.

- Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malá](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.

V horní části okna **Průzkumníka testů** je animovaný **řádek Pass/selhat** , protože testy jsou spouštěny. Při uzavírání testovacího běhu se **pruh úspěch/selhání** změní na zelený, pokud všechny testy proběhly úspěšně, nebo pokud dojde k selhání testu na červenou.
::: moniker-end
::: moniker range=">=vs-2019"
Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte jednu z následujících akcí:

- Chcete-li spustit všechny testy v řešení, vyberte ikonu **Spustit vše** .

- Chcete-li spustit všechny testy ve výchozí skupině, zvolte ikonu **spuštění** a pak zvolte skupinu v nabídce.

- Vyberte jednotlivé testy, které chcete spustit, otevřete nabídku kliknutím pravým tlačítkem pro vybraný test a pak zvolte možnost **Spustit vybrané testy**.

- Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní spuštění testů v nabídce nastavení na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Spustit testy po každém sestavení
::: moniker range="vs-2017"
|Tlačítko|Popis|
|-|-|
|![Spustit po sestavení](../test/media/ute_runafterbuild_btn.png)|Chcete-li spustit testy jednotek po každém místním sestavení, zvolte možnost **test** v nabídce Standard a pak zvolte možnost **Spustit testy po sestavení** na panelu nástrojů **Průzkumníka testů** .|

> [!NOTE]
> Spuštění testů jednotek po každém sestavení vyžaduje Visual Studio 2017 Enterprise nebo Visual Studio 2019. V aplikaci Visual Studio 2019 je součástí komunity a Professional i Enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Chcete-li spustit testy jednotek po každém místním sestavení, otevřete ikonu nastavení na panelu nástrojů Průzkumníka testů a vyberte možnost **Spustit testy po sestavení**.
::: moniker-end

## <a name="view-test-results"></a>Zobrazit výsledky testu

Když spouštíte, píšete a znovu spustíte testy, Průzkumník testů zobrazí výsledky ve skupinách **neúspěšných testů**, **úspěšných testů**, **přeskočených testů** a **nespustí testy**. Podokno podrobností v dolní nebo boční části Průzkumníka testů zobrazuje souhrn testovacího běhu.

### <a name="view-test-details"></a>Zobrazit podrobnosti testu

Chcete-li zobrazit podrobnosti o jednotlivých testech, vyberte test.

::: moniker range="vs-2017"
![Podrobnosti spuštění testu](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Podrobnosti spuštění testu](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

V podokně podrobností testu se zobrazí následující informace:

- Název zdrojového souboru a číslo řádku testovací metody.

- Stav testu.

- Uplynulý čas, po který trvalo spuštění testovací metody.

Pokud se test nezdařil, podokno podrobností také obsahuje:

- Zpráva vrácená jednotkou testu jednotek pro test.

- Trasování zásobníku v době, kdy se test nezdařil.

### <a name="view-the-source-code-of-a-test-method"></a>Zobrazit zdrojový kód testovací metody

Chcete-li zobrazit zdrojový kód testovací metody v editoru sady Visual Studio, vyberte test a pak zvolte možnost **Otevřít test** v místní nabídce kliknutím pravým tlačítkem myši (klávesnice: **F12**).

## <a name="group-and-filter-the-test-list"></a>Seskupení a filtrování seznamu testů

Průzkumník testů umožňuje seskupit testy do předdefinovaných kategorií. Většina rozhraní testů jednotek, která běží v Průzkumníku testů, vám umožní definovat vlastní kategorie a páry kategorií a hodnot pro seskupení testů. Můžete také filtrovat seznam testů porovnáním řetězců s vlastnostmi testu.

### <a name="group-tests-in-the-test-list"></a>Seskupit testy v seznamu testů

::: moniker range="vs-2017"
Chcete-li změnit způsob, jakým jsou testy uspořádány, zvolte šipku dolů vedle **tlačítka skupina pro tlačítko** ![ test Průzkumníka ](../test/media/ute_groupby_btn.png) a vyberte Nová kritéria seskupení.

![Seskupit testy podle kategorie v Průzkumníku testů](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Průzkumník testů umožňuje seskupit testy do hierarchie. Výchozím seskupením hierarchie je **projekt**, **obor názvů**a **Třída**. Chcete-li změnit způsob, jakým jsou testy uspořádány, zvolte tlačítko **Seskupit v** ![ Průzkumníku testu ](../test/media/ute_groupby_btn.png) a vyberte Nová kritéria seskupení.

![Seskupit testy podle kategorie v Průzkumníku testů](../test/media/vs-2019/test-explorer-groupby-162.png)

Můžete definovat vlastní úrovně hierarchie a seskupit podle **stavu** a pak **třídou** , například výběrem možnosti Seskupit podle v upřednostňovaném pořadí.

![Seskupit podle State a pak Class](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Skupiny Průzkumníka testů

::: moniker range="vs-2017"
|Skupina|Popis|
|-|-----------------|
|**Doba trvání**|Seskupuje test podle doby spuštění: **rychlá**, **střední**a **pomalá**.|
|**Zaznamenaný**|Seskupí testy podle výsledků spuštění: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**.|
|**Traits**|Seskupí testy podle párů kategorií/hodnot, které definujete. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|
|**Projekt**|Seskupí testy podle názvu projektů.|
::: moniker-end
::: moniker range=">=vs-2019"
|Skupina|Popis|
|-|-----------------|
|**Doba trvání**|Seskupí testy podle doby spuštění: **rychlá**, **střední**a **pomalá**.|
|**Stav**|Seskupí testy podle výsledků spuštění: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**, **Nespuštěné** .|
|**Cílová architektura** | Seskupí testy podle cíle v rámci svých projektů. |
|**Obor názvů**|Seskupí testy podle obsahujícího oboru názvů.|
|**Projekt**|Seskupí testy podle obsahujícího projektu.|
|**Třída**|Seskupí testy pomocí obsahující třídy.|
::: moniker-end

### <a name="traits"></a>Traits

Vlastnost je obvykle dvojice název/hodnota kategorie, ale může to být také jedna kategorie. Vlastnostem lze přiřadit metody, které jsou identifikovány jako testovací metoda v rámci jednotkového testu. Rozhraní testování částí může definovat kategorie vlastností. Přidáním hodnot do kategorií vlastností můžete definovat vlastní páry název-hodnota kategorie. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.

**Vlastnosti v rozhraní testování částí společnosti Microsoft pro spravovaný kód**

V rozhraní Microsoft pro testování částí pro spravované aplikace definujete v atributu dvojici název/hodnota vlastnosti <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . Testovací rozhraní obsahuje také tyto předdefinované vlastnosti:

|Znak|Popis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategorie vlastník je definována v rámci testovacího rozhraní jednotky a vyžaduje zadání řetězcové hodnoty vlastníka.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategorie priority je definována v rámci testovacího rozhraní jednotky a vyžaduje, abyste zadali celočíselnou hodnotu priority.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atribut TestCategory umožňuje zadat kategorii bez hodnoty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atribut TestProperty umožňuje definovat vlastnost páru kategorie/hodnota.|


**Vlastnosti v rozhraní Microsoft Unit Testing Framework pro C++**

Viz [Jak používat Microsoft Unit Testing Framework pro C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Vytváření vlastních seznamů testů

::: moniker range="vs-2017"
Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam testů, testy v seznamu se zobrazí v Průzkumníku testů. Test můžete přidat do více než jednoho seznamu skladeb a všechny testy v projektu jsou k dispozici, když vyberete výchozí seznam **testů pro všechny testy** .

![Zvolit seznam testů](../test/media/ute_playlist.png)

**Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v Průzkumníku testů. V nabídce kliknutím pravým tlačítkem myši vyberte možnost **Přidat do seznamu**  >  **NewPlaylist**. Uložte soubor s názvem a umístěním, které zadáte v dialogovém okně **vytvořit nový seznam** testů.

**Chcete-li přidat testy do seznamu stop**, vyberte jeden nebo více testů v Průzkumníku testů. V nabídce klepněte pravým tlačítkem myši na položku **Přidat do seznamu stop**a zvolte seznam testů, do kterého chcete přidat testy.

**Chcete-li otevřít seznam stop**, zvolte možnost **test** > **seznamu** testů v nabídce aplikace Visual Studio a buď zvolte ze seznamu naposledy použitých seznamů stop, nebo zvolte možnost **otevřít seznam stop** a zadejte název a umístění seznamu skladeb.

Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malá](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.
::: moniker-end
::: moniker range=">=vs-2019"
Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam testů, testy v seznamu se zobrazí na nové kartě Průzkumník testů. Test můžete přidat do více než jednoho seznamu skladeb.

**Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v Průzkumníku testů. V nabídce kliknutím pravým tlačítkem myši vyberte možnost **Přidat do seznamu skladeb**  >  **Nový seznam**.

![Vytvořit seznam testů](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Seznam se otevře na nové kartě Průzkumník testů. Tento seznam je možné použít jednou a pak ho zahodit, nebo můžete kliknout na tlačítko **Uložit** na panelu nástrojů v okně seznamu stop a pak vybrat název a umístění pro uložení seznamu.

![Seznam testů se otevře na samostatné kartě Průzkumníka testů.](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v Průzkumníku testů. Klikněte pravým tlačítkem a vyberte **Přidat do seznamu**testů  >  **Nový seznam**testů.

**Chcete-li otevřít seznam**testů, zvolte ikonu seznamu stop na panelu nástrojů sady Visual Studio a v nabídce vyberte dříve uložený soubor seznamu testů.

Pokud **chcete upravit seznam stop**, můžete kliknout pravým tlačítkem na libovolný test a pomocí možností nabídky ho přidat nebo odebrat ze seznamu testů.

Počínaje verzí Visual Studio 2019 verze 16,7 můžete zvolit tlačítko **Upravit** na panelu nástrojů. Zaškrtávací políčka se zobrazí vedle testů, které ukazují, jaké testy jsou zahrnuty a vyloučeny v seznamu. Teď skupiny upravte podle potřeby.

![Tlačítko Upravit seznam skladeb](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

Můžete také zaškrtnout nebo zrušit kontrolu polí nadřazených skupin v hierarchii. Tato akce vytvoří dynamický seznam testů, který vždy aktualizuje seznam stop na základě testů, které jsou v dané skupině. Například pokud umístíte značku zaškrtnutí vedle třídy, všechny testy přidané z této třídy se stávají součástí tohoto seznamu testů. Pokud odstraníte test z této třídy, je odebrán ze seznamu. Další informace o pravidlech najdete tak, že seznam stop uložíte na panelu nástrojů na tlačítko Uložit a otevřete soubor *. playlist* , který je vytvořený na disku. Tento soubor obsahuje seznam všech pravidel a jednotlivých testů, které tvoří seznam testů.

![Soubor XML se seznamem testů](../test/media/vs-2019/test-explorer-playlist-xml-file.png)
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Sloupce Průzkumníka testů

[Skupiny](#test-explorer-groups) jsou také k dispozici jako sloupce v Průzkumníku testů, spolu se vlastnostmi, trasováním zásobníku, chybovou zprávou a plně kvalifikovaným názvem. Většina sloupců není ve výchozím nastavení viditelná a můžete přizpůsobit zobrazené sloupce a pořadí, ve kterém se zobrazí.

![Seskupit podle State a pak Class](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtrování, řazení a změna uspořádání sloupců testu

Sloupce lze filtrovat, seřadit a změnit jejich uspořádání.
* Pokud chcete filtrovat konkrétní vlastnosti, klikněte na ikonu filtru v horní části sloupce vlastnosti.

  ![Filtr sloupců](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Chcete-li změnit pořadí sloupců, klikněte na záhlaví sloupce a přetáhněte je doleva nebo doprava.

* Pokud chcete sloupec seřadit, klikněte na záhlaví sloupce. Ne všechny sloupce lze seřadit. Můžete také řadit podle sekundárního sloupce podržením klávesy **SHIFT** a kliknutím na další záhlaví sloupce.

  ![Řazení sloupců](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Hledání a filtrování seznamu testů

Můžete také použít vyhledávací filtry Průzkumníka testů k omezení testovacích metod v projektech, které můžete zobrazit a spustit.

Když zadáte řetězec do vyhledávacího pole **Průzkumníka testů** a kliknete na tlačítko **ENTER**, seznam testů je filtrován tak, aby zobrazoval pouze testy, jejichž plně kvalifikované názvy obsahují řetězec.

Filtrování podle různých kritérií:

1. Otevřete rozevírací seznam napravo od vyhledávacího pole.

2. Vyberte Nová kritéria.

3. Zadejte hodnotu filtru mezi uvozovky. Pokud chcete vyhledat přesnou shodu řetězce místo obsahujícího shodu, použijte místo dvojtečky znak rovná se (=) (:).

::: moniker range="vs-2017"
![Filtrovat testy v Průzkumníku testů](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtrovat testy v Průzkumníku testů](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> V hledání jsou rozlišována malá a velká písmena a odpovídají zadanému řetězci všem částem hodnoty kritérií.

::: moniker range="vs-2017"
|Kvalifikátor|Popis|
|-|-----------------|
|**Znak**|Vyhledá shody v kategorii a hodnotě vlastností. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|
|**Projekt**|Vyhledá shody v názvech projektů testů.|
|**Chybová zpráva**|Vyhledá shodu v uživatelsky definovaných chybových zprávách vrácených neúspěšnými kontrolními výrazy.|
|**Cesta k souboru**|Vyhledá shody v plně kvalifikovaném názvu souboru zdrojových souborů testu.|
|**Plně kvalifikovaný název**|Vyhledá plně kvalifikovaný název testovacích oborů názvů, tříd a metod pro shody.|
|**Výstup**|Vyhledá chybové zprávy definované uživatelem, které jsou zapsány do standardního výstupu (stdout) nebo standardní chyby (stderr). Syntaxe pro určení výstupních zpráv je definována v rámci testovacího rozhraní jednotky.|
|**Zaznamenaný**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Kvalifikátor|Popis|
|-|-----------------|
|**Stav**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**.|
|**Traits**|Vyhledá shody v kategorii a hodnotě vlastností. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.|
|**Plně kvalifikovaný název**|Vyhledá plně kvalifikovaný název testovacích oborů názvů, tříd a metod pro shody.|
|**Projekt**|Vyhledá shody v názvech projektů testů.|
|**Cílová architektura**|Vyhledá názvy kategorií Průzkumníka testů pro shody: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**.|
|**Obor názvů**|Vyhledá shody v oborech názvů testu.|
|**Třída**|Vyhledá shody v názvech testovacích tříd.|
::: moniker-end

K vyloučení podmnožiny výsledků filtru použijte následující syntaxi:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Například `FullName:"MyClass" - FullName:"PerfTest"` vrátí všechny testy, které zahrnují "MyClass" v názvu, s výjimkou testů, které také zahrnují "PerfTest" v názvu.

### <a name="analyze-unit-test-code-coverage"></a>Analýza pokrytí kódu testu jednotek

Množství kódu produktu, který je skutečně testován pomocí testů jednotek, můžete určit pomocí nástroje pokrytí kódu sady Visual Studio, který je k dispozici v edici Visual Studio Enterprise. Můžete spustit pokrytí kódu pro vybrané testy nebo pro všechny testy v řešení.

Spuštění pokrytí kódu pro testovací metody v řešení:

::: moniker range="vs-2017"

1. Zvolte možnost **test** na horním řádku nabídek a pak zvolte možnost **Analyzovat pokrytí kódu**.

2. V podnabídce vyberte jeden z následujících příkazů:

    - **Vybrané testy** spouští testovací metody, které jste vybrali v Průzkumníku testů.

    - **Všechny testy** spustí všechny testovací metody v řešení.

::: moniker-end

::: moniker range=">=vs-2019"

* Klikněte pravým tlačítkem myši v Průzkumníku testů a vyberte možnost **Analyzovat pokrytí kódu pro vybrané testy** .

::: moniker-end

V okně **výsledky pokrytí kódu** se zobrazí procentuální podíl bloků kódu produktu, které byly uplatněny pomocí řádku, funkce, třídy, oboru názvů a modulu.

Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Zástupci testů

Testy lze spustit z Průzkumníka testů kliknutím pravým tlačítkem myši v editoru kódu na test a výběrem možnosti **Spustit test** nebo pomocí výchozího [zástupce Průzkumníka testů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) v aplikaci Visual Studio. Některé zástupce jsou založené na kontextu. To znamená, že spouštějí nebo [ladí testy](../test/debug-unit-tests-with-test-explorer.md) na základě toho, kde je kurzor v editoru kódu. Pokud je kurzor uvnitř testovací metody, pak se tato testovací metoda spustí. Pokud je kurzor na úrovni třídy, pak se spustí všechny testy v této třídě. To je stejné i pro úrovni oboru názvů.

|Časté příkazy| Klávesové zkratky|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**CTRL** + **R**, **CTRL** + **T**|
|TestExplorer.RunAllTestsInContext|**CTRL** + **R**, **T**|
|TestExplorer.RunAllTests|**CTRL** + **R**, **a**|
|TestExplorer.RepeatLastRun|**CTRL** + **R**, **L**|

> [!NOTE]
> Nemůžete spustit test v abstraktní třídě, protože testy jsou definovány pouze v abstraktních třídách a nikoli v instanci. Chcete-li spustit testy v abstraktních třídách, vytvořte třídu, která je odvozena z abstraktní třídy.

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Ladění testů částí pomocí Průzkumníka testů](../test/debug-unit-tests-with-test-explorer.md)
- [Spuštění testování částí v podobě 64bitového procesu](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Průzkumník testů – nejčastější dotazy](test-explorer-faq.md)
