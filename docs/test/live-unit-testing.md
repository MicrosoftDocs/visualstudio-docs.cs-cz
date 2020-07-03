---
title: Live Unit Testing
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 185d722f65dce0062dc58a06a05590aacb68138b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906220"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Konfigurace a použití Live Unit Testing

Při vývoji aplikace Live Unit Testing automaticky spouští všechny ovlivněné testy jednotek na pozadí a prezentuje výsledky a pokrytí kódu v reálném čase. Při úpravách kódu Live Unit Testing poskytuje zpětnou vazbu o tom, jak změny ovlivnily existující testy a zda se nový kód, který jste přidali, zabývá jedním nebo více existujícími testy. Tím se jemně dohlížíte na zápis testů jednotek, když provádíte opravy chyb nebo přidáváte nové funkce.

> [!NOTE]
> Live Unit Testing je k dispozici pro projekty C# a Visual Basic, které cílí na .NET Core nebo .NET Framework v edici Enterprise sady Visual Studio.

Při použití Live Unit Testing pro testy, uchovává data o stavu testů. Použití trvalých dat umožňuje Live Unit Testing nabízet špičkový výkon při spouštění testů dynamicky v reakci na změny kódu.

## <a name="supported-test-frameworks"></a>Podporovaná testovací rozhraní

Live Unit Testing pracuje se třemi oblíbenými platformami testování částí uvedenými v následující tabulce. Zobrazuje se taky minimální podporovaná verze jejich adaptérů a platforem. Rozhraní pro testování částí jsou dostupná z NuGet.org.

|Testovací rozhraní  |Minimální verze adaptéru sady Visual Studio  |Minimální verze architektury  |
|---------|---------|---------|
|xUnit.net |xUnit. Runner. VisualStudio verze 2.2.0-beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter verze 3.5.1 |NUnit verze 3.5.0 |
|MSTest |MSTest. TestAdapter 1.1.4 – Preview |MSTest. TestFramework 1.0.5 – Preview |

Pokud máte starší testovací projekty založené na MSTest, které odkazují na Microsoft. VisualStudio. QualityTools. UnitTestFramework, a nechcete přejít na novější balíčky NuGet MSTest, upgradujte na Visual Studio 2019 nebo Visual Studio 2017.

V některých případech může být nutné explicitně obnovit balíčky NuGet, na které odkazuje projekt, aby mohla Live Unit Testing fungovat. To můžete provést buď explicitním sestavením řešení (vyberte řešení **sestavení znovu**  >  **sestavit** z nabídky nejvyšší úrovně), nebo obnovením balíčků v řešení (klikněte pravým tlačítkem na řešení a vyberte **obnovit balíčky NuGet**).

## <a name="configure"></a>Konfigurace

Nakonfigurujte Live Unit Testing tak, **Tools**že vyberete  >  **Možnosti** nástrojů na panelu nabídek nejvyšší úrovně a pak v levém podokně dialogového okna **Možnosti** vyberete **Live Unit Testing** .

