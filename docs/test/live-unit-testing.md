---
title: Live Unit Testing
description: Přečtěte si o Live Unit Testing při vývoji aplikací, včetně podporovaných platforem a způsobu konfigurace Live Unit Testing.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: b9b78771c36dce26744ba74af63922cf1efa48e2
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798619"
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
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Pokud máte starší projekty testů založené na MSTest, které odkazují na Microsoft.VisualStudio.QualityTools.UnitTestFramework, a nechcete přejít na novější balíčky MSTest NuGet, upgradujte na Visual Studio 2019 nebo Visual Studio 2017.

V některých případech možná budete muset explicitně obnovit balíčky NuGet odkazované projektem, aby Live Unit Testing fungovaly. Můžete to provést buď explicitním sestavením řešení (v nabídce Visual Studio nejvyšší úrovně vyberte Sestavit řešení znovu sestavit) nebo obnovením balíčků v řešení (klikněte pravým tlačítkem na řešení a vyberte Obnovit balíčky  >   **NuGet).**

## <a name="configure"></a>Konfigurace

Nakonfigurujte Live Unit Testing tak, že v řádku nabídek na nejvyšší úrovni vyberete Možnosti nástrojů Visual Studio pak v levém podokně dialogového okna Live Unit Testing vyberete Další  >   možnosti.  

