---
title: Spouštění testů částí pomocí Průzkumníka testů
description: Naučte se spouštět testy pomocí Průzkumníka testů v Visual Studio. Toto téma popisuje, jak povolit automatické testovací běhy po sestavení, zobrazit výsledky testů, seskupit a filtrovat seznam testů, vytvářet seznamy stop a používat klávesové zkratky pro testy.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 26dbed25f42f40614597075ad26c855398b56025
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925121"
---
# <a name="run-unit-tests-with-test-explorer"></a>Spouštění testů částí pomocí Průzkumníka testů

Pomocí Průzkumníka testů můžete spouštět testy jednotek Visual Studio nebo jiných projektů testů jednotek. Pomocí Průzkumníka testů můžete také seskupit testy do kategorií, filtrovat seznam testů a vytvářet, ukládat a spouštět seznamy testů. Můžete také analyzovat pokrytí kódu a [ladit testy jednotek](../test/debug-unit-tests-with-test-explorer.md).

**Průzkumník testů** může spouštět testy z více projektů testů v řešení a z testovacích tříd, které jsou součástí projektů produkčního kódu. Projekty testů mohou používat různé architektury testování částí. Když je kód v rámci testu napsán pro .NET, projekt testů může být napsán v libovolném jazyce, který také cílí na .NET, bez ohledu na jazyk cílového kódu. Nativní projekty kódu C/C++ se musí testovat pomocí architektury testování částí jazyka C++.

## <a name="build-your-test-project"></a>Sestavení testovacího projektu

Pokud ještě nemáte ve svém testovacím řešení nastavený projekt Visual Studio, musíte nejprve vytvořit a sestavit testovací projekt.

- [Začínáme s testováním jednotek (.NET)](../test/getting-started-with-unit-testing.md)
- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)

Visual Studio obsahuje rozhraní Microsoftu pro testování částí pro spravovaný i nativní kód. Průzkumník testů ale může také spustit libovolné rozhraní testování částí, které má implementované adaptéry Průzkumníka testů. Další informace o instalaci testovacích architektur jednotek třetích stran najdete v tématu Instalace rozhraní testování částí [třetích stran.](../test/install-third-party-unit-test-frameworks.md)

## <a name="run-tests-in-test-explorer"></a>Spouštění testů v Průzkumníku testů

Když sestavíte projekt testů, zobrazí se testy v Průzkumníku testů. Pokud průzkumník testů není  viditelný, v nabídce Visual Studio vyberte Test, zvolte **Windows** a pak zvolte **Průzkumník** testů (nebo stiskněte **Ctrl**  +  **E,** **T).**

