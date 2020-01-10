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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851434"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Konfigurace a použití Live Unit Testing

Při vývoji aplikace Live Unit Testing automaticky spouští všechny ovlivněné testy jednotek na pozadí a prezentuje výsledky a pokrytí kódu v reálném čase. Při úpravě kódu, na jaký vliv na existující testy změny Live Unit Testing poskytuje zpětnou vazbu a určuje, zda nový kód jste přidali se vztahuje na jeden nebo více existujících testů. Tím se jemně dohlížíte na zápis testů jednotek, když provádíte opravy chyb nebo přidáváte nové funkce.

> [!NOTE]
> Live Unit Testing je k dispozici pro C# a Visual Basic projekty, které cílí na .NET Core nebo .NET Framework v edici Enterprise sady Visual Studio.

Při použití Live Unit Testing pro testy, uchovává data o stavu testů. Použití trvalých dat umožňuje Live Unit Testing nabízet špičkový výkon při spouštění testů dynamicky v reakci na změny kódu.

## <a name="supported-test-frameworks"></a>Podporované testovacích architektur

Live Unit Testing spolupracuje s tři rozhraní testování částí oblíbených uvedené v následující tabulce. Zobrazuje se taky minimální podporovaná verze jejich adaptérů a platforem. Rozhraní testování částí jsou všechny dostupné z webu NuGet.org.

|Rozhraní pro testování  |Minimální verze aplikace Visual Studio adaptéru  |Minimální verze rozhraní Framework  |
|---------|---------|---------|
|xUnit.net |verze 2.2.0-beta3-build1187 xunit.Runner.VisualStudio |1\.9.2 xunit |
|NUnit |NUnit3TestAdapter verzí 3.5.1 |NUnit verze 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Pokud máte starší testovací projekty založené na MSTest, které odkazují na Microsoft. VisualStudio. QualityTools. UnitTestFramework, a nechcete přejít na novější balíčky NuGet MSTest, upgradujte na Visual Studio 2019 nebo Visual Studio 2017.

V některých případech může být nutné explicitně obnovit balíčky NuGet, na které odkazuje projekt, aby mohla Live Unit Testing fungovat. To můžete provést buď explicitním sestavením řešení (vyberte **sestavení > znovu** **Sestavit řešení** z nabídky nejvyšší úrovně), nebo obnovením balíčků v řešení (klikněte pravým tlačítkem na řešení a vyberte **obnovit balíčky NuGet**).

## <a name="configure"></a>Konfigurovat

Nakonfigurujte Live Unit Testing výběrem **nástrojů** > **Možnosti** na nejvyšší úrovni řádku nabídek sady Visual Studio a potom v levém podokně dialogového okna **Možnosti** vyberte **Live Unit Testing** .

