---
title: Naučte se testovat kód pomocí živého testování částí
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 748dfc592fbf7a3b9737e9f418362067b92bb8ff
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594289"
---
# <a name="get-started-with-live-unit-testing"></a>Začínáme s funkcí Live Unit Testing

Pokud povolíte Live Unit Testing v řešení sady Visual Studio, vizuálně znázorňuje pokrytí testu a stav testů. Live Unit Testing také dynamicky spouští testy vždy, když upravíte kód a okamžitě vás upozorní, když vaše změny způsobí selhání testů.

Live Unit Testing lze použít k testování řešení, která cílí na .NET Framework nebo .NET Core. V tomto kurzu se naučíte používat Live Unit Testing vytvořením jednoduché knihovny tříd, která cílí na .NET Standard a vytvoříte projekt MSTest, který cílí na .NET Core pro otestování.

Kompletní řešení C# si můžete stáhnout z [MicrosoftDocs/Visual Studio docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) úložišti na Githubu.

## <a name="prerequisites"></a>Požadavky

Tento kurz vyžaduje, abyste nainstalovali edici Visual Studio Enterprise s využitím úlohy **vývoje .NET Core pro různé platformy** .

## <a name="create-the-solution-and-the-class-library-project"></a>Vytvoření řešení a projekt knihovny tříd

Začněte vytvořením řešení sady Visual Studio s názvem UtilityLibraries, které se skládá z jednoho .NET Standard projektu knihovny tříd StringLibrary.

Řešením je kontejner pro jeden nebo více projektů. Chcete-li vytvořit prázdné řešení, otevřete aplikaci Visual Studio a proveďte následující kroky:

1. Vyberte **souboru** > **nový** > **projektu** z nejvyšší úrovně nabídky sady Visual Studio.

