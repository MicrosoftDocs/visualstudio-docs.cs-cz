---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 1e1a0ec1fd6f2fbdf4f016b1d22db5a6929b5e24
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75851434"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Jak konfigurovat a používat živé testování částí

Při vývoji aplikace živé testování částí automaticky spustí všechny ovlivněné testy částí na pozadí a zobrazí výsledky a pokrytí kódu v reálném čase. Při úpravě kódu poskytuje živé testování částí zpětnou vazbu o tom, jak vaše změny ovlivnily existující testy a zda je nový kód, který jste přidali, pokryt jedním nebo více existujícími testy. To jemně připomíná, abyste při provádění oprav chyb nebo přidávání nových funkcí psali testy částí.

> [!NOTE]
> Živé testování částí je k dispozici pro projekty jazyka C# a Visual Basic, které cílí na rozhraní .NET Core nebo .NET Framework v edici Enterprise sady Visual Studio.

Při použití live testování částí pro vaše testy, uchovává data o stavu testů. Použití trvalých dat umožňuje live testování částí nabídnout vynikající výkon při dynamickém spuštění testů v reakci na změny kódu.

## <a name="supported-test-frameworks"></a>Podporované testovací architektury

Živé testování částí pracuje se třemi oblíbenými rozhraními pro testování částí uvedenými v následující tabulce. Minimální podporovaná verze jejich adaptérů a rámců je také zobrazena. Testování částí rámce jsou k dispozici od NuGet.org.

|Testovací rámec  |Minimální verze adaptéru Visual Studio  |Minimální verze rozhraní Framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio verze 2.2.0-beta3-build1187 |xjednotka 1,9,2 |
|NJednotka |NUnit3TestAdaptér verze 3.5.1 |NUnit verze 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Pokud máte starší testovací projekty založené na MSTest, které odkazují na Microsoft.VisualStudio.QualityTools.UnitTestFramework a nechcete přejít na novější balíčky MSTest NuGet, upgradujte na Visual Studio 2019 nebo Visual Studio 2017.

V některých případech budete muset explicitně obnovit balíčky NuGet odkazuje projektu, aby pro živé testování částí fungovat. Můžete to provést buď provedením explicitní sestavení řešení (vyberte **sestavení** > **znovu sestavit řešení** z nabídky visual studio nejvyšší úrovně) nebo obnovením balíčků v řešení (klikněte pravým tlačítkem myši na řešení a vyberte obnovit **nuget balíčky).**

## <a name="configure"></a>Konfigurace

Nakonfigurujte živé testování částí výběrem**možností** **nástrojů** > z panelu nabídek aplikace Visual Studio nejvyšší úrovně a výběrem **živého testování částí** v levém podokně dialogového okna **Možnosti.**

