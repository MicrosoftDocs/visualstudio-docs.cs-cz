---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: e4ace476a2454c7f6735f19cd07f222d6c06564e
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913335"
---
# <a name="live-unit-testing-with-visual-studio"></a>Live Unit Testing se sadou Visual Studio

Vyvíjíte aplikaci, Live Unit Testing automaticky spustí všechny testy jednotek během toho na pozadí a představuje výsledky a pokrytí kódu za provozu v rozhraní IDE sady Visual Studio v reálném čase. Při úpravě kódu, na jaký vliv na existující testy změny Live Unit Testing poskytuje zpětnou vazbu a určuje, zda nový kód jste přidali se vztahuje na jeden nebo více existujících testů. To je pro psaní jednotkových testů při provádění oprav chyb a přidání nových funkcí jemně připomene.

> [!NOTE]
> Live Unit Testing je k dispozici pro C# a Visual Basic projekty, které cílí na rozhraní .NET Core nebo .NET Framework ve verzi Enterprise sady Visual Studio.

Pokud používáte Live Unit Testing pro testy, Live Unit Testing uchovává data o stavu vašich testů. Schopnost používat trvalých dat umožňuje Live Unit Testing nabízí špičkový výkon při spouštění testů dynamicky v reakci na změny kódu.

## <a name="supported-test-frameworks"></a>Podporované testovacích architektur
Live Unit Testing spolupracuje s tři rozhraní testování částí oblíbených uvedené v následující tabulce. Minimální podporovaná verze jejich adaptéry a rozhraní je také uvedený v tabulce. Rozhraní testování částí jsou všechny dostupné z webu NuGet.org.

|Rozhraní pro testování  |Minimální verze aplikace Visual Studio adaptéru  |Minimální verze rozhraní Framework  |
|---------|---------|---------|
|xUnit.net |verze 2.2.0-beta3-build1187 xunit.Runner.VisualStudio |1\.9.2 xunit |
|NUnit |NUnit3TestAdapter verzí 3.5.1 |NUnit verze 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Pokud máte starší projekty `Microsoft.VisualStudio.QualityTools.UnitTestFramework` testů založené na MSTest a nechcete přejít k novějším balíčkům NuGet MSTest, upgradujte na Visual Studio 2017 verze 15,4 nebo novější.

V některých případech budete muset explicitně obnovit balíčky NuGet odkazované projekty v řešení v pořadí pro Live Unit Testing pro práci. Uděláte to buď tímto způsobem vytvořte explicitní sestavení řešení (vyberte **sestavení** > **znovu sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio) nebo obnovují se balíčky v řešení ( Klikněte pravým tlačítkem na řešení a vyberte **obnovit balíčky NuGet**) před povolením živých Unit Testing.

## <a name="configure-live-unit-testing"></a>Konfigurace Live Unit Testing

Live Unit Testing můžete nakonfigurovat tak, že vyberete **nástroje** > **možnosti** z nejvyšší úrovně řádku nabídek sady Visual Studio a pak vyberete **Live Unit Testing** v levém podokně **možnosti** dialogového okna.

