---
title: Naučte se testovat kód pomocí živého testování částí
description: Naučte se používat Live Unit Testing vytvořením jednoduché knihovny tříd, která cílí na .NET Standard a vytvoření projektu MSTest, který cílí na .NET Core pro otestování.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: d411465869cc960631063d09752d38536af94119
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683612"
---
# <a name="get-started-with-live-unit-testing"></a>Začínáme s funkcí Live Unit Testing

Pokud povolíte Live Unit Testing v řešení sady Visual Studio, vizuálně znázorňuje pokrytí testu a stav testů. Live Unit Testing také dynamicky spouští testy vždy, když upravíte kód a okamžitě vás upozorní, když vaše změny způsobí selhání testů.

Live Unit Testing lze použít k testování řešení, která cílí na .NET Framework nebo .NET Core. V tomto kurzu se naučíte používat Live Unit Testing vytvořením jednoduché knihovny tříd, která cílí na .NET Standard a vytvoříte projekt MSTest, který cílí na .NET Core pro otestování.

Kompletní řešení C# se dá stáhnout z úložiště [MicrosoftDocs/VisualStudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) na GitHubu.

## <a name="prerequisites"></a>Požadavky

Tento kurz vyžaduje, abyste nainstalovali edici Visual Studio Enterprise s využitím úlohy **vývoje .NET Core pro různé platformy** .

## <a name="create-the-solution-and-the-class-library-project"></a>Vytvořit řešení a projekt knihovny tříd

Začněte vytvořením řešení sady Visual Studio s názvem UtilityLibraries, které se skládá z jednoho .NET Standard projektu knihovny tříd StringLibrary.

Řešení je pouze kontejner pro jeden nebo více projektů. Chcete-li vytvořit prázdné řešení, otevřete aplikaci Visual Studio a proveďte následující kroky:

1.   >    >  V nabídce aplikace Visual Studio nejvyšší úrovně vyberte soubor nový **projekt** .