> [!TIP]
> Po povolení Live Unit Testing (viz další část, [spuštění, pozastavení a zastavení Live Unit Testing](#start-pause-and-stop)) můžete také otevřít dialogové okno **Možnosti** výběrem možnosti **test** > **Live Unit Testing** > **Možnosti**.

Následující obrázek ukazuje možnosti konfigurace Live Unit Testing, které jsou k dispozici v dialogovém okně:

![Možnosti konfigurace Live Unit Testing](./media/lut-options.png)

Konfigurovatelných možností, které patří:

- Určuje, zda Live Unit Testing pozastaví při řešení je sestavení a ladění.

- Určuje, zda Live Unit Testing pozastaví při napájení z baterie systému klesne pod zadanou prahovou hodnotu.

- Určuje, zda Live Unit Testing spustí automaticky při otevření řešení.

- Jestli se má povolit ladění symbolů a generování komentáře dokumentace XML.

- Adresáře, ve kterém k uložení trvalá data.

- Možnost odstranit všechny trvalá data. To je užitečné, když se Live Unit Testing chová v nepředvídatelném nebo neočekávaném způsobu, což naznačuje, že trvalá data jsou poškozena.

- Interval, po kterém vypršel časový limit testovacího případu. Výchozí hodnota je 30 sekund.

- Maximální počet testovacích procesů, které vytvoří Live Unit Testing.

- Maximální množství paměti, které využívají Live Unit Testing procesy.

- Úroveň informací, zapsán do Live Unit Testing **výstup** okna.

   Mezi možnosti patří žádné protokolování (**žádný**), chybové zprávy pouze (**chyba**), chybové zprávy a informační zprávy (**informace o**, výchozí hodnota), nebo všechny podrobnosti (**Verbose** ).

   Můžete také zobrazit podrobný výstup v Live Unit Testing **výstup** okna tak, že přiřadíte hodnotu "1" do proměnné prostředí na úrovni uživatele s názvem `VS_UTE_DIAGNOSTICS`a následného restartování sady Visual Studio.

   Chcete-li zachytit podrobné zprávy protokolu MSBuild z Live Unit Testing v souboru, nastavte `LiveUnitTesting_BuildLog` individuální prostředí proměnnou pro název souboru, který má obsahovat protokol.

## <a name="start-pause-and-stop"></a>Spuštění, pozastavení a zastavení

Chcete-li povolit Live Unit Testing, vyberte možnost **Test** > **Live Unit Testing** > **Start** v nabídce aplikace Visual Studio nejvyšší úrovně. Když je povolený Live Unit Testing, možnosti dostupné v nabídce **Live Unit Testing** se změní z jedné položky, **Start**, na **pozastavit** a **zastavit**:

- **Pozastavení** dočasně pozastaví Live Unit Testing.

  Když je Live Unit Testing pozastavit, vizualizace pokrytí se v editoru nezobrazí, ale všechna shromážděná data se zachovají. Chcete-li pokračovat v Live Unit Testing, vyberte **pokračovat** z nabídky Live Unit Testing. Live Unit Testing provádí potřebnou práci pro zachycení všech úprav, které byly provedeny v době, kdy byla pozastavena, a odpovídajícím způsobem aktualizuje glyfy.

- **Zastavení** Live Unit Testing zcela zastaví. Live Unit Testing odstraní všechna data, která se budou shromažďovat.

> [!NOTE]
> Pokud začnete Live Unit Testing v řešení, které neobsahuje projekt testování částí, možnosti **pozastavit** a **zastavit** se zobrazí v nabídce **Live Unit Testing** , ale Live Unit Testing nespustí. V okně **výstup** se zobrazí zpráva, která začíná. Toto řešení neodkazuje na žádné podporované adaptéry testů...

Kdykoli můžete dočasně pozastavit nebo úplně zastavit Live Unit Testing. To může být vhodné například v případě, že jste uprostřed refaktoringu a víte, že testy budou v průběhu chvilky přerušeny.

## <a name="view-coverage-visualization"></a>Zobrazit vizualizaci pokrytí

Po povolení Live Unit Testing aktualizuje jednotlivé řádky kódu v editoru sady Visual Studio, aby se zobrazila informace o tom, zda se kód, který píšete, zabývá testy jednotek a zda jsou testy, které se na něj vztahují, přecházejí. Následující obrázek ukazuje řádky kódu s předáváním i neúspěšnými testy, jakož i řádky kódu, které nejsou pokryty testy. Pouze předáním testy jsou pokryté řádky upravené pomocí zelený "✓", jeden nebo více selhávající testy jsou pokryté řádky upravené pomocí red "x" a řádky upravena podle modrý "➖" nejsou pokryty všemi jakýkoli test.

![Pokrytí kódu v aplikaci Visual Studio](./media/lut-codewindow.png)

Vizualizace pokrytí Live Unit Testing je okamžitě aktualizována při úpravě kódu v editoru kódu. Při zpracování úprav se změny vizualizace, které označují, že data nejsou aktuální, přidáním obrázku kulatého časovače pod průchozí, neúspěšné a nezahrnuté symboly, jak ukazuje následující obrázek.

![Pokrytí kódu v aplikaci Visual Studio s ikonou časovače](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Získat informace o stavu testu

Podržením ukazatele nad symbol bylo úspěšné nebo neúspěšné v okně kódu, uvidíte, kolik testů se tím tento řádek. Chcete-li zobrazit stav jednotlivých testů, vyberte symbol:

![Stav testu pro symbol v aplikaci Visual Studio](./media/lut-failedinfo.png)

Kromě poskytování názvů a výsledků testů vám popisek umožňuje znovu spustit nebo ladit sadu testů. Pokud vyberete jednu nebo více testů v popisu, můžete také spustit nebo ladit pouze tyto testy. To umožňuje ladit testy bez odejití z okna kódu. Při ladění, kromě pozorování všech zarážek, které jste již pravděpodobně nastavili, se spuštění programu pozastaví, když ladicí program spustí metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>, která vrací neočekávaný výsledek.

Když najedete myší neúspěšných testů v popisu, rozšiřuje poskytnout další informace o selhání, jak je znázorněno na následujícím obrázku. Pokud chcete přejít přímo k neúspěšnému testu, poklikejte na něj v popisku.

![Neúspěšné informace popisu tlačítka testu v aplikaci Visual Studio](./media/lut-failedmsg.png)

Když přejdete na neúspěšný test, Live Unit Testing vizuálně indikuje v podpisu metody testy, které mají:

- předáno (označeno poloviční plnou kádinkou a zelenou "✓")
- neúspěšné (polovina plná kádinka s červeným "🞩")
- nejsou zapojené do Live Unit Testing (poloviční plná kádinka spolu s modrou "➖").

Bez testovacích metod nejsou upravené pomocí symbolu. Následující obrázek znázorňuje všechny čtyři typy metod.

![Testovací metody v aplikaci Visual Studio se symbolem Pass nebo neúspěchu](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostikujte a opravte chyby a testů

Z neúspěšného testu můžete snadno ladit kód produktu, provádět úpravy a pokračovat ve vývoji aplikace. Vzhledem k tomu, že Live Unit Testing běží na pozadí, není nutné zastavit a restartovat Live Unit Testing během cyklu ladění, úprav a pokračování.

Například selhání testu zobrazené na předchozím obrázku bylo způsobeno nesprávným předpokladem v metodě testu, že neabecední znaky vracejí `true` při předání do metody <xref:System.Char.IsLower%2A?displayProperty=fullName>. Po opravě testovací metody by měly projít všechny testy. Nemusíte pozastavit ani zastavit Live Unit Testing.

## <a name="test-explorer"></a>Průzkumník testů

**Průzkumník testů** poskytuje rozhraní, které umožňuje spouštět a ladit testy a analyzovat výsledky testů. Live Unit Testing integruje **Průzkumník testů**. Live Unit Testing není povolena nebo je zastavená, **Průzkumníka testů** zobrazuje stav testů jednotek při posledním spuštění testu. Změny zdrojového kódu vyžadují, znovu spusťte testy. Naproti tomu při zapnuté funkci Live Unit Testing, stav jednotky, které se testuje v **Průzkumník testů** ihned aktualizovat. Nemusíte explicitně spouštět testy jednotek.

> [!TIP]
> Otevřete **Průzkumník testů** výběrem možnosti **test** > **Windows** > **Průzkumník testů** v nabídce Visual Studio nejvyšší úrovně.

V okně **Průzkumník testů** si můžete všimnout, že některé testy jsou vybledlé. Pokud například povolíte Live Unit Testing po otevření dříve uloženého projektu, okno **Průzkumník testů** vynechalo vše, ale neúspěšný test, jak ukazuje následující obrázek. V tomto případě Live Unit Testing znovu spustit neúspěšný test, ale nespustí úspěšné testy znovu. Důvodem je to, že trvalá data Live Unit Testing znamenají, že se od posledního spuštění testů nezměnily žádné změny.

![Neúspěšný test v Průzkumníku testů](media/lut-test-explorer.png)

Můžete znovu spustit všechny testy, které se projeví na zvolna, a to výběrem možnosti **Spustit vše** nebo **Spustit** z nabídky **Průzkumník testů** . Nebo vyberte jeden nebo více testů v nabídce **Průzkumník testů** , klikněte pravým tlačítkem myši a vyberte možnost **Spustit vybrané testy** nebo **ladit vybrané testy** z místní nabídky. Jak jsou testy spuštěny, jejich pokračovala horní části.

Existují určité rozdíly mezi Live Unit Testing automatickým spuštěním a aktualizuje výsledky testů a explicitně spouštění testů z **Průzkumníka testů**. Tyto rozdíly mezi patří:

- Spouštění nebo ladění testů z okna Průzkumníka testů běží regulární binární soubory, zatímco Live Unit Testing běží instrumentované binární soubory.
- Live Unit Testing nevytvoří novou doménu aplikace pro spuštění testů, ale místo toho spustí testy z výchozí doménu. Spustit testy z **Průzkumník testů** okno Vytvořit novou doménu aplikace.
- Live Unit Testing spustí testy v každé sestavení testu postupně. V okně **Průzkumník testů** můžete zvolit paralelní spuštění více testů.

## <a name="large-solutions"></a>Velká řešení

Pokud má vaše řešení 10 nebo více projektů, Visual Studio zobrazí následující dialog, když:

- spustit Live Unit Testing a neexistují žádná trvalá data
- Vyberte **nástroje** > **možnosti** > **Live Unit Testing** > **Odstranit trvalá data** .

![Live Unit Testing dialogové okno pro velké projekty](media/lut-large-project.png)

Dialog vás upozorní na to, že dynamické spuštění velkého počtu testů ve velkých projektech může mít vážně vliv na výkon. Pokud vyberete **OK**, Live Unit Testing spustí všechny testy v řešení. Pokud vyberete **zrušit**, můžete vybrat testy ke spuštění. V následující části se dozvíte, jak to provést.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Zahrnout a vyloučit projekty testů a testovací metody

Pro řešení s mnoha testovacími projekty můžete určit, které projekty a jednotlivé metody v projektu se účastní Live Unit Testing. Pokud máte řešení s využitím stovek projekty testů, můžete vybrat cílovou sadu testovacích projektů k účasti v Live Unit Testing. To lze provést několika způsoby v závislosti na tom, zda chcete vyloučit všechny testy v projektu nebo řešení, zahrnout nebo vyloučit většinu testů nebo vyloučit jednotlivé testy. Live Unit Testing uloží stav zahrnout nebo vyloučit jako nastavení uživatele a zapamatuje, když je řešení zavřít a znovu otevřít.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Vyloučit všechny testy v projektu nebo řešení

Chcete-li vybrat jednotlivé projekty při testech jednotek, proveďte následující po Live Unit Testing je spuštění:

1. Klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a zvolte **Live testy** > **vyloučit** vyloučit celé řešení.
1. Klikněte pravým tlačítkem na každý testovací projekt, který chcete zahrnout do testů a zvolte **Live testy** > **zahrnout**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Vyloučit jednotlivé testy z okna editoru kódu

Okna editoru kódu můžete použít k zahrnutí nebo vyloučení jednotlivých testovacích metod. Klikněte pravým tlačítkem na podpis testovací metody v okně editoru kódu a vyberte jednu z následujících možností:

- **Živé testy** > **Zahrnout \<vybranou metodu >**
- **Živé testy** > **vyloučení \<vybrané metody >**
- **Živé testy** > **vyloučí všechny \<vybrané metody, ale >**

### <a name="exclude-tests-programmatically"></a>Vyloučení testů prostřednictvím kódu programu

Můžete použít <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atribut programově vyloučené z hlášení jejich pokrytí v Live Unit Testing metody, třídy nebo struktury.

Pomocí následujících atributů vylučte jednotlivé metody z Live Unit Testing:

- Pro xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Pomocí následujících atributů vylučte celé sestavení testů z Live Unit Testing:

- Pro xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Viz také:

- [Kód testovací nástroje](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blogu Live Unit Testing](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Nejčastější dotazy k funkci Live Unit Testing](live-unit-testing-faq.md)
- [Video pro kanál 9: Live Unit Testing v aplikaci Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