> [!TIP]
> Po povolení Live Unit Testing (viz další část, [spuštění, pozastavení a zastavení Live Unit Testing](#start-pause-and-stop)) můžete také otevřít dialogové okno **Možnosti** výběrem možnosti **test**  >  **Live Unit Testing**  >  **Options**.

Následující obrázek ukazuje možnosti konfigurace Live Unit Testing, které jsou k dispozici v dialogovém okně:

![Možnosti konfigurace Live Unit Testing](./media/lut-options.png)

Mezi konfigurovatelné možnosti patří:

- Určuje, zda se při sestavení a ladění řešení Live Unit Testing pozastaví.

- Určuje, jestli se Live Unit Testing pozastaví, když baterie energie systému klesne pod zadanou prahovou hodnotu.

- Určuje, zda se při otevření řešení automaticky spustí Live Unit Testing.

- Určuje, zda má být povoleno generování komentáře k symbolům ladění a dokumentaci XML.

- Adresář, do kterého se mají ukládat trvalá data

- Možnost odstraňovat všechna trvalá data. To je užitečné, když se Live Unit Testing chová v nepředvídatelném nebo neočekávaném způsobu, což naznačuje, že trvalá data jsou poškozena.

- Interval, po kterém vypršel časový limit testovacího případu. Výchozí hodnota je 30 sekund.

- Maximální počet testovacích procesů, které Live Unit Testing vytvořit.

- Maximální velikost paměti, kterou mohou Live Unit Testing procesy spotřebovat.

- Úroveň informací zapsaných do okna **výstup** Live Unit Testing.

   Mezi možnosti patří žádné protokolování (**žádné**), pouze chybové zprávy (**Chyba**), chybové a informativní zprávy (**informace**, výchozí nastavení) nebo všechny podrobnosti (**podrobné**).

   Můžete také zobrazit podrobný výstup v okně Live Unit Testing **výstup** přiřazením hodnoty "1" k proměnné prostředí na úrovni uživatele s názvem `VS_UTE_DIAGNOSTICS` a následným restartováním sady Visual Studio.

   Chcete-li zachytit podrobné zprávy protokolu nástroje MSBuild z Live Unit Testing v souboru, nastavte `LiveUnitTesting_BuildLog` proměnnou prostředí na úrovni uživatele na název souboru, který bude obsahovat protokol.

## <a name="start-pause-and-stop"></a>Spuštění, pozastavení a zastavení

Pokud chcete povolit Live Unit Testing, vyberte **test**  >  **Live Unit Testing**  >  **Spustit** z nabídky Visual Studio nejvyšší úrovně. Když je povolený Live Unit Testing, možnosti dostupné v nabídce **Live Unit Testing** se změní z jedné položky, **Start**, na **pozastavit** a **zastavit**:

- **Pozastavení** dočasně pozastaví Live Unit Testing.

  Když je Live Unit Testing pozastavit, vizualizace pokrytí se v editoru nezobrazí, ale všechna shromážděná data se zachovají. Chcete-li obnovit Live Unit Testing, vyberte možnost **pokračovat** v nabídce Live Unit Testing. Live Unit Testing provádí potřebnou práci pro zachycení všech úprav, které byly provedeny v době, kdy byla pozastavena, a odpovídajícím způsobem aktualizuje glyfy.

- **Zastavení** Live Unit Testing zcela zastaví. Live Unit Testing zahodí všechna data, která shromáždila.

> [!NOTE]
> Pokud začnete Live Unit Testing v řešení, které neobsahuje projekt testování částí, možnosti **pozastavit** a **zastavit** se zobrazí v nabídce **Live Unit Testing** , ale Live Unit Testing nespustí. V okně **výstup** se zobrazí zpráva, která začíná. Toto řešení neodkazuje na žádné podporované adaptéry testů...

Kdykoli můžete Live Unit Testing dočasně pozastavit nebo úplně zastavit. To může být vhodné například v případě, že jste uprostřed refaktoringu a víte, že testy budou v průběhu chvilky přerušeny.

## <a name="view-coverage-visualization"></a>Zobrazit vizualizaci pokrytí

Po povolení Live Unit Testing aktualizuje jednotlivé řádky kódu v editoru sady Visual Studio, aby se zobrazila informace o tom, zda se kód, který píšete, zabývá testy jednotek a zda jsou testy, které se na něj vztahují, přecházejí. Následující obrázek ukazuje řádky kódu s předáváním i neúspěšnými testy, jakož i řádky kódu, které nejsou pokryty testy. Řádky dekorované zelenou "✓" jsou pokryty pouze předáním testů, řádky dekorované červeným symbolem "x" jsou pokryty jedním nebo více neúspěšnými testy a řádky dekorované modrou "➖" nejsou předmětem žádného testu.

![Pokrytí kódu v aplikaci Visual Studio](./media/lut-codewindow.png)

Vizualizace pokrytí Live Unit Testing je okamžitě aktualizována při úpravě kódu v editoru kódu. Při zpracování úprav se změny vizualizace, které označují, že data nejsou aktuální, přidáním obrázku kulatého časovače pod průchozí, neúspěšné a nezahrnuté symboly, jak ukazuje následující obrázek.

![Pokrytí kódu v aplikaci Visual Studio s ikonou časovače](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Získat informace o stavu testu

Najeďte myší na symbol úspěšný nebo neúspěšný v okně Code (kód), kde vidíte, kolik testů se na daný řádek zasáhne. Chcete-li zobrazit stav jednotlivých testů, vyberte symbol:

![Stav testu pro symbol v aplikaci Visual Studio](./media/lut-failedinfo.png)

Kromě poskytování názvů a výsledků testů vám popisek umožňuje znovu spustit nebo ladit sadu testů. Pokud vyberete jeden nebo více testů v popisku, můžete také spustit nebo ladit pouze ty testy. To vám umožní ladit testy bez nutnosti opustit okno kódu. Při ladění, kromě pozorování všech zarážek, které jste již pravděpodobně nastavili, se spuštění programu pozastaví, když ladicí program spustí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu, která vrátí neočekávaný výsledek.

Když najedete myší na neúspěšný test v popisu tlačítka, rozbalí se, aby se poskytly další informace o selhání, jak je znázorněno na následujícím obrázku. Pokud chcete přejít přímo k neúspěšnému testu, poklikejte na něj v popisku.

![Neúspěšné informace popisu tlačítka testu v aplikaci Visual Studio](./media/lut-failedmsg.png)

Když přejdete na neúspěšný test, Live Unit Testing vizuálně indikuje v podpisu metody testy, které mají:

- předáno (označeno poloviční plnou kádinkou a zelenou "✓")
- neúspěšné (poloviční plná kádinka s červeným symbolem " 🞩 ")
- nejsou zapojené do Live Unit Testing (poloviční plná kádinka spolu s modrou "➖").

Netestové metody nejsou upraveny symbolem. Následující obrázek znázorňuje všechny čtyři typy metod.

![Testovací metody v aplikaci Visual Studio se symbolem Pass nebo neúspěchu](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostika a oprava selhání testu

Z neúspěšného testu můžete snadno ladit kód produktu, provádět úpravy a pokračovat ve vývoji aplikace. Vzhledem k tomu, že Live Unit Testing běží na pozadí, není nutné zastavit a restartovat Live Unit Testing během cyklu ladění, úprav a pokračování.

Například selhání testu zobrazené na předchozím obrázku bylo způsobeno nesprávným předpokladem v testovací metodě, kterou vrátí neabecední znaky, `true` Pokud jsou předány <xref:System.Char.IsLower%2A?displayProperty=fullName> metodě. Po opravě testovací metody by měly projít všechny testy. Nemusíte pozastavit ani zastavit Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Průzkumník testů

**Průzkumník testů** poskytuje rozhraní, které umožňuje spouštět a ladit testy a analyzovat výsledky testů. Live Unit Testing se integruje s **průzkumníkem testů**. Pokud Live Unit Testing není povolen nebo je zastaven, **Průzkumník testů** zobrazí stav testů testování při posledním spuštění testu. Změny zdrojového kódu vyžadují, abyste znovu znovu provedli testy. Naproti tomu, pokud je povolena Live Unit Testing, se stav testů jednotek v **Průzkumníku testů** okamžitě aktualizuje. Nemusíte explicitně spouštět testy jednotek.

> [!TIP]
> Otevřete **Live Unit Testing** tím, **Test**že  >  **Windows**  >  v nabídce aplikace Visual Studio nejvyšší úrovně vyberete test Windows**Test Explorer** .

V okně **Průzkumník testů** si můžete všimnout, že některé testy jsou vybledlé. Pokud například povolíte Live Unit Testing po otevření dříve uloženého projektu, okno **Průzkumník testů** vynechalo vše, ale neúspěšný test, jak ukazuje následující obrázek. V tomto případě Live Unit Testing znovu spustit neúspěšný test, ale nespustí úspěšné testy znovu. Důvodem je to, že trvalá data Live Unit Testing znamenají, že se od posledního spuštění testů nezměnily žádné změny.

![Neúspěšný test v Průzkumníku testů](media/lut-test-explorer.png)

Můžete znovu spustit všechny testy, které se projeví na zvolna, a to výběrem možnosti **Spustit vše** nebo **Spustit** z nabídky **Průzkumník testů** . Nebo vyberte jeden nebo více testů v nabídce **Průzkumník testů** , klikněte pravým tlačítkem myši a vyberte možnost **Spustit vybrané testy** nebo **ladit vybrané testy** z místní nabídky. Při spuštění testů se tyto testy dostanou nahoru.

Některé rozdíly mezi Live Unit Testing automaticky spouští a aktualizují výsledky testů a explicitně spouštějící testy z **Průzkumníka testů**. Mezi tyto rozdíly patří:

- Spuštění nebo ladění testů z okna Průzkumníka testů spouští běžné binární soubory, zatímco Live Unit Testing spouští instrumentované binární soubory.
- Live Unit Testing nevytváří novou doménu aplikace pro spuštění testů, ale místo toho spustí testy z výchozí domény. Testy spuštěné v okně **Průzkumníka testů** vytvoří novou doménu aplikace.
- Live Unit Testing spouští testy v každém testovacím sestavení sekvenčně. V okně **Průzkumník testů** můžete zvolit paralelní spuštění více testů.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing okno

**Live Unit Testing**, podobně jako **Průzkumník testů**, poskytuje rozhraní, které umožňuje spouštět a ladit testy a analyzovat výsledky testů. Když je povoleno Live Unit Testing, stav testů jednotek v **Průzkumníku testů** se okamžitě aktualizuje. Nemusíte explicitně spouštět testy jednotek. Pokud Live Unit Testing není povolen nebo je zastaven, **Live Unit Testing** zobrazí stav testů testování při posledním spuštění testu. Po restartování Live Unit Testing se pro opětovné spuštění testů vyžaduje změna zdrojového kódu.

> [!TIP]
> Začněte Live Unit Testing výběrem možnosti **test**  >  **Live Unit Testing**  >  **začít** v nabídce aplikace Visual Studio nejvyšší úrovně. Můžete také otevřít okno **Live Unit Testing** pomocí **zobrazení**  >  **jiných**  >  **oken Live Unit Testing**Windows.

V okně **Live Unit Testing** můžete všimnout, že některé testy jsou vybledlé. Například při zastavení a restartování Live Unit Testing **Live Unit Testing** okno vykreslí všechny testy, jak ukazuje následující obrázek. Výsledky nepatrného testu ukazují, že test nebyl součástí nejnovějšího běhu služby Live Unit Test. Testy se spustí pouze v případě, že je zjištěna změna testu nebo závislostí testu. Pokud nedojde ke změně, vyhnete se tak zbytečnému spuštění testu. V tomto případě je výsledek šedé testu stále "aktuální", i když nebyl součástí posledního spuštění.

![Vybledlé testy v Průzkumníku testů](media/vs-2019/lut-test-explorer.png)

Můžete znovu spustit všechny testy, které se projeví při změně kódu.

Některé rozdíly mezi Live Unit Testing automaticky spouští a aktualizují výsledky testů a explicitně spouštějící testy z **Průzkumníka testů**. Mezi tyto rozdíly patří:

- Spuštění nebo ladění testů z okna Průzkumníka testů spouští běžné binární soubory, zatímco Live Unit Testing spouští instrumentované binární soubory.
- Live Unit Testing nevytváří novou doménu aplikace pro spuštění testů, ale místo toho spustí testy z výchozí domény. Testy spuštěné v okně **Průzkumníka testů** vytvoří novou doménu aplikace.
- Live Unit Testing spouští testy v každém testovacím sestavení sekvenčně. V okně **Průzkumník testů** můžete zvolit paralelní spuštění více testů.
::: moniker-end

## <a name="large-solutions"></a>Velká řešení

Pokud má vaše řešení 10 nebo více projektů, Visual Studio zobrazí následující dialog, když:

- spustit Live Unit Testing a neexistují žádná trvalá data
- Vyberte **Tools**  >  **Možnosti**nástrojů  >  **Live Unit Testing**  >  **Odstranit trvalá data** .

![Dialog Live Unit Testing pro velké projekty](media/lut-large-project.png)

Dialog vás upozorní na to, že dynamické spuštění velkého počtu testů ve velkých projektech může mít vážně vliv na výkon. Pokud vyberete **OK**, Live Unit Testing spustí všechny testy v řešení. Vyberete-li možnost **Zrušit**, můžete vybrat testy, které mají být provedeny. V následující části se dozvíte, jak to provést.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Zahrnutí a vyloučení testovacích projektů a testovacích metod

Pro řešení s mnoha testovacími projekty můžete určit, které projekty a jednotlivé metody v projektu se účastní Live Unit Testing. Například pokud máte řešení se stovkami testovacích projektů, můžete vybrat cílovou sadu testovacích projektů, které se budou podílet na Live Unit Testing. To lze provést několika způsoby v závislosti na tom, zda chcete vyloučit všechny testy v projektu nebo řešení, zahrnout nebo vyloučit většinu testů nebo vyloučit jednotlivé testy. Live Unit Testing ukládá zahrnutí/vyloučení stavu jako uživatelské nastavení a pamatuje ho při zavření a opětovném otevření řešení.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Vyloučit všechny testy v projektu nebo řešení

Chcete-li vybrat jednotlivé projekty v testování částí, proveďte následující po spuštění Live Unit Testing:

1. Klikněte pravým tlačítkem na řešení v **Průzkumník řešení** a vyberte možnost **živé testy**  >  k**vyloučení** pro vyloučení celého řešení.
1. Klikněte pravým tlačítkem na každý projekt testů, který chcete zahrnout do testů, a vyberte možnost **živé testy**  >  **včetně**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Vyloučit jednotlivé testy z okna editoru kódu

Můžete použít okno editoru kódu k zahrnutí nebo vyloučení jednotlivých testovacích metod. Klikněte pravým tlačítkem na podpis testovací metody v okně editoru kódu a vyberte jednu z následujících možností:

- **Živé testy**  >  **Zahrnout \<selected method> **
- **Živé testy**  >  **Vyloučit \<selected method> **
- **Živé testy**  >  **Vyloučit všechny kromě \<selected method> **

### <a name="exclude-tests-programmatically"></a>Vyloučení testů prostřednictvím kódu programu

Atribut můžete použít <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> pro programové vyloučení metod, tříd nebo struktur z hlášení jejich pokrytí v Live Unit Testing.

Pomocí následujících atributů vylučte jednotlivé metody z Live Unit Testing:

- Pro xUnit:`[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit:`[Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest:`[TestCategory("SkipWhenLiveUnitTesting")]`

Pomocí následujících atributů vylučte celé sestavení testů z Live Unit Testing:

- Pro xUnit:`[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit:`[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest:`[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Viz také

- [Nástroje pro testování kódu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog Live Unit Testing](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Nejčastější dotazy k funkci Live Unit Testing](live-unit-testing-faq.md)
- [Video pro kanál 9: Live Unit Testing v aplikaci Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