1. Do vyhledávacího pole šablony zadejte **řešení** a pak vyberte šablonu **prázdného řešení** . Pojmenujte projekt **UtilityLibraries**.

   ::: moniker range="vs-2017"

   ![Dialog * * Nový projekt * *](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Dokončete vytváření řešení.

Teď, když jste vytvořili řešení, vytvoříte knihovnu tříd s názvem StringLibrary, která obsahuje řadu metod rozšíření pro práci s řetězci.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení UtilityLibraries a vyberte **Přidat**  >  **Nový projekt**.

::: moniker range="vs-2017"

2. V dialogovém okně **Přidat nový projekt** vyberte uzel C# a pak vyberte **.NET Standard**.

   > [!NOTE]
   > Vzhledem k tomu, že naše knihovna cílí .NET Standard spíše než konkrétní implementace rozhraní .NET, může být volána z jakékoli implementace rozhraní .NET, která podporuje tuto verzi .NET Standard. Další informace najdete v tématu [.NET Standard](/dotnet/standard/net-standard).

3. V pravém podokně vyberte šablonu **Knihovna tříd (.NET Standard)** a do textového pole **název** zadejte **StringLibrary** , jak je znázorněno na následujícím obrázku:

   ![Dialog * * Přidat nový projekt * *](./media/lut-start/add-project-cs.png)

4. Vyberte **OK** a vytvořte projekt.

::: moniker-end

::: moniker range=">=vs-2019"

2. Do vyhledávacího pole šablony zadejte **knihovny tříd** a vyberte šablonu **knihovna tříd (.NET Standard)** . Klikněte na **Next** (Další).

   > [!NOTE]
   > Vzhledem k tomu, že naše knihovna cílí .NET Standard spíše než konkrétní implementace rozhraní .NET, může být volána z jakékoli implementace rozhraní .NET, která podporuje tuto verzi .NET Standard. Další informace najdete v tématu [.NET Standard](/dotnet/standard/net-standard).

3. Pojmenujte projekt **StringLibrary**.

4. Kliknutím na **vytvořit** vytvořte projekt.

::: moniker-end

5. Nahraďte veškerý existující kód v editoru kódu následujícím kódem:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary má tři statické metody:

   - `StartsWithUpper` Vrátí, `true` zda řetězec začíná velkým znakem. v opačném případě vrátí `false` .

   - `StartsWithLower`Vrátí, `true` zda řetězec začíná malým znakem. v opačném případě vrátí hodnotu `false` .

   - `HasEmbeddedSpaces` Vrátí, `true` zda řetězec obsahuje vložený prázdný znak. v opačném případě vrátí `false` .

6.   >  V nabídce aplikace Visual Studio nejvyšší úrovně vyberte **řešení** sestavení Build. Sestavení by mělo být úspěšné.

## <a name="create-the-test-project"></a>Vytvoření testovacího projektu

Dalším krokem je vytvoření projektu testu jednotek pro otestování knihovny StringLibrary. Testy jednotek vytvoříte provedením následujících kroků:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení UtilityLibraries a vyberte **Přidat**  >  **Nový projekt**.

::: moniker range="vs-2017"

2. V dialogovém okně **Přidat nový projekt** vyberte uzel C# a pak vyberte **.NET Core**.

   > [!NOTE]
   > Testy jednotek nemusíte psát ve stejném jazyce jako vaše knihovna tříd.

3. V pravém podokně vyberte šablonu **projekt testů jednotek (.NET Core)** a do textového pole **název** zadejte **StringLibraryTests** , jak ukazuje následující obrázek:

   ![Dialog * * Přidat nový projekt * * pro projekt testování částí](./media/lut-start/add-unit-test-cs.png)

4. Vyberte **OK** a vytvořte projekt.

   > [!NOTE]
   > Tento kurz Začínáme používá Live Unit Testing s testovacím rozhraním MSTest. Můžete také použít testovací architektury xUnit a NUnit.

::: moniker-end

::: moniker range=">=vs-2019"

2. Do pole hledání šablony zadejte **test jednotek** , jako jazyk vyberte **C#** a potom vyberte **projekt testování částí** pro šablonu .NET Core. Klikněte na **Next** (Další).

   > [!NOTE]
   > Počínaje verzí Visual Studio 2019 verze 16,9 se název šablony projektu MSTest změnil z **projektu testu jednotek MSTest (.NET Core)** na **test jednotek projektu**.

3. Pojmenujte projekt **StringLibraryTests** a klikněte na **Další**.

4. Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.

   > [!NOTE]
   > Tento kurz Začínáme používá Live Unit Testing s testovacím rozhraním MSTest. Můžete také použít testovací architektury xUnit a NUnit.

::: moniker-end

5. Projekt testu jednotek nemůže automaticky přistupovat ke knihovně tříd, kterou testuje. Přístup ke knihovně testů udělíte přidáním odkazu na projekt knihovny tříd. Chcete-li to provést, klikněte pravým tlačítkem myši na `StringLibraryTests` projekt a vyberte možnost **Přidat**  >  **odkaz**. V dialogovém okně **Správce odkazů** se ujistěte, že je vybraná karta **řešení** , a vyberte projekt StringLibrary, jak je znázorněno na následujícím obrázku.

   ![Dialogové okno * * Správce odkazů * *](./media/lut-start/add-reference.png)

6. Nahraďte kód pro standardní testování částí poskytovaný šablonou následujícím kódem:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Uložte projekt výběrem ikony **Uložit** na panelu nástrojů.

   Vzhledem k tomu, že kód testu jednotek obsahuje několik znaků, které nejsou ASCII, zobrazí se následující dialogové okno s upozorněním, že některé znaky budou ztraceny, pokud soubor uložíte ve výchozím formátu ASCII.

8. Klikněte na tlačítko **Uložit s jiným kódováním** .

   ![Zvolit kódování souboru](media/lut-start/ascii-encoding.png)

9. V rozevíracím seznamu **kódování** v dialogovém okně **možnosti uložení zálohy** vyberte možnost **Unicode (UTF-8 bez podpisu)-znaková stránka 65001**, jak ukazuje následující obrázek:

   ![Výběr kódování UTF-8](media/lut-start/utf8-encoding.png)

10. Zkompilujte projekt testů jednotek výběrem **sestavení sestavit znovu**  >  **sestavit** v nabídce aplikace Visual Studio nejvyšší úrovně.

Vytvořili jste knihovnu tříd a také některé testy jednotek pro ni. Nyní jste dokončili nezbytné úkony, která je potřebná k použití Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Povolit Live Unit Testing

Zatím i když jste napsali testy pro knihovnu tříd StringLibrary, neudělali jste je. Po povolení je Live Unit Testing spustí automaticky. Uděláte to takto:

1. Volitelně můžete vybrat okno editoru kódu, které obsahuje kód pro StringLibrary. Toto je buď *Class1.cs* pro projekt C# nebo *Class1. vb* pro projekt Visual Basic. (Tento krok vám umožní vizuální kontrolu výsledku testů a rozsahu pokrytí kódu, když povolíte Live Unit Testing.)

1.   >    >  V nabídce aplikace Visual Studio nejvyšší úrovně vyberte test Live Unit Testing **Spustit** .

1. Visual Studio spustí živý test jednotek, který automaticky spustí všechny testy.

::: moniker range="vs-2017"
Po dokončení testů v **Průzkumníku testů** se zobrazí celkové výsledky a výsledek jednotlivých testů. Kromě toho okno editoru kódu graficky zobrazuje jak pokrytí testovacího kódu, tak i výsledek pro vaše testy. Jak ukazuje následující obrázek, všechny tři testy byly úspěšně provedeny. Ukazuje také, že naše testy pokryly všechny cesty kódu v `StartsWithUpper` metodě a že všechny testy byly úspěšně spuštěny (což je označeno zelenou značkou zaškrtnutí "✓"). Nakonec ukazuje, že žádná z ostatních metod v StringLibrary nemá pokrytí kódu (což je označeno modrou čárou "➖").

![Průzkumník testů a okno editoru kódu po spuštění služby Live Unit Testing](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
Když nástroj dokončí testy, **Live Unit Testing** zobrazí celkové výsledky a výsledek jednotlivých testů. Kromě toho okno editoru kódu graficky zobrazuje jak pokrytí testovacího kódu, tak i výsledek pro vaše testy. Jak ukazuje následující obrázek, všechny tři testy byly úspěšně provedeny. Ukazuje také, že naše testy pokryly všechny cesty kódu v `StartsWithUpper` metodě a že všechny testy byly úspěšně spuštěny (což je označeno zelenou značkou zaškrtnutí "✓"). Nakonec ukazuje, že žádná z ostatních metod v StringLibrary nemá pokrytí kódu (což je označeno modrou čárou "➖").

![Okno Live Test Exploreru a editoru kódu po spuštění služby Live Unit Testing](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Můžete také získat podrobnější informace o pokrytí testu a výsledcích testů výběrem určité ikony pokrytí kódu v okně Editor kódu. Chcete-li prostudovat tuto podrobnost, postupujte následovně:

1. Klikněte na zelenou značku zaškrtnutí na řádku, který čte `if (String.IsNullOrWhiteSpace(s))` do `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing uvádí, že tři testy pokrývají tento řádek kódu a všechny byly úspěšně provedeny.

   ![Pokrytí kódu pro podmíněný příkaz if](media/lut-start/code-coverage-cs1.png)

1. Klikněte na zelenou značku zaškrtnutí na řádku, který čte `return Char.IsUpper(s[0])` do `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing označuje, že pouze dva testy pokrývají tento řádek kódu a všechny byly úspěšně provedeny.

   ![Pokrytí kódu pro příkaz return](media/lut-start/code-coverage-cs2.png)

Hlavní problém, který Live Unit Testing identifikuje, není úplným pokrytím kódu. Vyřešíte ho v další části.

## <a name="expand-test-coverage"></a>Rozbalit pokrytí testu

V této části rozšíříte testování částí do `StartsWithLower` metody. I když to uděláte, Live Unit Testing bude dynamicky pokračovat v testování kódu.

Chcete-li rozšíření pokrytí kódu k `StartsWithLower` metodě, postupujte následovně:

1. `TestStartsWithLower` `TestDoesNotStartWithLower` Do souboru zdrojového kódu testu projektu přidejte následující metody a:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Upravte `DirectCallWithNullOrEmpty` metodu přidáním následujícího kódu hned za volání [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing automaticky spouští nové a upravené testy při úpravě zdrojového kódu. Jak ukazuje následující obrázek, všechny testy, včetně dvou přidaných a těch, které jste změnili, byly úspěšné.

   ::: moniker range="vs-2017"
   ![Průzkumník testů po rozšíření pokrytí testu](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Live Test Explorer po rozšíření pokrytí testu](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. Přepněte do okna, které obsahuje zdrojový kód pro třídu StringLibrary. Live Unit Testing nyní ukazuje, že naše pokrytí kódu je rozšířeno na `StartsWithLower` metodu.

    ![Pokrytí kódu pro metodu StartsWithLower](media/lut-start/lut-extended-cs.png)

V některých případech mohou být úspěšné testy v **Průzkumníku testů** zobrazeny šedě. To znamená, že právě probíhá test, nebo že test ještě nebyl spuštěn, protože nebyly provedeny žádné změny kódu, které by ovlivnily test od posledního spuštění.

Zatím všechny naše testy byly úspěšné. V další části se podíváme, jak můžete zpracovat selhání testu.

## <a name="handle-a-test-failure"></a>Zpracování selhání testu

V této části se seznámíte s tím, jak můžete pomocí Live Unit Testing identifikovat, řešit potíže a řešit selhání testů. Provedete to tak, že rozbalíte pokrytí testu do `HasEmbeddedSpaces` metody.

1. Do testovacího souboru přidejte následující metodu:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Když se test spustí, Live Unit Testing označuje, že `TestHasEmbeddedSpaces` metoda se nezdařila, jak ukazuje následující obrázek:

   ::: moniker range="vs-2017"
   ![Průzkumník testů, který hlásí neúspěšný test](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Aplikace Live Test Explorer vykazující neúspěšný test](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Vyberte okno, které zobrazí kód knihovny. Live Unit Testing rozšířila pokrytí kódu k `HasEmbeddedSpaces` metodě. Také hlásí selhání testu přidáním červeného " 🞩 " na řádky, které jsou pokryty neúspěšnými testy.

1. Najeďte myší na řádek s `HasEmbeddedSpaces` podpisem metody. Live Unit Testing zobrazí popis, který hlásí, že je metoda předmětem jednoho testu, jak ukazuje následující obrázek:

   ![Live Unit Testing informace o neúspěšném testu](media/lut-start/test-failure-info-cs.png)

1. Vyberte **TestHasEmbeddedSpaces** test, který selhal. Live Unit Testing poskytuje několik možností, jako je například spuštění všech testů a ladění všech testů, jak je znázorněno na následujícím obrázku:

   ::: moniker range="vs-2017"
   ![Možnosti Live Unit Testing pro neúspěšný test](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Možnosti Live Unit Testing pro neúspěšný test](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Vyberte **ladit vše** pro ladění neúspěšného testu.

1. Visual Studio provede test v režimu ladění.

   Test přiřadí každému řetězci v poli proměnnou s názvem `phrase` a předá ji `HasEmbeddedSpaces` metodě. Spuštění programu pozastaví a vyvolá ladicí program při prvním vyhodnocení výrazu Assert `false` . Dialogové okno výjimky, které je výsledkem neočekávané hodnoty ve [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) volání metody, je znázorněno na následujícím obrázku.

   ![Dialogové okno výjimky Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   Kromě toho jsou k dispozici všechny ladicí nástroje, které poskytuje Visual Studio, aby nám pomohl vyřešit náš neúspěšný test, jak je znázorněno na následujícím obrázku:

   ![Nástroje pro ladění sady Visual Studio](media/lut-start/debugging-tools-cs.png)

   Všimněte si, že v okně **Automatické** hodnoty `phrase` je hodnota proměnné "Name\tDescription", což je druhý prvek pole. Testovací metoda očekává `HasEmbeddedSpaces` , že se vrátí, `true` když je tento řetězec předán, namísto toho vrátí `false` . Zjevně nerozpozná "\t", znak tabulátoru jako vložené místo.

1. Vyberte   >  **pokračovat** v ladění, stiskněte klávesu **F5** nebo klikněte na tlačítko **pokračovat** na panelu nástrojů a pokračujte v provádění testovacího programu. Protože došlo k neošetřené výjimce, test skončí.
To poskytuje dostatek informací pro předběžné šetření chyby. Buď `TestHasEmbeddedSpaces` (testovací rutina) vytvořil nesprávný předpoklad, nebo `HasEmbeddedSpaces` nerozpozná správně všechny vložené mezery.

1. Chcete-li problém diagnostikovat a opravit, začněte `StringLibrary.HasEmbeddedSpaces` metodou. Podívejte se na porovnání v `HasEmbeddedSpaces` metodě. Považuje se za vložené místo U + 0020. Standard Unicode ale obsahuje řadu dalších znakových mezer. To naznačuje, že kód knihovny byl nesprávně testován pro prázdný znak.

1. Nahraďte porovnání rovnosti voláním <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing automaticky znovu spustí testovací metodu, která se nezdařila.

   Live Unit Testing zobrazí aktualizované výsledky, které se také zobrazí v okně Editor kódu.

## <a name="see-also"></a>Viz také

- [Live Unit Testing v aplikaci Visual Studio](live-unit-testing.md)
- [Live Unit Testing nejčastějších dotazech](live-unit-testing-faq.md)