> [!TIP]
> Po povolení testování živých částí (viz další část [Start, pozastavit a zastavit testování živých částí](#start-pause-and-stop)) můžete také otevřít dialogové okno **Možnosti** výběrem**možnosti** **testování** > **živé jednotky** > .

Následující obrázek znázorňuje možnosti konfigurace testování živých částí, které jsou k dispozici v dialogovém okně:

![Možnosti konfigurace testování živých částí](./media/lut-options.png)

Konfigurovatelné možnosti zahrnují:

- Zda live testování částí pozastaví při vytvoření řešení a odlazení.

- Zda se testování živých částí pozastaví, když napájení systému baterie klesne pod zadanou prahovou hodnotu.

- Zda je při otevření řešení automaticky spuštěno živé testování částí.

- Určuje, zda má být povolen symbol ladění a generování komentářů dokumentace XML.

- Adresář, do kterého chcete uložit trvalá data.

- Možnost odstranit všechna trvalá data. To je užitečné, když živé testování částí se chová nepředvídatelným nebo neočekávaným způsobem, což naznačuje, že došlo k poškození trvalých dat.

- Interval, po kterém časový interval testovacího případu out. Výchozí hodnota je 30 sekund.

- Maximální počet testovacích procesů, které vytvoří testování živé části.

- Maximální množství paměti, které mohou spotřebovat procesy testování živých částí.

- Úroveň informací zapsaných do okna **Výstup** živého testování částí.

   Možnosti zahrnují žádné protokolování (**Žádné**), pouze chybové zprávy (**Chyba**), chybové a informační zprávy (**Info**, výchozí), nebo všechny detaily (**Verbose**).

   Můžete také zobrazit podrobný výstup v okně **Výstup** živétestování částí přiřazením hodnoty "1" proměnné `VS_UTE_DIAGNOSTICS`prostředí na úrovni uživatele s názvem a restartováním sady Visual Studio.

   Chcete-li zachytit podrobné zprávy protokolu MSBuild z `LiveUnitTesting_BuildLog` testování živých částí v souboru, nastavte proměnnou prostředí na úrovni uživatele na název souboru tak, aby protokol obsahoval.

## <a name="start-pause-and-stop"></a>Spuštění, pozastavení a zastavení

Chcete-li povolit živé testování částí, vyberte **test** > **spuštění testování** > živých částí**z** nabídky Visual Studio nejvyšší úrovně. Je-li povoleno testování živých částí, možnosti dostupné v nabídce **Testování živých částí** se změní z jedné položky **Start**, **na Pozastavit** a **zastavit**:

- **Pozastavit** dočasné pozastavení testování živých částí.

  Při pozastavení živétestování částí, vizualizace pokrytí se nezobrazí v editoru, ale všechna data, která byla shromážděna je zachována. Chcete-li pokračovat v testování živých částí, vyberte **pokračovat** v nabídce Testování živých částí. Živé testování částí provádí nezbytnou práci, aby dohnalo všechny úpravy, které byly provedeny v době, kdy byly pozastaveny, a odpovídajícím způsobem aktualizuje glyfy.

- **Zastavte** úplně zastaví živé testování částí. Živé testování částí zahodí všechna data, která shromáždila.

> [!NOTE]
> Pokud spustíte živé testování částí v řešení, které neobsahuje projekt testování částí, zobrazí se možnosti **Pozastavit** a **Zastavit** v nabídce **Testování živých částí,** ale živé testování částí se nespustí. Okno **Výstup** zobrazí zprávu, která začíná " Žádné podporované testovací adaptéry jsou odkazovány tímto řešením ...".

Kdykoli můžete dočasně pozastavit nebo zcela zastavit živé testování částí. Můžete to udělat, například pokud jste uprostřed refaktoringu a víte, že vaše testy budou na chvíli přerušeny.

## <a name="view-coverage-visualization"></a>Zobrazit vizualizaci disponibility

Po jeho povolení živé testování částí aktualizuje každý řádek kódu v editoru Sady Visual Studio, aby vám ukázal, zda je kód, který píšete, pokryt testy částí a zda testy, které jej pokrývají, předají. Následující obrázek znázorňuje řádky kódu s předávání mandatismu i selhává testy, stejně jako řádky kódu, které nejsou zahrnuty testy. Řádky zdobené zeleným "✓" jsou pokryty pouze absolvováním zkoušek, řádky zdobené červeným "x" jsou pokryty jedním nebo více testy selhání a řádky zdobené modrou "➖" nejsou pokryty žádným testem.

![Pokrytí kódu v sadě Visual Studio](./media/lut-codewindow.png)

Live Testování částí pokrytí vizualizace je aktualizován okamžitě při úpravě kódu v editoru kódu. Při zpracování úprav se vizualizace změní tak, že data nejsou aktuální přidáním obrázku kruhového časovače pod symboly předávání, selhání a nezahrnuté symboly, jak ukazuje následující obrázek.

![Pokrytí kódu v sadě Visual Studio s ikonou časovače](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Získání informací o stavu testu

Najetím na symbol úspěšné nebo neúspěšné v okně kódu můžete vidět, kolik testů je zasaženo na tento řádek. Chcete-li zobrazit stav jednotlivých testů, vyberte symbol:

![Test stavu symbolu v sadě Visual Studio](./media/lut-failedinfo.png)

Kromě poskytnutí názvů a výsledků testů umožňuje popisek znovu spustit nebo ladit sadu testů. Pokud vyberete jeden nebo více testů v popisku, můžete také spustit nebo ladit pouze tyto testy. To umožňuje ladit testy bez nutnosti opustit okno kódu. Při ladění, kromě pozorování všech zarážek, které jste již nastavili, program spuštění pozastaví, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> když ladicí program spustí metodu, která vrací neočekávaný výsledek.

Když v popisku najedete na místo neúspěšného testu, rozbalí se a poskytne další informace o chybě, jak je znázorněno na následujícím obrázku. Chcete-li přejít přímo na neúspěšný test, poklepejte na něj v popisku.

![Informace v popisku testu se nezdařilo v sadě Visual Studio](./media/lut-failedmsg.png)

Při přechodu na neúspěšný test živé testování částí vizuálně označuje v podpisu metody testy, které mají:

- (označeno poloúplnou kádinkou spolu se zeleným "✓")
- selhal (poloúplná kádinka spolu🞩s červenou " ")
- nejsou zapojeny do živého testování částí (poloúplná kádinka spolu s modrým "➖")

Netestovací metody nejsou zdobeny symbolem. Následující obrázek znázorňuje všechny čtyři typy metod.

![Testovací metody v sadě Visual Studio se symbolem vyhovění nebo selhání](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostika a oprava selhání testu

Z neúspěšného testu můžete snadno ladit kód produktu, provádět úpravy a pokračovat ve vývoji aplikace. Vzhledem k tomu, že živé testování částí běží na pozadí, není nutné zastavit a restartovat živé testování částí během ladění, úprav a pokračovat v cyklu.

Například selhání testu zobrazené v předchozím obrázku bylo způsobeno nesprávným předpokladem v `true` testovací metodě, že neabecední znaky vrátit při předání metodě. <xref:System.Char.IsLower%2A?displayProperty=fullName> Po opravě zkušební metody by měly projít všechny testy. Není třeba pozastavit nebo zastavit živé testování částí.

## <a name="test-explorer"></a>Průzkumník testů

**Průzkumník testů** poskytuje rozhraní, které umožňuje spouštět a ladit testy a analyzovat výsledky testů. Živé testování částí se integruje s **Průzkumníkem testů**. Pokud testování živých částí není povoleno nebo je zastaveno, **Průzkumník testů** zobrazí stav testů částí při posledním spuštění testu. Změny zdrojového kódu vyžadují opětovné spuštění testů. Naopak při aktivnítestování částí je povolena, stav testování částí v **Průzkumníku testů** je aktualizován okamžitě. Není nutné explicitně spustit testy částí.

> [!TIP]
> Sem **Průzkumníka testů** otevřete výběrem **možnosti Testovat** > **Průzkumníka testů** **systému Windows** > z nabídky Visual Studio nejvyšší úrovně.

Můžete si všimnout v okně **Průzkumníka testů,** že některé testy jsou vybledlé. Například když povolíte live testování částí po otevření dříve uloženého projektu, okno **Průzkumníktestů** vybledlo všechny, ale neúspěšný test, jak ukazuje následující obrázek. V tomto případě live testování částí má znovu spustit neúspěšný test, ale neznovu spustit úspěšné testy. Důvodem je, že živé testování částí trvalá data označuje, že nebyly žádné změny od testování byly naposledy úspěšně spuštěny.

![Neúspěšný test v Průzkumníku testů](media/lut-test-explorer.png)

Všechny testy, které se zobrazí jako vybledlé, můžete znovu spustit výběrem možností **Spustit vše** nebo **Spustit** z nabídky **Průzkumník testů.** Nebo vyberte jeden nebo více testů v nabídce **Průzkumník testů,** klikněte pravým tlačítkem myši a pak z místní nabídky vyberte **Spustit vybrané testy** nebo Ladit vybrané **testy.** Jak testy jsou spuštěny, oni bubliny nahoru.

Existují určité rozdíly mezi live testování částí automaticky spuštěna aktualizace výsledků testů a explicitně spuštěny testy z **Průzkumníka testů**. Tyto rozdíly zahrnují:

- Spuštění nebo ladění testů z okna Průzkumníka testů spouští pravidelné binární soubory, zatímco živé testování částí spouští instrumentované binární soubory.
- Živé testování částí nevytváří novou doménu aplikace pro spuštění testů, ale spíše spustí testy z výchozí domény. Testy spuštěné z okna **Průzkumníka testů** vytvářejí novou doménu aplikace.
- Testování živých částí spustí testy v každé testovací sestavení postupně. V okně **Průzkumník testů** můžete spustit více testů paralelně.

## <a name="large-solutions"></a>Velká řešení

Pokud vaše řešení obsahuje 10 nebo více projektů, Visual Studio zobrazí následující dialogové okno, když:

- spustit živé testování částí a nejsou k dispozici žádná trvalá data
- vybrat **možnosti možnosti** > **Options** > **živé testování částí odstranit** > **trvalá data**

![Dialogové okno Živé testování částí pro velké projekty](media/lut-large-project.png)

Dialogové okno vás upozorní, že dynamické provádění velkého počtu testů ve velkých projektech může vážně ovlivnit výkon. Pokud vyberete **OK**, live testování částí provede všechny testy v řešení. Pokud vyberete **Zrušit**, můžete vybrat testy, které chcete provést. V následující části je vysvětleno, jak to provést.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Zahrnout a vyloučit testovací projekty a zkušební metody

U řešení s mnoha testovacími projekty můžete řídit, které projekty a jednotlivé metody v projektu se účastní živého testování částí. Například pokud máte řešení se stovkami testovacích projektů, můžete vybrat cílovou sadu testovacích projektů k účasti na živé testování částí. Existuje několik způsobů, jak to provést, v závislosti na tom, zda chcete vyloučit všechny testy v projektu nebo řešení, zahrnout nebo vyloučit většinu testů nebo vyloučit jednotlivé testy. Živé testování částí ukládá zahrnout nebo vyloučit stav jako uživatelské nastavení a pamatuje si to, když je řešení uzavřeno a znovu otevřeno.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Vyloučit všechny testy v projektu nebo řešení

Chcete-li vybrat jednotlivé projekty v jednotkových testech, postupujte po spuštění testování živých částí:

1. Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a zvolte **živé testy** > **vyloučit** vyloučit celé řešení.
1. Klikněte pravým tlačítkem myši na každý testovací projekt, který chcete zahrnout do testů, a zvolte **živé testy** > **zahrnout**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Vyloučit jednotlivé testy z okna editoru kódu

Okno editoru kódu můžete použít k zahrnutí nebo vyloučení jednotlivých testovacích metod. Klikněte pravým tlačítkem myši na podpis testovací metody v okně editoru kódu a vyberte jednu z následujících možností:

- **Živé testy** > **zahrnují \<vybranou metodu>**
- **Živé testy** > **Vylučují \<vybranou metodu>**
- **Živé testy** > **vyložit všechny, ale \<vybrané metody>**

### <a name="exclude-tests-programmatically"></a>Programově vyloučit testy

<xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> Atribut můžete použít programově vyloučit metody, třídy nebo struktury z vykazování jejich pokrytí v testování živých částí.

Pomocí následujících atributů vylučte jednotlivé metody z testování živých částí:

- Pro xUnit:`[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit:`[Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest:`[TestCategory("SkipWhenLiveUnitTesting")]`

Následující atributy vylučte celou sestavu testů z testování živých částí:

- Pro xUnit:`[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit:`[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest:`[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Viz také

- [Nástroje pro testování kódu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog o testování živých částí](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Nejčastější dotazy k funkci Live Unit Testing](live-unit-testing-faq.md)
- [Video kanálu 9: Živé testování částí v sadě Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