1. Do vyhledávacího pole šablony zadejte **řešení** a pak vyberte šablonu **prázdného řešení** .

   ::: moniker range="vs-2017"

   ![** Dialogového okna Nový projekt **](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Dokončete vytváření řešení.

Teď, když jste vytvořili řešení, vytvoříte knihovnu tříd s názvem StringLibrary, která obsahuje řadu metod rozšíření pro práci s řetězci.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení UtilityLibraries a vyberte **Přidat** > **Nový projekt**.

::: moniker range="vs-2017"

2. V **přidat nový projekt** dialogového okna, vyberte jazyka C# uzlu, pak vyberte **.NET Standard**.

   > [!NOTE]
   > Vzhledem k tomu, že naše knihovna cílí .NET Standard spíše než konkrétní implementace rozhraní .NET, může být volána z jakékoli implementace rozhraní .NET, která podporuje tuto verzi .NET Standard. Další informace najdete v tématu [.NET Standard](/dotnet/standard/net-standard).

3. V pravém podokně vyberte šablonu **Knihovna tříd (.NET Standard)** a do textového pole **název** zadejte **StringLibrary** , jak ukazuje následující obrázek:

   ![** Přidat nový projekt ** dialogového okna](./media/lut-start/add-project-cs.png)

4. Vyberte **OK** pro vytvoření projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Do vyhledávacího pole šablony zadejte **knihovny tříd** a vyberte šablonu **knihovna tříd (.NET Standard)** . Klikněte na **Další**.

   > [!NOTE]
   > Vzhledem k tomu, že naše knihovna cílí .NET Standard spíše než konkrétní implementace rozhraní .NET, může být volána z jakékoli implementace rozhraní .NET, která podporuje tuto verzi .NET Standard. Další informace najdete v tématu [.NET Standard](/dotnet/standard/net-standard).

3. Pojmenujte projekt **StringLibrary**.

4. Kliknutím na **vytvořit** vytvořte projekt.

::: moniker-end

5. Všechny existující kód v okně kódu nahraďte následujícím kódem:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary má tři statické metody:

   - `StartsWithUpper` Vrátí `true` Pokud řetězec začíná velkým písmenem; v opačném případě vrátí `false`.

   - `StartsWithLower`Vrátí `true` Pokud řetězec začíná znakem znak malého písmene; v opačném případě vrátí `false`.

   - `HasEmbeddedSpaces` Vrátí `true` řetězec obsahuje vložený prázdný znak; v opačném případě vrátí `false`.

6. Vyberte **sestavení** > **sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio. Sestavení by mělo být úspěšné.

## <a name="create-the-test-project"></a>Vytvořte projekt testu

Dalším krokem je vytvoření projektu testu jednotek pro otestování knihovny StringLibrary. Vytvořte jednotkové testy podle následujících kroků:

1. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení UtilityLibraries a vyberte **Přidat** > **Nový projekt**.

::: moniker range="vs-2017"

2. V **přidat nový projekt** dialogového okna, vyberte jazyka C# uzlu, pak vyberte **.NET Core**.

   > [!NOTE]
   > Není nutné pro psaní jednotkových testů ve stejném jazyce jako knihovnu tříd.

3. V pravém podokně vyberte šablonu **projekt testů jednotek (.NET Core)** a do textového pole **název** zadejte **StringLibraryTests** , jak ukazuje následující obrázek:

   ![** Dialogové okno Přidat nový projekt ** pro projekt testování částí](./media/lut-start/add-unit-test-cs.png)

4. Vyberte **OK** pro vytvoření projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Do vyhledávacího pole šablony zadejte **test jednotek** a vyberte šablonu **projekt testování částí (.NET Core)** . Klikněte na **Další**.

3. Pojmenujte projekt **StringLibraryTests**.

4. Kliknutím na **vytvořit** vytvořte projekt.

::: moniker-end

   > [!NOTE]
   > Tento úvodní kurz používá Live Unit Testing s testovací rozhraní MSTest. Můžete také použít xUnit a NUnit testovacích architektur.

5. Projekt testu jednotek nelze přistoupit, automaticky knihovny tříd, který je testování. Udělit přístup ke knihovně testu tak, že přidáte odkaz na projekt knihovny tříd. Chcete-li to provést, klikněte pravým tlačítkem na `StringLibraryTests` projektu a vyberte **přidat** > **odkaz**. V dialogovém okně **Správce odkazů** se ujistěte, že je vybraná karta **řešení** , a vyberte projekt StringLibrary, jak je znázorněno na následujícím obrázku.

   ![** Správce odkaz ** dialogového okna](./media/lut-start/add-reference.png)

6. Nahraďte často používaný kód testu jednotek poskytovanou šablonou následujícím kódem:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Uložte projekt tak, že vyberete **Uložit** ikonu na panelu nástrojů.

8. Vzhledem k tomu, že kód testu jednotek obsahuje několik znaků, které nejsou ASCII, Visual Studio zobrazí následující dialog, který upozorňuje na to, že některé znaky budou ztraceny, pokud soubor uložíte ve výchozím formátu ASCII. Zvolte **uložit s kódováním ostatní** tlačítko.

   ![Zvolte kódování souboru](media/lut-start/ascii-encoding.png)

9. V rozevíracím seznamu **kódování** v dialogovém okně **možnosti uložení zálohy** vyberte možnost **Unicode (UTF-8 bez podpisu)-znaková stránka 65001**, jak ukazuje následující obrázek:

   ![Výběr kódování UTF-8](media/lut-start/utf8-encoding.png)

10. Zkompilujte projekt jednotkového testu výběrem **sestavení** > **znovu sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio.

Pro něj jste vytvořili knihovnu tříd, jakož i některá testování částí. Nyní jste dokončili nezbytné úkony, které aplikace potřebovala použít Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Povolte Live Unit Testing

Zatím i když jste napsali testy pro knihovnu tříd StringLibrary, neudělali jste je. Live Unit Testing je spouští automaticky jakmile ho povolíte. Chcete-li to mohli udělat, postupujte takto:

1. Volitelně můžete vybrat okno kódu, které obsahuje kód pro StringLibrary. Je to *Class1.cs* pro projekt C# nebo *Class1.vb* pro projekt jazyka Visual Basic. (Tento krok vám umožní vizuální kontrolu výsledku testů a rozsahu pokrytí kódu, když povolíte Live Unit Testing.)

1. Vyberte **testovací** > **Live Unit Testing** > **Start** z nejvyšší úrovně nabídky sady Visual Studio.

1. Testování jednotek za provozu, který se automaticky spouští všechny testy se spustí aplikace Visual Studio.

Po dokončení spouštění vašich testů **Průzkumník testů** zobrazí celkové výsledky a výsledky jednotlivých testů. Kromě toho okna kódu graficky zobrazuje pokrytí kódu testu a výsledky testů. Jak ukazuje následující obrázek, všechny tři testy byly úspěšně provedeny. Profil také ukazuje, že naše testy pokryli ve všech cestách kódu. `StartsWithUpper` metoda a všechny testy úspěšně spuštěn (která je zobrazena zelená značka zaškrtnutí, "✓"). Nakonec ukazuje, že žádná z ostatních metod v StringLibrary nemá pokrytí kódu (což je označeno modrou čárou "➖").

![Okna Průzkumníka testů a kódu po spuštění Live Unit testing](media/lut-start/lut-results-cs.png)

Můžete také získáte podrobnější informace o testovací pokrytí a výsledky testu tak, že vyberete ikonu pokrytí kódu v okně kódu. Prozkoumat těchto podrobných informací, postupujte takto:

1. Klikněte na zelené zaškrtnutí na řádku, který čte `if (String.IsNullOrWhiteSpace(s))` v `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing uvádí, že tři testy pokrývají tento řádek kódu a všechny byly úspěšně provedeny.

   ![Pokrytí kódu pro podmíněný příkaz "if"](media/lut-start/code-coverage-cs1.png)

1. Klikněte na zelené zaškrtnutí na řádku, který čte `return Char.IsUpper(s[0])` v `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing označuje, že pouze dva testy pokrývají tento řádek kódu a všechny byly úspěšně provedeny.

   ![Pokrytí kódu pro příkaz return](media/lut-start/code-coverage-cs2.png)

Hlavní problém, který identifikuje Live Unit Testing je pokrytí kódu neúplné. Budete ho vyřešit v další části.

## <a name="expand-test-coverage"></a>Rozbalte pokrytí testu

V této části budete rozšíření testování částí a `StartsWithLower` metody. Když to uděláte, Live Unit Testing dynamicky budou k testování kódu.

K rozšíření pokrytí kódu `StartsWithLower` metodu, postupujte takto:

1. Přidejte následující `TestStartsWithLower` a `TestDoesNotStartWithLower` metody do souboru se zdrojovým kódem projektu testu:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Upravit `DirectCallWithNullOrEmpty` metoda přidáním následujícího kódu ihned po volání [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing automaticky provádí nové a změněné testy, když upravíte zdrojového kódu. Jak ukazuje následující obrázek **Průzkumníka testů** , všechny testy, včetně dvou přidaných a těch, které jste změnili, byly úspěšné.

   ![Průzkumník testů po rozšíření pokrytí testu](media/lut-start/test-dynamic.png)

1. Přepněte do okna, které obsahuje zdrojový kód pro třídu StringLibrary. Teď zobrazují, které je rozšířit naše pokrytí kódu pro Live Unit Testing `StartsWithLower` metody.

    ![Pokrytí kódu pro metodu StartsWithLower](media/lut-start/lut-extended-cs.png)

V některých případech mohou být úspěšné testy v **Průzkumníku testů** zobrazeny šedě. To znamená, že právě probíhá test, nebo že test ještě nebyl spuštěn, protože nebyly provedeny žádné změny kódu, které by ovlivnily test od posledního spuštění.

Zatím všechny naše testy proběhly úspěšně. V další části prozkoumáme, jak můžete zpracovávat selhání testu.

## <a name="handle-a-test-failure"></a>Zpracování selhání testu

V této části budete prozkoumávat, jak vám pomůže Live Unit Testing identifikovat, řešení potíží a řešit selhání testů. Provedete to tak, že rozbalíte pokrytí testu pro `HasEmbeddedSpaces` metody.

1. Přidejte následující metodu do souboru testu:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Když se test spustí, Live Unit Testing označuje, že metoda `TestHasEmbeddedSpaces` se nezdařila, jak ukazuje následující obrázek:

   ![Průzkumník testů, který hlásí neúspěšný test](media/lut-start/test-failure.png)

1. Vyberte okno zobrazující kód knihovny. Live Unit Testing rozšířila pokrytí kódu k metodě `HasEmbeddedSpaces`. Také oznámí selhání testu tak, že přidáte červený "🞩" na řádky, které jsou předmětem selhání testů.

1. Najeďte myší na řádek s `HasEmbeddedSpaces` podpis metody. Live Unit Testing zobrazí popis, který oznamuje, že se metoda zabývá jedním testem, jak ukazuje následující obrázek:

   ![Live Unit Testing informace o neúspěšném testu](media/lut-start/test-failure-info-cs.png)

1. Vyberte neúspěšný **TestHasEmbeddedSpaces** testování. Live Unit Testing poskytuje celou řadu možností, jako je například spuštění všech testů, spuštění vybraných testů, ladění všech testů a ladění vybraných testů, jak ukazuje následující obrázek:

   ![Možnosti Live Unit Testing pro neúspěšný test](media/lut-start/test-failure-options.png)

1. Vyberte **ladit vybrané** k ladění selhání testu.

1. Visual Studio test spustí v režimu ladění.

   Test přiřadí každému řetězci v poli proměnnou s názvem `phrase` a předá ji metodě `HasEmbeddedSpaces`. Pozastaví provádění programu a vyvolá ladicí program první čas je výrazu assert `false`. Dialogové okno výjimky, které je výsledkem neočekávané hodnoty ve volání metody [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) , je znázorněno na následujícím obrázku.

   ![Dialogové okno výjimky Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   Kromě toho jsou k dispozici všechny ladicí nástroje, které poskytuje Visual Studio, aby nám pomohl vyřešit náš neúspěšný test, jak je znázorněno na následujícím obrázku:

   ![Nástroje pro ladění sady Visual Studio](media/lut-start/debugging-tools-cs.png)

   Poznámka: v **automatické hodnoty** okno, která hodnota `phrase` proměnná je "Name\tDescription", což je druhý prvek pole. Testovací metoda očekává, že `HasEmbeddedSpaces` vrátit `true` když je jí předán tento řetězec; místo toho vrátí `false`. Je zřejmé nerozpozná "\t", znak tabulátoru jako vložené místo.

1. Vyberte **ladění** > **pokračovat**, stiskněte klávesu **F5**, nebo klikněte na tlačítko **pokračovat** tlačítko na panelu nástrojů má pokračovat provedením Otestujte aplikaci. Protože došlo k neošetřené výjimce, test se ukončí.
To poskytuje dostatek informací pro předběžné šetření chyby. Buď `TestHasEmbeddedSpaces` (rutina testu) provedené nesprávné předpokladů, nebo `HasEmbeddedSpaces` nerozpozná správně všechny vložené mezery.

1. Chcete-li problém diagnostikovat a opravit, začněte s metodou `StringLibrary.HasEmbeddedSpaces`. Podívejte se na porovnání v `HasEmbeddedSpaces` metody. Vložené místo jako U + 0020 vyhodnotí. Unicode Standard však zahrnuje celou řadou dalších znaky. To naznačuje, že kód knihovny obsahuje nesprávně testovány z hlediska prázdným znakem.

1. Porovnání rovnosti nahraďte volání <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing automaticky znovu spustí neúspěšnou zkušební metodu a aktualizuje výsledky v okně Code (kód) a v **Průzkumníku testů**, jak ukazuje následující obrázek:

    ![Úspěšný HasEmbeddedSpaces test](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Viz také:

- [Live Unit Testing v sadě Visual Studio](live-unit-testing.md)
- [Live Unit Testing – nejčastější dotazy](live-unit-testing-faq.md)