> [!TIP]
> Jakmile povolíte službu Live Unit Testing (naleznete v části Další [spustit, pozastavit a zastavit Live Unit Testing](#start-pause-and-stop-live-unit-testing)), můžete také otevřít **možnosti** dialogové okno tak, že vyberete **testovací**  >  **Live Unit Testing** > **možnosti**.

Následující obrázek znázorňuje Live Unit Testing možnosti konfigurace k dispozici v dialogovém okně:

  ![Image](./media/lut-options.png)

Konfigurovatelných možností, které patří:

- Určuje, zda Live Unit Testing pozastaví při řešení je sestavení a ladění.

- Určuje, zda Live Unit Testing pozastaví při napájení z baterie systému klesne pod zadanou prahovou hodnotu.

- Určuje, zda Live Unit Testing spustí automaticky při otevření řešení.

- Jestli se má povolit ladění symbolů a generování komentáře dokumentace XML.

- Adresáře, ve kterém k uložení trvalá data.

- Možnost odstranit všechny trvalá data. To je užitečné, když Live Unit Testing je chovat nepředvídatelnými nebo neočekávané způsobem, což naznačuje, že došlo k poškození trvalá data.

- Interval, po jejímž uplynutí testovacího případu vyprší časový limit; Výchozí hodnota je 30 sekund.

- Maximální počet testovacích procesů, které vytvoří Live Unit Testing.

- Maximální množství paměti, které využívají Live Unit Testing procesy.

- Úroveň informací, zapsán do Live Unit Testing **výstup** okna.

   Mezi možnosti patří žádné protokolování (**žádný**), chybové zprávy pouze (**chyba**), chybové zprávy a informační zprávy (**informace o**, výchozí hodnota), nebo všechny podrobnosti (**Verbose** ).

   Můžete také zobrazit podrobný výstup v Live Unit Testing **výstup** okna tak, že přiřadíte hodnotu "1" do proměnné prostředí na úrovni uživatele s názvem `VS_UTE_DIAGNOSTICS`a následného restartování sady Visual Studio.

   Chcete-li zachytit podrobné zprávy protokolu MSBuild z Live Unit Testing v souboru, nastavte `LiveUnitTesting_BuildLog` individuální prostředí proměnnou pro název souboru, který má obsahovat protokol.

## <a name="start-pause-and-stop-live-unit-testing"></a>Spuštění, pozastavení a zastavit Live Unit Testing

Povolíte tak, že vyberete Live Unit Testing **testovací** > **Live Unit Testing** > **Start** z nejvyšší úrovně nabídky sady Visual Studio. Když Live Unit Testing je povoleno, možnosti, které jsou k dispozici na **Live Unit Testing** změnu nabídky z jedné položky, **Start**do **pozastavení**, **Zastavit**, a **resetování čištění**.

> [!NOTE]
> Je-li spustit Live Unit Testing v řešení, která neobsahuje projekt testování částí, **pozastavení**, **Zastavit**, a **resetování čisté** možnosti se zobrazí na **Live Testování jednotek** nabídky, ale Live Unit Testing nespustí. **Výstup** okno zobrazí zprávu, která začíná "žádné adaptéry testu podporované není odkazováno pomocí tohoto řešení..."

Kdykoli můžete dočasně pozastavit nebo úplně zastavit Live Unit Testing. Můžete to provést, například pokud uprostřed Refaktoring a vědět, že testy se přeruší nějakou dobu. Nabídka tři možnosti jsou:

- **Pozastavit**, které dočasně pozastaví Live Unit Testing.

    Pokud Live Unit Testing je pozastavený, vaše vizualizace pokrytí se nezobrazí v editoru, ale zachovají všechna data, která byla shromážděna. Chcete-li pokračovat v Live Unit Testing, vyberte **pokračovat** z nabídky Live Unit Testing. Live Unit Testing provádí potřebné dohnat všechny úpravy, které byly provedeny, když byla pozastavena a odpovídajícím způsobem aktualizuje glyfy.

- **Zastavit**, úplně zastavit Live Unit Testing. Live Unit Testing odstraní všechna data, která se budou shromažďovat.

- **Resetovat Vyčistit**, které zastaví Live Unit Testing, trvalá data odstraní a restartuje Live Unit Testing.

- **Možnosti**, otevře **možnosti** dialogového okna popsané v [konfigurace Live Unit Testing](#configure-live-unit-testing) oddílu.

## <a name="view-coverage-visualization-in-the-editor-as-you-type"></a>Zobrazit pokrytí vizualizace v editoru během psaní

Jednou povolená, Live Unit Testing aktualizací všech řádků kódu v editoru sady Visual Studio, chcete-li zobrazit, zda kód, který píšete je pokryta testy jednotek a zda úspěšných testů, které ho pokrývají.  Následující obrázek znázorňuje řádky kódu s jak úspěšným a neúspěšným testy, stejně jako řádky kódu, které nejsou pokryty všemi testy. Pouze předáním testy jsou pokryté řádky upravené pomocí zelený "✓", jeden nebo více selhávající testy jsou pokryté řádky upravené pomocí red "x" a řádky upravena podle modrý "➖" nejsou pokryty všemi jakýkoli test.

  ![Image](./media/lut-codewindow.png)

Live Unit Testing pokrytí vizualizace je ihned aktualizovat při úpravě kódu v editoru kódu. Při zpracování úprav, změn vizualizace k označení, že data nejsou tak, že přidáte kruhové časovače aktuální obrázku dole předání služeb při selhání a nejsou pokryty symboly, jak ukazuje následující obrázek.

  ![Image](./media/lut-codeupdating.png)

## <a name="get-information-on-successful-or-failed-tests"></a>Získejte informace o úspěšných a neúspěšných testů

Podržením ukazatele nad symbol bylo úspěšné nebo neúspěšné v okně kódu, uvidíte, kolik testů se tím tento řádek. Pokud kliknete na symbol, zobrazí se stav jednotlivých testů, jak ukazuje následující obrázek:

  ![Image](./media/lut-failedinfo.png)

Kromě toho, že názvy a výsledky testů, umožňuje popisku můžete znovu spustit sadu testů, a ke spuštění sady testů pomocí ladicího programu. Pokud vyberete jednu nebo více testů v popisu, můžete také spustit nebo ladit pouze tyto testy. To umožňuje ladit testy bez odejití z okna kódu. Při ladění, kromě sledování všechny zarážky, možná jste už nastavili, pozastaví provádění programu při spustí ladicí program [ `Assert` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) metodu, která vrací neočekávané výsledky.

Když najedete myší neúspěšných testů v popisu, rozšiřuje poskytnout další informace o selhání, jak je znázorněno na následujícím obrázku. Pokud dvakrát kliknete na neúspěšných testů v popisu, můžete přejít přímo k němu.

  ![Image](./media/lut-failedmsg.png)

Při návštěvě neúspěšných testů Live Unit Testing také vizuálně označuje v podpisu metody testy, které jste předali (uvedenými kádinky polovině plně spolu s zelený "✓"), se nezdařilo (režim polovině kádinky spolu s červeným "🞩"), nebo nejsou součástí Live Unit Testing (režim polovině kádinky spolu s modrým "➖"). Bez testovacích metod nejsou upravené pomocí symbolu. Následující obrázek znázorňuje všechny čtyři typy metod.

  ![Image](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostikujte a opravte chyby a testů

Z neúspěšných testů můžete snadno ladit kód produktu, proveďte úpravy a pokračovat ve vývoji vaší aplikace. Protože Live Unit Testing běží na pozadí, není nutné zastavit a restartovat Live Unit Testing během ladění, upravit a pokračovat v cyklu.

Například selhání testu je vidět na předchozím obrázku bylo způsobeno nesprávnou předpokladů v testovací metodě, která vrátí neabecedními znaky `true` když předána <xref:System.Char.IsLower%2A?displayProperty=fullName> metody. Jakmile jsme opravit testovací metody, zjistíme, že všechny testy byly úspěšné. Když jsme se v takovém případě nejsou k pozastavení nebo ukončení v Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing a Průzkumník testů

Obvykle **Průzkumníka testů** poskytuje rozhraní, které umožňuje spouštět, ladit a analyzovat výsledky testů. Live Unit Testing integruje **Průzkumník testů**. Live Unit Testing není povolena nebo je zastavená, **Průzkumníka testů** zobrazuje stav testů jednotek při posledním spuštění testu. Změny zdrojového kódu vyžadují, znovu spusťte testy. Naproti tomu při zapnuté funkci Live Unit Testing, stav jednotky, které se testuje v **Průzkumník testů** ihned aktualizovat. Už nemusíte explicitně spouštět testy jednotek.

> [!NOTE]
> Můžete otevřít **Průzkumník testů** tak, že vyberete **testovací** > **Windows** > **Průzkumník testů** z Visual Studio nabídek nejvyšší úrovně.

Můžete si všimnout v **Průzkumník testů** okno, které jsou některé testy barevně navýšení kapacity. Například, když povolíte Live Unit Testing po otevření dříve uložený projektu **Průzkumníka testů** okno měl barevně všechny ale neúspěšných testů, jak ukazuje následující obrázek. V tomto případě Live Unit Testing je znovu spustit neúspěšných testů, ale jeho nebyl znovu spusťte testy úspěšné, protože Live Unit Testing pro trvalé data označují, že vzhledem k tomu, že testy byly spuštěny poslední úspěšně nebyly provedeny žádné změny.

  ![Image](media/lut-test-explorer.png)

Můžete znovu spustit všechny testy, které se zobrazují barevně tak, že vyberete **spustit všechny** nebo **spustit** možnosti z **Průzkumník testů** nabídky, nebo tak, že vyberete jeden nebo více testů v **Průzkumník testů** nabídce kliknete pravým tlačítkem a vyberete **spustit vybrané testy** nebo **ladit vybrané testy** z místní nabídky. Jak jsou testy spuštěny, jejich pokračovala horní části.

Existují určité rozdíly mezi Live Unit Testing automatickým spuštěním a aktualizuje výsledky testů a explicitně spouštění testů z **Průzkumníka testů**. Tyto rozdíly mezi patří:

- Spouštění nebo ladění testů z okna Průzkumníka testů běží regulární binární soubory, zatímco Live Unit Testing běží instrumentované binární soubory.
- Live Unit Testing nevytvoří novou doménu aplikace pro spuštění testů, ale místo toho spustí testy z výchozí doménu. Spustit testy z **Průzkumník testů** okno Vytvořit novou doménu aplikace.
- Live Unit Testing spustí testy v každé sestavení testu postupně. V okně **Průzkumník testů** můžete zvolit možnost spuštění více testů paralelně.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing a rozsáhlých řešeních

Pokud má vaše řešení 10 nebo více projektů po spuštění funkce Live Unit Testing a neexistuje žádná trvalá data, nebo když vyberete **testovací** > **Live Unit Testing**  >  **Resetování čisté** možnost z nejvyšší úrovně nabídky sady Visual Studio, Visual Studio se zobrazí následující dialogové okno s upozorněním, že dynamické spuštění velkého počtu testů ve velkých projektech vážně může ovlivnit výkon. Pokud vyberete **OK**, Live Unit Testing spustí všechny testy v řešení. Pokud vyberete **zrušit**, můžete vybrat testy ke spuštění. Informace o tom, jak to provést, najdete v následující části, [zahrnutí a vyloučení projekty testů a testovací metody](#include-and-exclude-test-projects-and-test-methods).

![Live Unit Testing dialogové okno pro velké projekty](media/lut-large-project.png)

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Zahrnout a vyloučit projekty testů a testovací metody

Pro řešení s mnoha testovacích projektů můžete řídit, jaké projekty a jaké jednotlivých metod v projektu účastnit Live Unit Testing. Pokud máte řešení s využitím stovek projekty testů, můžete vybrat cílovou sadu testovacích projektů k účasti v Live Unit Testing. Existuje několik způsobů, jak to provést, v závislosti na tom, jestli chcete vyloučit všechny testy v projektu nebo řešení, jestli se má zahrnout nebo vyloučit většinu testů, nebo zda chcete vyloučit otestuje jednotlivě. Live Unit Testing uloží stav zahrnout nebo vyloučit jako nastavení uživatele a zapamatuje, když je řešení zavřít a znovu otevřít.

**Kromě všech testů v projektu nebo řešení**

Chcete-li vybrat jednotlivé projekty při testech jednotek, proveďte následující po Live Unit Testing je spuštění:

1. Klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a zvolte **Live testy** > **vyloučit** vyloučit celé řešení.
1. Klikněte pravým tlačítkem na každý testovací projekt, který chcete zahrnout do testů a zvolte **Live testy** > **zahrnout**.

**Vyloučení jednotlivých testů z okna editoru kódu**

Okna editoru kódu můžete použít k zahrnutí nebo vyloučení jednotlivých testovacích metod. Klikněte pravým tlačítkem na podpis testovací metody v okně editoru kódu a vyberte **Live testy** >  **[vybranou metodu]** , **Live testy**  >  **Vyloučit [vybrané metody]** , nebo **Live testy** > **vyloučit vše kromě [vybrané metody]** , kde název je "vybranou metodu" Metoda, kterou jste vybrali v okně kódu.

**S výjimkou testů prostřednictvím kódu programu**

Můžete použít <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atribut programově vyloučené z hlášení jejich pokrytí v Live Unit Testing metody, třídy nebo struktury.

Také vám pomůže následující atributy z Live Unit Testing vyloučit jednotlivé metody:

- Pro xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Můžete také vyloučit celé sestavení testů z Live Unit Testing:

- Pro xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Pro NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Pro MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Viz také:

- [Kód testovací nástroje](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blogu Live Unit Testing](https://go.microsoft.com/fwlink/?linkid=842514)
- [Nejčastější dotazy k funkci Live Unit Testing](live-unit-testing-faq.md)
- [Video pro kanál 9: Live Unit Testing v aplikaci Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