::: moniker range="vs-2017"
![Průzkumník testů jednotek](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Průzkumník testů](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Když testy spustíte, napíšete a znovu spustíte, Průzkumník testů zobrazí výsledky  ve výchozích skupinách neúspěšných testů **,** úspěšně provedených **testů,** přeskočení testů a nespouštěných **testů.** Můžete změnit způsob, jakým Průzkumník testů seskupuje testy.
::: moniker-end
::: moniker range=">=vs-2019"
Při spouštění, zápisu a opětovném spouštění testů zobrazí Průzkumník testů výsledky ve výchozím seskupení **projektů,** oborů **názvů** a **třídy**. Můžete změnit způsob, jakým Průzkumník testů seskupuje testy.
::: moniker-end

Velkou část práce při hledání, uspořádání a spouštění testů můžete provádět na panelu nástrojů **Průzkumníka** testů.

::: moniker range="vs-2017"
![Spouštění testů z panelu nástrojů Průzkumníka testů](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Spouštění testů z panelu nástrojů Průzkumníka testů](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Spouštění testů

::: moniker range="vs-2017"
Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte některou z následujících akcí:

- Pokud chcete spustit všechny testy v řešení, zvolte **Spustit vše** (nebo stiskněte **Ctrl** + **R**, **V).**

- Pokud chcete spustit všechny testy ve výchozí skupině, zvolte **Spustit** a pak v nabídce zvolte skupinu.

- Vyberte jednotlivé testy, které chcete spustit, otevřete nabídku po kliknutí pravým tlačítkem pro vybraný test a pak zvolte Spustit **vybrané** testy (nebo stiskněte **Ctrl** + **R,** **T).**

- Pokud jednotlivé testy nemají žádné závislosti, které by zabránily jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů pomocí ![Snímek obrazovky s přepínacím tlačítkem Paralelní provádění testů na Visual Studio panelu nástrojů Průzkumníka testů Když je toto tlačítko vybrané, testy poběží paralelně.](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může znatelně zkrátit dobu, po které se spustí všechny testy.

Panel **pro průchod/selhání** v horní části okna **Průzkumníka testů** je při spuštění testů animovaný. V závěru testovacího běhu se barva pruhu **pro průchod/selhání** změní na zelenou, pokud všechny testy proběhly úspěšně nebo zčervena, pokud některý test selhal.
::: moniker-end
::: moniker range=">=vs-2019"
Můžete spustit všechny testy v řešení, všechny testy ve skupině nebo sadu testů, které vyberete. Proveďte některou z následujících akcí:

- Pokud chcete spustit všechny testy v řešení, zvolte ikonu **Spustit vše** (nebo stiskněte **Ctrl** + **R**, **V).**

- Pokud chcete spustit všechny testy ve výchozí skupině, zvolte **ikonu Spustit** a pak v nabídce zvolte skupinu.

- Vyberte jednotlivé testy, které chcete spustit, otevřete nabídku po kliknutí pravým tlačítkem pro vybraný test a pak zvolte Spustit **vybrané** testy (nebo stiskněte **Ctrl** + **R,** **T).**

- Pokud jednotlivé testy nemají žádné závislosti, které by zabránily jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů v nabídce nastavení na panelu nástrojů. To může znatelně zkrátit dobu, po které se spustí všechny testy.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Spouštění testů po každém sestavení
::: moniker range="vs-2017"
|Tlačítko|Description|
|-|-|
|![Spuštění po sestavení](../test/media/ute_runafterbuild_btn.png)|Pokud chcete testy jednotek spustit po každém místním sestavení, zvolte  **Test** ve standardní nabídce a pak na panelu nástrojů **Průzkumník** testů zvolte Spustit testy po sestavení.|

> [!NOTE]
> Spouštění testů jednotek po každém sestavení vyžaduje Visual Studio 2017 Enterprise nebo Visual Studio 2019. V Visual Studio 2019 je součástí Community a Professional i Enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Pokud chcete testy jednotek spustit po každém místním sestavení, otevřete ikonu nastavení na panelu nástrojů Průzkumníka testů a vyberte **Spustit testy po sestavení**.
::: moniker-end

## <a name="view-test-results"></a>Zobrazení výsledků testů

Když testy spustíte, napíšete a znovu spustíte, Průzkumník testů zobrazí výsledky  ve skupinách neúspěšných **testů,** úspěšně provedených **testů,** přeskočení testů a nespouštěných **testů.** V podokně podrobností v dolní nebo boční části Průzkumníka testů se zobrazí souhrn testovacího běhu.

### <a name="view-test-details"></a>Zobrazení podrobností testu

Pokud chcete zobrazit podrobnosti o jednotlivém testu, vyberte test.

::: moniker range="vs-2017"
![Podrobnosti o spuštění testu](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Podrobnosti o spuštění testu](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

V podokně podrobností testu se zobrazí následující informace:

- Název zdrojového souboru a číslo řádku testovací metody.

- Stav testu

- Uplynulý čas, který testovací metoda trvala ke spuštění.

Pokud test selže, zobrazí se v podokně podrobností také:

- Zpráva vrácená architekturou testování částí pro test.

- Trasování zásobníku v době, kdy test selhal.

### <a name="view-the-source-code-of-a-test-method"></a>Zobrazení zdrojového kódu testovací metody

Pokud chcete zobrazit zdrojový kód testovací metody v editoru Visual Studio, vyberte  test a pak v nabídce po kliknutí pravým tlačítkem zvolte Otevřít test (nebo stiskněte **F12).**

## <a name="group-and-filter-the-test-list"></a>Seskupení a filtrování seznamu testů

Průzkumník testů umožňuje seskupit testy do předdefinovaných kategorií. Většina architektur testování částí, které běží v Průzkumníku testů, umožňuje definovat vlastní kategorie a páry kategorií a hodnot pro seskupení testů. Seznam testů můžete také filtrovat porovnáním řetězců s vlastnostmi testu.

### <a name="group-tests-in-the-test-list"></a>Seskupení testů v seznamu testů

::: moniker range="vs-2017"
Pokud chcete změnit způsob uspořádání testů, zvolte šipku dolů vedle tlačítka Seskupit podle Tlačítko skupiny Průzkumník testů a vyberte nová  ![ ](../test/media/ute_groupby_btn.png) kritéria seskupení.

![Seskupení testů podle kategorie v Průzkumníku testů](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Průzkumník testů umožňuje seskupit testy do hierarchie. Výchozí seskupení hierarchií je **Projekt,** **Obor názvů** a **třída**. Pokud chcete změnit způsob uspořádání testů, zvolte tlačítko Seskupit podle Skupina Průzkumníka testů a vyberte nová  ![ ](../test/media/ute_groupby_btn.png) kritéria seskupení.

![Seskupení testů podle kategorie v Průzkumníku testů](../test/media/vs-2019/test-explorer-groupby-162.png)

Můžete definovat vlastní úrovně hierarchie a seskupit podle **State** a pak třída, například výběrem možnosti Seskupit podle v upřednostňovaném pořadí. 

![Snímek obrazovky Visual Studio s hierarchií testů v jednom podokně a s nabídkou Seskupit podle v druhém s zaškrtnutou možností Třída a Stav](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Skupiny Průzkumníka testů

::: moniker range="vs-2017"
|Skupina|Popis|
|-|-----------------|
|**Doba trvání**|Seskupuje test podle doby **provádění: Rychlá,** **Střední** a **Pomalá.**|
|**Výsledek**|Seskupí testy podle výsledků spuštění: **Neúspěšné testy,** **Přeskočené testy,** **Úspěšně prošly testy.**|
|**Vlastnosti**|Seskupí test podle párů kategorií a hodnot, které definujete. Syntaxe pro určení kategorií vlastností a hodnot je definována architekturou testování částí.|
|**Projekt**|Skupiny testuje podle názvu projektů.|
::: moniker-end
::: moniker range=">=vs-2019"
|Skupina|Popis|
|-|-----------------|
|**Doba trvání**|Seskupí testy podle doby spuštění: **rychlá**, **střední** a **pomalá**.|
|**Stav**|Seskupí testy podle výsledků spuštění: **neúspěšné testy**, **vynechané testy**, **Úspěšné testy**, **Nespuštěné** .|
|**Cílová architektura** | Seskupí testy podle cíle v rámci svých projektů. |
|**Obor názvů**|Seskupí testy podle obsahujícího oboru názvů.|
|**Projekt**|Seskupí testy podle obsahujícího projektu.|
|**Třída**|Seskupí testy pomocí obsahující třídy.|
::: moniker-end

### <a name="traits"></a>Traits

Vlastnost je obvykle dvojice název/hodnota kategorie, ale může to být také jedna kategorie. Vlastnostem lze přiřadit metody, které jsou identifikovány jako testovací metoda v rámci jednotkového testu. Rozhraní testování částí může definovat kategorie vlastností. Přidáním hodnot do kategorií vlastností můžete definovat vlastní páry název-hodnota kategorie. Syntaxe pro určení kategorií vlastností a hodnot je definována v rámci testovacího rozhraní jednotky.

**Vlastnosti v rozhraní testování částí společnosti Microsoft pro spravovaný kód**

V rozhraní Microsoft pro testování částí pro spravované aplikace definujete v atributu dvojici název/hodnota vlastnosti  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . Testovací rozhraní obsahuje také tyto předdefinované vlastnosti:

|Znak|Description|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategorie vlastník je definována v rámci testovacího rozhraní jednotky a vyžaduje zadání řetězcové hodnoty vlastníka.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategorie priority je definována v rámci testovacího rozhraní jednotky a vyžaduje, abyste zadali celočíselnou hodnotu priority.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atribut TestCategory umožňuje určit kategorii testu jednotek.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atribut TestProperty umožňuje definovat vlastnost páru kategorie/hodnota.|


**Vlastnosti v rozhraní Microsoft Unit Testing Framework pro C++**

Viz [Jak používat Microsoft Unit Testing Framework pro C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Vytváření vlastních seznamů testů

::: moniker range="vs-2017"
Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam testů, testy v seznamu se zobrazí v Průzkumníku testů. Test můžete přidat do více než jednoho seznamu skladeb a všechny testy v projektu jsou k dispozici, když vyberete výchozí seznam **testů pro všechny testy** .

![Zvolit seznam testů](../test/media/ute_playlist.png)

**Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v Průzkumníku testů. V nabídce kliknutím pravým tlačítkem myši vyberte možnost **Přidat do seznamu**  >  **NewPlaylist**. Uložte soubor s názvem a umístěním, které zadáte v dialogovém okně **vytvořit nový seznam** testů.

**Chcete-li přidat testy do seznamu stop**, vyberte jeden nebo více testů v Průzkumníku testů. V nabídce klepněte pravým tlačítkem myši na položku **Přidat do seznamu stop** a zvolte seznam testů, do kterého chcete přidat testy.

**Chcete-li otevřít seznam stop**, zvolte možnost **test** > **seznamu** testů v nabídce aplikace Visual Studio a buď zvolte ze seznamu naposledy použitých seznamů stop, nebo zvolte možnost **otevřít seznam stop** a zadejte název a umístění seznamu skladeb.

Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![Snímek obrazovky s přepínačem paralelního spuštění testu na panelu nástrojů Visual Studio Test Explorer.](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.
::: moniker-end
::: moniker range=">=vs-2019"
Můžete vytvořit a uložit seznam testů, které chcete spustit nebo zobrazit jako skupinu. Když vyberete seznam testů, testy v seznamu se zobrazí na nové kartě Průzkumník testů. Test můžete přidat do více než jednoho seznamu skladeb.

**Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v Průzkumníku testů. V nabídce kliknutím pravým tlačítkem myši vyberte možnost **Přidat do seznamu skladeb**  >  **Nový seznam**.

![Vytvořit seznam testů](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Seznam se otevře na nové kartě Průzkumník testů. Tento seznam je možné použít jednou a pak ho zahodit, nebo můžete kliknout na tlačítko **Uložit** na panelu nástrojů v okně seznamu stop a pak vybrat název a umístění pro uložení seznamu.

![Seznam testů se otevře na samostatné kartě Průzkumníka testů.](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**Chcete-li vytvořit seznam stop**, vyberte jeden nebo více testů v Průzkumníku testů. Klikněte pravým tlačítkem a vyberte **Přidat do seznamu** testů  >  **Nový seznam** testů.

**Chcete-li otevřít seznam** testů, zvolte ikonu seznamu stop na panelu nástrojů sady Visual Studio a v nabídce vyberte dříve uložený soubor seznamu testů.

Pokud **chcete upravit seznam stop**, můžete kliknout pravým tlačítkem na libovolný test a pomocí možností nabídky ho přidat nebo odebrat ze seznamu testů.

Počínaje verzí Visual Studio 2019 verze 16,7 můžete zvolit tlačítko **Upravit** na panelu nástrojů. Zaškrtávací políčka se zobrazí vedle testů, které ukazují, jaké testy jsou zahrnuty a vyloučeny v seznamu. Teď skupiny upravte podle potřeby.

![Tlačítko Upravit seznam skladeb](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

Můžete také zaškrtnout nebo zrušit kontrolu polí nadřazených skupin v hierarchii. Tato akce vytvoří dynamický seznam testů, který vždy aktualizuje seznam stop na základě testů, které jsou v dané skupině. Například pokud umístíte značku zaškrtnutí vedle třídy, všechny testy přidané z této třídy se stávají součástí tohoto seznamu testů. Pokud odstraníte test z této třídy, je odebrán ze seznamu. Další informace o pravidlech najdete tak, že seznam stop uložíte na panelu nástrojů na tlačítko Uložit a otevřete soubor *. playlist* , který je vytvořený na disku. Tento soubor obsahuje seznam všech pravidel a jednotlivých testů, které tvoří seznam testů.

![Soubor XML se seznamem testů](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

Pokud chcete vytvořit seznam testů pro vlastnosti, použijte následující formát pro MSTest.
```xml
<Playlist Version="2.0">
    <Rule Name="Includes" Match="Any">
        <Property Name="Trait" Value="SchemaUpdateBasic" />
    </Rule>
</Playlist>
```

Pro xUnit použijte následující formát. Ujistěte se, že mezi vaším `TestCategory` jménem a příponou je mezera `[Value]` .
```xml
<Playlist Version="2.0">
  <Rule Name="Includes" Match="Any">
    <Rule Match="All">
      <Property Name="Solution" />
        <Rule Match="Any">
            <Property Name="Trait" Value="TestCategory [Value]" />
        </Rule>
    </Rule>
  </Rule>
</Playlist>
```

::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Sloupce Průzkumníka testů

[Skupiny](#test-explorer-groups) jsou také k dispozici jako sloupce v Průzkumníku testů, spolu se vlastnostmi, trasováním zásobníku, chybovou zprávou a plně kvalifikovaným názvem. Většina sloupců není ve výchozím nastavení viditelná a můžete přizpůsobit zobrazené sloupce a pořadí, ve kterém se zobrazí.

![Snímek obrazovky Průzkumníka testů sady Visual Studio zobrazující nabídku se zvolenými sloupci a podnabídku se zvolenou dobou trvání, vlastností a chybové zprávy.](../test/media/vs-2019/test-explorer-columns-16-2.png)

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
|Kvalifikátor|Description|
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
|Kvalifikátor|Description|
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

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>Test zvukové hromádky
Průzkumník testů může přehrát zvuk při dokončení testovacího běhu. Existují dva zvuky: jeden zvuk pro indikaci, že testovací běh byl úspěšný, a druhý zvuk k indikaci, že testovací běh byl dokončen s alespoň jedním neúspěšným testem. Tyto zvuky můžete nastavit v dialogovém okně výchozí zvuk Windows 10. Tato funkce je k dispozici počínaje verzí Visual Studio 2019 Update 16,9 Preview 3.

1. Otevřete výchozí dialogové okno zvuk systému Windows 10.
2. Přejděte na kartu **zvuky** .
3. Najděte kategorii **Microsoft Visual Studio** . Zvolte, že **testovací běh byl úspěšný** nebo že **testovací běh neuspěl** pro výběr přednastavených zvuků nebo procházení na vlastní zvukový soubor.  
![Dialogové okno zvuk Windows 10](../test/media/default-windows-10-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Ladění testů částí pomocí Průzkumníka testů](../test/debug-unit-tests-with-test-explorer.md)
- [Spuštění testování částí v podobě 64bitového procesu](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Průzkumník testů – nejčastější dotazy](test-explorer-faq.md)