> [!TIP]
> Po Live Unit Testing (viz další část [Spuštění, pozastavení](#start-pause-and-stop)a zastavení Live Unit Testing ) můžete také  otevřít dialogové okno Možnosti výběrem možnosti  >  **Test Live Unit Testing**  >  **Možnosti**.

Následující obrázek znázorňuje možnosti Live Unit Testing konfigurace dostupné v dialogovém okně:

![Live Unit Testing možnosti konfigurace](./media/lut-options.png)

Mezi konfigurovatelné možnosti patří:

- Určuje Live Unit Testing se pozastaví při sestavení a ladění řešení.

- Určuje Live Unit Testing se pozastaví, když napájení baterie v systému klesne pod zadanou prahovou hodnotu.

- Určuje Live Unit Testing se spustí automaticky při otevření řešení.

- Určuje, jestli se má povolit generování ladicích symbolů a komentářů dokumentace XML.

- Adresář, do kterého se mají ukládat trvalá data.

- Možnost odstranit všechna trvalá data. To je užitečné, Live Unit Testing se chová nepředvídatelným nebo neočekávaným způsobem, což naznačuje, že trvalá data jsou poškozená.

- Interval, po jehož uplynutí časový limit testovacího případu Výchozí hodnota je 30 sekund.

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

Kdykoli můžete dočasně pozastavit nebo úplně zastavit Live Unit Testing. Můžete to udělat například v případě, že jste uprostřed refaktoringu a víte, že vaše testy budou na chvíli přerušené.

## <a name="view-coverage-visualization"></a>Zobrazení vizualizace pokrytí

Po jeho povolení Live Unit Testing aktualizuje každý řádek kódu v editoru Visual Studio, aby vám ukázal, jestli kód, který píšete, je pokryt testy jednotek a jestli testy, které ho pokrývají, jsou úspěšné. Následující obrázek ukazuje řádky kódu s úspěšné i neúspěšné testy a také řádky kódu, které testy nepokrýjí. Čáry, které jsou dekorované zeleným ":", jsou pokryté pouze absolvováním testů, čáry dekorované červeným "x" jsou pokryty jedním nebo více neúspěšných testy a čáry dekorované modrým "➖" nejsou pokryty žádným testem.

![Pokrytí kódu v Visual Studio](./media/lut-codewindow.png)

Live Unit Testing pokrytí se aktualizuje okamžitě při úpravě kódu v editoru kódu. Při zpracování úprav se vizualizace změní, aby indikuje, že data nejsou aktuální, a to přidáním obrázku s kruhovým časovačem pod předávkující, neúspěšné a nepokryté symboly, jak je vidět na následujícím obrázku.

![Pokrytí kódu v Visual Studio ikonou časovače](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Získání informací o stavu testu

Když najedete myší na symbol Úspěch nebo Nedaří se v okně kódu, uvidíte, kolik testů na tento řádek ujelo. Pokud chcete zobrazit stav jednotlivých testů, vyberte symbol:

![Stav testu symbolu v Visual Studio](./media/lut-failedinfo.png)

Kromě zadání názvů a výsledků testů vám popis umožňuje znovu spustit nebo ladit sadu testů. Pokud vyberete jeden nebo více testů v popisu, můžete také spustit nebo ladit pouze tyto testy. To vám umožní ladit testy, aniž byste museli opustit okno kódu. Při ladění se kromě sledování všech zarážek, které jste už možná nastavili, pozastaví provádění programu, když ladicí program spustí metodu, která <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> vrací neočekávaný výsledek.

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

**Průzkumník testů** poskytuje rozhraní, které umožňuje spouštět a ladit testy a analyzovat výsledky testů. Live Unit Testing se integruje s **průzkumníkem testů**. Pokud Live Unit Testing není povolen nebo je zastaven, **Průzkumník testů** zobrazí stav testů testování při posledním spuštění testu. Změny zdrojového kódu vyžadují, abyste znovu znovu provedli testy. Naopak pokud Live Unit Testing, stav testů jednotek v Průzkumníku testů se okamžitě aktualizuje.  Testy jednotek nemusíte spouštět explicitně.

> [!TIP]
> Otevřete **Live Unit Testing** tak, **že** v nabídce nejvyšší úrovně vyberete Test  >  **Průzkumníka** testů Visual Studio  >   windows.

V okně Průzkumníka **testů** si můžete všimnout, že některé testy postupně zmizí. Když například po otevření dříve uloženého projektu povolíte  Live Unit Testing, okno Průzkumníka testů postupně zesláblo všechno, ale neúspěšný test, jak je vidět na následujícím obrázku. V tomto případě Live Unit Testing znovu spustit neúspěšný test, ale úspěšně neproběhl. Je to proto Live Unit Testing trvalá data indikuje, že od posledního úspěšného spuštění testů nebyly žádné změny.

![Neúspěšný test v Průzkumníku testů](media/lut-test-explorer.png)

Všechny testy, které se zobrazují jako  prolnutí, můžete spustit znovu tak, že v nabídce Průzkumníka testů vyberete možnosti Spustit vše nebo **Spustit.**  Nebo vyberte jeden nebo více testů v nabídce **Průzkumník** testů,  klikněte pravým  tlačítkem a pak v místní nabídce vyberte Spustit vybrané testy nebo Ladit vybrané testy. Při spouštění testů se v horní části promísí.

Mezi automatickým spuštěním a aktualizací výsledků Live Unit Testing a explicitním spouštěním testů z Průzkumníka testů existují **určité rozdíly.** Mezi tyto rozdíly patří:

- Spouštění nebo ladění testů z okna Průzkumníka testů spouští běžné binární soubory, zatímco Live Unit Testing spouští instrumentované binární soubory.
- Live Unit Testing nevytváří novou doménu aplikace pro spouštění testů, ale spouští testy z výchozí domény. Testy spouštěné z okna **Průzkumníka testů** vytvoří novou doménu aplikace.
- Live Unit Testing postupně spouští testy v každém testovacím sestavení. V okně **Průzkumníka** testů můžete spustit více testů paralelně.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing okno

**Live Unit Testing**, podobně jako **Průzkumník testů**, poskytuje rozhraní, které umožňuje spouštět a ladit testy a analyzovat výsledky testů. Když je povoleno Live Unit Testing, stav testů jednotek v **Průzkumníku testů** se okamžitě aktualizuje. Nemusíte explicitně spouštět testy jednotek. Pokud Live Unit Testing není povolen nebo je zastaven, **Live Unit Testing** zobrazí stav testů testování při posledním spuštění testu. Po restartování Live Unit Testing se pro opětovné spuštění testů vyžaduje změna zdrojového kódu.

> [!TIP]
> Začněte Live Unit Testing výběrem možnosti **test**  >  **Live Unit Testing**  >  **začít** v nabídce aplikace Visual Studio nejvyšší úrovně. Můžete také otevřít okno **Live Unit Testing** pomocí **zobrazení**  >  **jiných**  >  **oken Live Unit Testing** Windows.

V okně **Live Unit Testing** můžete všimnout, že některé testy jsou vybledlé. Například při zastavení a restartování Live Unit Testing **Live Unit Testing** okno vykreslí všechny testy, jak ukazuje následující obrázek. Výsledky nepatrného testu ukazují, že test nebyl součástí nejnovějšího běhu služby Live Unit Test. Testy se spustí pouze v případě, že je zjištěna změna testu nebo závislostí testu. Pokud nedojde ke změně, vyhnete se tak zbytečnému spuštění testu. V tomto případě je výsledek šedé testu stále "aktuální", i když nebyl součástí posledního spuštění.

![Vybledlé testy v Průzkumníku testů](media/vs-2019/lut-test-explorer.png)

Můžete znovu spustit všechny testy, které se projeví při změně kódu.

Některé rozdíly mezi Live Unit Testing automaticky spouští a aktualizují výsledky testů a explicitně spouštějící testy z **Průzkumníka testů**. Mezi tyto rozdíly patří:

- Spuštění nebo ladění testů z okna Průzkumníka testů spouští běžné binární soubory, zatímco Live Unit Testing spouští instrumentované binární soubory.
- Live Unit Testing nevytváří novou doménu aplikace pro spuštění testů, ale místo toho spustí testy z výchozí domény. Testy spouštěné z okna **Průzkumníka testů** vytvoří novou doménu aplikace.
- Live Unit Testing postupně spouští testy v každém testovacím sestavení. V okně **Průzkumníka** testů můžete spustit více testů paralelně.
::: moniker-end

## <a name="large-solutions"></a>Rozsáhlá řešení

Pokud má vaše řešení 10 nebo více projektů, Visual Studio při spuštění zobrazí následující dialogové okno:

- spuštění Live Unit Testing a neexistují žádná trvalá data
- Výběr **možností**  >  **Nástroje**  >  **Live Unit Testing**  >  **odstranění trvalých dat**

![Live Unit Testing dialogové okno pro velké projekty](media/lut-large-project.png)

Dialog vás upozorní, že dynamické provádění velkého počtu testů ve velkých projektech může mít závažný dopad na výkon. Pokud vyberete **OK,** Live Unit Testing spustí všechny testy v řešení. Pokud **vyberete Zrušit,** můžete vybrat testy, které se budou spouštět. Následující část vysvětluje, jak to provést.

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>Zahrnutí a vyloučení testovacích projektů a testovacích metod

U řešení s mnoha projekty testů můžete řídit, které projekty a jednotlivé metody v projektu se účastní Live Unit Testing. Pokud máte například řešení se stovkami testovacích projektů, můžete vybrat cílovou sadu testovacích projektů, které se budou účastnit Live Unit Testing. Můžete to provést několika způsoby v závislosti na tom, jestli chcete vyloučit všechny testy v projektu nebo řešení, zahrnout nebo vyloučit většinu testů nebo vyloučit jednotlivé testy. Live Unit Testing uloží stav zahrnutí/vyloučení jako uživatelské nastavení a zapamatuje si ho při zavření a opětovném otevření řešení.

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>Vyloučení všech testů v projektu nebo řešení

Pokud chcete vybrat jednotlivé projekty v testech jednotek, po spuštění Live Unit Testing následující akce:

1. Klikněte pravým tlačítkem na řešení **v Průzkumník řešení** a zvolte **Live Unit Testing**  >  **Vyloučit,** abyste vyloučili celé řešení.
1. Klikněte pravým tlačítkem na každý testovací projekt, který chcete zahrnout do testů, a vyberte **Live Unit Testing**  >  **Zahrnout**.

### <a name=&quot;exclude-individual-tests-from-the-code-editor-window&quot;></a>Vyloučit jednotlivé testy z okna editoru kódu

Můžete použít okno editoru kódu k zahrnutí nebo vyloučení jednotlivých testovacích metod. Klikněte pravým tlačítkem na podpis testovací metody v okně editoru kódu a vyberte jednu z následujících možností:

- **Live Unit Testing**  >  **Zahrnout \<selected method>**
- **Live Unit Testing**  >  **Vyloučit \<selected method>**
- **Live Unit Testing**  >  **Vyloučit všechny kromě \<selected method>**

### <a name=&quot;exclude-tests-programmatically&quot;></a>Vyloučení testů prostřednictvím kódu programu

Atribut můžete použít <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> pro programové vyloučení metod, tříd nebo struktur z hlášení jejich pokrytí v Live Unit Testing.

Pomocí následujících atributů vylučte jednotlivé metody z Live Unit Testing:

- Pro xUnit: `[Trait(&quot;Category&quot;, &quot;SkipWhenLiveUnitTesting")]`
- Pro NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Pomocí následujících atributů vylučte celé sestavení testů z Live Unit Testing:

- Pro xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Viz také

- [Nástroje pro testování kódu](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog Live Unit Testing](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Nejčastější dotazy k funkci Live Unit Testing](live-unit-testing-faq.yml)
- [Video pro kanál 9: Live Unit Testing v aplikaci Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
