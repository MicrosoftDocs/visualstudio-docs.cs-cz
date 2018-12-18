---
title: Zjistěte, jak testovat kód pomocí Live 2017 Test jednotek | Dokumentace Microsoftu
ms.date: 08/31/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 8908b592283f81d8c60a2adb93c12af3f5e61ba7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056782"
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Začínáme s Live Unit Testing v sadě Visual Studio

Když povolíte Live Unit Testing v řešení sady Visual Studio, Live Unit Testing znázorňuje vizuální stav testů a pokrytí testu. Také dynamicky provádí testy kdykoli upravit kód a okamžitě vás upozorní, když změny způsobit selhání testů.

Live Unit Testing je možné pro testování řešení, které jsou cíleny rozhraní .NET Framework nebo .NET Core. V tomto kurzu se naučíte používat Live Unit Testing tak, že vytvoříte jednoduchou třídu knihovny, který cílí na .NET Standard a vytvoříte projekt MSTest, který cílí na .NET Core a otestovat ho.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
Kompletní řešení C# si můžete stáhnout z [MicrosoftDocs/Visual Studio docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) úložišti na Githubu.
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
Kompletní řešení jazyka Visual Basic si můžete stáhnout z [MicrosoftDocs/Visual Studio docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) úložišti na Githubu.

---

## <a name="prerequisites"></a>Požadavky

Tento kurz vyžaduje, že jste nainstalovali Visual Studio 2017 Enterprise Edition verze 15.3 se funkcí .NET Core 2.0.

## <a name="create-the-solution-and-the-class-library-project"></a>Vytvoření řešení a projekt knihovny tříd

Začněte vytvořením řešení sady Visual Studio s názvem `UtilityLibraries` , který se skládá z jedné .NET Standard projekt knihovny tříd, `StringLibrary`. Můžete napsat `StringLibrary` v C# nebo Visual Basic.

Řešením je kontejner pro jeden nebo více projektů. Pokud chcete vytvořit řešení, otevřete Visual Studio 2017 a postupujte takto:

1. Vyberte **souboru** > **nový** > **projektu** z nejvyšší úrovně nabídky sady Visual Studio.

1. V **nový projekt** dialogového okna, rozbalte **ostatní typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**. Vyberte **prázdné řešení** šablony v pravém podokně a zadejte `UtilityLibraries` v **název** textového pole, jak ukazuje následující obrázek:

   ![** Dialogového okna Nový projekt **](./media/lut-start/new-solution.png)

1. Vyberte **OK** k vytvoření řešení.

Teď, když jsme vytvořili řešení, vytvoříte knihovny tříd s názvem `StringLibrary` , který obsahuje řadu rozšiřující metody pro práci s řetězci.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na `UtilityLibraries` řešení a vyberte **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogového okna, vyberte jazyka C# uzlu, pak vyberte **.NET Standard**.

   > [!NOTE]
   > Vzhledem k tomu, zaměřuje na naše knihovny .NET Standard spíše než konkrétní implementace rozhraní .NET, můžete volat z jakékoli implementace .NET, která podporuje danou verzi .NET Standard. Další informace najdete v tématu [.NET Standard](/dotnet/standard/net-standard).

1. Vyberte **knihovna tříd (.NET Standard)** šablony v pravém podokně a zadejte `StringLibrary` v **název** textového pole, jak ukazuje následující obrázek:

   ![** Přidat nový projekt ** dialogového okna](./media/lut-start/add-project-cs.png)

1. Vyberte **OK** pro vytvoření projektu.

1. Všechny existující kód v okně kódu nahraďte následujícím kódem:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` má tři statické metody:

      - `StartsWithUpper` Vrátí `true` Pokud řetězec začíná velkým písmenem; v opačném případě vrátí `false`.

      - `StartsWithLower`Vrátí `true` Pokud řetězec začíná znakem znak malého písmene; v opačném případě vrátí `false`.

      - `HasEmbeddedSpaces` Vrátí `true` řetězec obsahuje vložený prázdný znak; v opačném případě vrátí `false`.

1.  Vyberte **sestavení** > **sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio. Visual Studio by měl úspěšným sestavením své knihovny.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na `UtilityLibraries` řešení a vyberte **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogového okna, vyberte uzel Visual Basic a pak vyberte **.NET Standard**.

   > [!NOTE]
   > Vzhledem k tomu, zaměřuje na naše knihovny .NET Standard spíše než konkrétní implementace rozhraní .NET, můžete volat z jakékoli implementace .NET, která podporuje danou verzi .NET Standard. Další informace najdete v tématu [.NET Standard](/dotnet/standard/net-standard).

1. Vyberte **knihovna tříd (.NET Standard)** šablony v pravém podokně a zadejte `StringLibrary` v **název** textového pole, jak ukazuje následující obrázek:

   ![** Přidat nový projekt ** dialogového okna](./media/lut-start/add-project-vb.png)

1. Vyberte **OK** pro vytvoření projektu.

1. Všechny existující kód v okně kódu nahraďte následujícím kódem:

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` má tři statické metody:

      - `StartsWithUpper` Vrátí `true` Pokud řetězec začíná velkým písmenem; v opačném případě vrátí `false`.

      - `StartsWithLower`Vrátí `true` Pokud řetězec začíná znakem znak malého písmene; v opačném případě vrátí `false`.

      - `HasEmbeddedSpaces` Vrátí `true` řetězec obsahuje vložený prázdný znak; v opačném případě vrátí `false`.

1. Klikněte pravým tlačítkem na projekt StringLibrary v **Průzkumníka řešení** a vyberte **vlastnosti**. V **aplikace** kartu, odstraníte tím stávající text v **kořenový obor názvů** textového pole, jak ukazuje následující obrázek. Kořenový obor názvů je definován [příkaz Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement) ve zdrojovém kódu.

   ![Dialogové okno Vlastnosti projektu pro projekt jazyka Visual Basic](./media/lut-start/vb-properties.png)

1.  Vyberte **sestavení** > **sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio. Visual Studio by měl úspěšným sestavením své knihovny.

---

## <a name="create-the-test-project"></a>Vytvořte projekt testu

Dalším krokem je vytvoření projektu testování částí pro testování `StringLibrary` knihovny. Vytvořte jednotkové testy podle následujících kroků:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na `UtilityLibraries` řešení a vyberte **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogového okna, vyberte jazyka C# uzlu, pak vyberte **.NET Core**.

   > [!NOTE]
   > Není nutné pro psaní jednotkových testů ve stejném jazyce jako knihovnu tříd.

1. Vyberte **projekt testu jednotek (.NET Core)** šablony v pravém podokně a zadejte `StringLibraryTests` v **název** textového pole, jak ukazuje následující obrázek:

   ![** Dialogové okno Přidat nový projekt ** pro projekt testování částí](./media/lut-start/add-unit-test-cs.png)

1. Vyberte **OK** pro vytvoření projektu.

   > [!NOTE]
   > Tento úvodní kurz používá Live Unit Testing s testovací rozhraní MSTest. Můžete také použít xUnit a NUnit testovacích architektur.

1. Projekt testu jednotek nelze přistoupit, automaticky knihovny tříd, který je testování. Udělit přístup ke knihovně testu tak, že přidáte odkaz na projekt knihovny tříd. Chcete-li to provést, klikněte pravým tlačítkem na `StringLibraryTests` projektu a vyberte **přidat** > **odkaz**. V **správce odkazů** dialogového okna, ujistěte se, že **řešení** karta je vybraný a vyberte `StringLibrary` projektu, jak je znázorněno na následujícím obrázku.

   ![** Správce odkaz ** dialogového okna](./media/lut-start/add-reference.png)

1. Nahraďte často používaný kód testu jednotek poskytovanou šablonou následujícím kódem:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. Uložte projekt tak, že vyberete **Uložit** ikonu na panelu nástrojů.

1. Testování jednotek kódu obsahuje některé jiné znaky než ASCII, Visual Studio zobrazí následující dialogové okno nás upozornit, že některé znaky budou ztraceny, pokud jsme soubor uložte ve formátu ASCII jeho výchozí. Zvolte **uložit s kódováním ostatní** tlačítko.

   ![Zvolte kódování souboru](media/lut-start/ascii-encoding.png)

1. V **kódování** rozevírací seznam **možnosti ukládání záloh** dialogovém okně zvolte **kódování Unicode (UTF-8 bez podpisu) - znaková stránka 65001**, jak je vidět na následujícím obrázku:

   ![Výběr kódování UTF-8](media/lut-start/utf8-encoding.png)

1. Zkompilujte projekt jednotkového testu výběrem **sestavení** > **znovu sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na `UtilityLibraries` řešení a vyberte **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogového okna, vyberte uzel Visual Basic a pak vyberte **.NET Core**.

   > [!NOTE]
   > Není nutné pro psaní jednotkových testů ve stejném jazyce jako knihovnu tříd.

1. Vyberte **projekt testu jednotek (.NET Core)** šablony v pravém podokně a zadejte `StringLibraryTests` v **název** textového pole, jak ukazuje následující obrázek:

   ![** Dialogové okno Přidat nový projekt ** pro testování částí](./media/lut-start/add-unit-test-vb.png)

1. Vyberte **OK** pro vytvoření projektu.

   > [!NOTE]
   > Tento úvodní kurz používá Live Unit Testing s testovací rozhraní MSTest. Můžete také použít xUnit a NUnit testovacích architektur.

1. Projekt testu jednotek nelze přistoupit, automaticky knihovny tříd, který je testování. Udělit přístup ke knihovně testu tak, že přidáte odkaz na projekt knihovny tříd. Chcete-li to provést, klikněte pravým tlačítkem na `StringLibraryTests` projektu a vyberte **přidat** > **odkaz**. V **správce odkazů** dialogového okna, ujistěte se, že **řešení** karta je vybraný a vyberte `StringLibrary` projektu, jak je znázorněno na následujícím obrázku.

   ![** Správce odkaz ** dialogového okna](./media/lut-start/add-reference.png)

1. Nahraďte často používaný kód testu jednotek poskytovanou šablonou následujícím kódem:

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. Uložte projekt tak, že vyberete **Uložit** ikonu na panelu nástrojů.

1. Testování jednotek kódu obsahuje některé jiné znaky než ASCII, Visual Studio zobrazí následující dialogové okno nás upozornit, že některé znaky budou ztraceny, pokud jsme soubor uložte ve formátu ASCII jeho výchozí. Zvolte **uložit s kódováním ostatní** tlačítko.

   ![Zvolte kódování souboru](media/lut-start/ascii-encoding.png)

1. V **kódování** rozevírací seznam **možnosti ukládání záloh** dialogovém okně zvolte **kódování Unicode (UTF-8 bez podpisu) - znaková stránka 65001**, jak je vidět na následujícím obrázku:

   ![Výběr kódování UTF-8](media/lut-start/utf8-encoding.png)

1. Kompilace projektu testování částí pomocí **sestavení** > **znovu sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio.

---

Pro něj jste vytvořili knihovnu tříd, jakož i některá testování částí. Nyní jste dokončili nezbytné úkony, které aplikace potřebovala použít Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Povolte Live Unit Testing

Míry, i když jste napsali testy pro `StringLibrary` knihovny tříd, které neprovedly je. Live Unit Testing je spouští automaticky jakmile ho povolíte. Chcete-li to mohli udělat, postupujte takto:

1. Volitelně vyberte okno kódu, který obsahuje kód pro `StringLibrary`. Je to *Class1.cs* pro projekt C# nebo *Class1.vb* pro projekt jazyka Visual Basic. (Tento krok vám umožní vizuálně zkoumat výsledků testů a rozsah pokrytí kódu, jakmile povolíte Live Unit Testing.)

1. Vyberte **testovací** > **Live Unit Testing** > **Start** z nejvyšší úrovně nabídky sady Visual Studio.

1. Testování jednotek za provozu, který se automaticky spouští všechny testy se spustí aplikace Visual Studio.

Po dokončení spouštění vašich testů **Průzkumník testů** zobrazí celkové výsledky a výsledky jednotlivých testů. Kromě toho okna kódu graficky zobrazuje pokrytí kódu testu a výsledky testů. Jak ukazuje následující obrázek, všechny tři testy proběhlo úspěšně. Profil také ukazuje, že naše testy pokryli ve všech cestách kódu. `StartsWithUpper` metoda a všechny testy úspěšně spuštěn (která je zobrazena zelená značka zaškrtnutí, "✓"). A konečně, který ukazuje, že žádné z ostatních metod v `StringLibrary` mají pokrytí kódu (což je indikován modrá čára "➖").

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Okna Průzkumníka testů a kódu po spuštění Live Unit testing](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Okna Průzkumníka testů a kódu po spuštění Live Unit testing](media/lut-start/lut-results-vb.png)

---

Můžete také získáte podrobnější informace o testovací pokrytí a výsledky testu tak, že vyberete ikonu pokrytí kódu v okně kódu. Prozkoumat těchto podrobných informací, postupujte takto:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Klikněte na zelené zaškrtnutí na řádku, který čte `if (String.IsNullOrWhiteSpace(s))` v `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing označuje, že tři testy zahrnují tento řádek kódu a, že všechny uzavřeli dohodu o úspěšně.

   ![Pokrytí kódu pro podmíněný příkaz "if"](media/lut-start/code-coverage-cs1.png)

1. Klikněte na zelené zaškrtnutí na řádku, který čte `return Char.IsUpper(s[0])` v `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing označuje, že pouze dva testy zahrnují tento řádek kódu a že všechny uzavřeli dohodu o úspěšně.

   ![Pokrytí kódu pro příkaz return](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Klikněte na zelené zaškrtnutí na řádku, který čte `If (String.IsNullOrWhiteSpace(s)) Then` v `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing označuje, že tři testy zahrnují tento řádek kódu a, že všechny uzavřeli dohodu o úspěšně.

   ![Pokrytí kódu pro podmíněný příkaz "If"](media/lut-start/code-coverage-vb1.png)

1. Klikněte na zelené zaškrtnutí na řádku, který čte `Return Char.IsUpper(s(0))` v `StartsWithUpper` metody. Jak ukazuje následující obrázek, Live Unit Testing označuje, že pouze dva testy zahrnují tento řádek kódu a že všechny uzavřeli dohodu o úspěšně.

   ![Pokrytí kódu pro příkaz return](media/lut-start/code-coverage-vb2.png)

---

Hlavní problém, který identifikuje Live Unit Testing je pokrytí kódu neúplné. Budete ho vyřešit v další části.

## <a name="expand-test-coverage"></a>Rozbalte pokrytí testu

V této části budete rozšíření testování částí a `StartsWithLower` metody. Když to uděláte, Live Unit Testing dynamicky budou k testování kódu.

K rozšíření pokrytí kódu `StartsWithLower` metodu, postupujte takto:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Přidejte následující `TestStartsWithLower` a `TestDoesNotStartWithLower` metody do souboru se zdrojovým kódem projektu testu:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Upravit `DirectCallWithNullOrEmpty` metoda přidáním následujícího kódu ihned po volání [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing automaticky provádí nové a změněné testy, když upravíte zdrojového kódu. Jako na následujícím obrázku z **Průzkumník testů** ukazuje, všechny testy, včetně dvou jste přidali a ten, který jste upravili, proběhlo úspěšně.

   ![Průzkumník testů po rozbalení pokrytí testu.](media/lut-start/test-dynamic.png)

1. Přepněte do okna, který obsahuje zdrojový kód `StringLibrary` třídy. Teď zobrazují, které je rozšířit naše pokrytí kódu pro Live Unit Testing `StartsWithLower` metody.

    ![Pokrytí kódu pro metodu StartsWithLower](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Přidejte následující `TestStartsWithLower` a `TestDoesNotStartWithLower` metody do souboru se zdrojovým kódem projektu testu:

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Upravit `DirectCallWithNullOrEmpty` metoda přidáním následujícího kódu ihned po volání [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Live Unit Testing automaticky provádí nové a změněné testy, když upravíte zdrojového kódu. Jako na následujícím obrázku z **Průzkumník testů** ukazuje, všechny testy, včetně dvou jste přidali a ten, který jste upravili, proběhlo úspěšně.

   ![Průzkumník testů po rozbalení pokrytí testu.](media/lut-start/test-dynamic.png)

1. Přepněte do okna, který obsahuje zdrojový kód `StringLibrary` třídy. Teď zobrazují, které je rozšířit naše pokrytí kódu pro Live Unit Testing `StartsWithLower` metody.

    ![Pokrytí kódu pro StartsWithLower](media/lut-start/lut-extended-vb.png)

---

V některých případech úspěšných testů v **Průzkumník testů** může být šedě. Který označuje, že test právě probíhá, nebo, že test nebyl znovu spustit, protože byly změny žádný kód, který by ovlivnily test od poslední spuštění.

Zatím všechny naše testy proběhly úspěšně. V další části prozkoumáme, jak můžete zpracovávat selhání testu.

## <a name="handle-a-test-failure"></a>Zpracování selhání testu

V této části budete prozkoumávat, jak vám pomůže Live Unit Testing identifikovat, řešení potíží a řešit selhání testů. Provedete to tak, že rozbalíte pokrytí testu pro `HasEmbeddedSpaces` metody.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Přidejte následující metodu do souboru testu:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Když je spuštěn test, Live Unit Testing znamená, že `TestHasEmbeddedSpaces` metody se nezdařila, jak ukazuje následující obrázek:

   ![Průzkumník testů reporting selhání testu.](media/lut-start/test-failure.png)

1. Vyberte okno zobrazující kód knihovny. Všimněte si, že Live Unit Testing se rozšířila pokrytí kódu `HasEmbeddedSpaces` metody. Také oznámí selhání testu tak, že přidáte červený "🞩" na řádky, které jsou předmětem selhání testů.

1. Najeďte myší na řádek s `HasEmbeddedSpaces` podpis metody. Live Unit Testing zobrazí popisek, který bude hlásit, že metoda je popsaná v jeden test, jak ukazuje následující obrázek:

   ![Live Unit Testing informace o selhání testu.](media/lut-start/test-failure-info-cs.png)

1. Vyberte neúspěšný **TestHasEmbeddedSpaces** testování. Všimněte si, že zobrazuje Live Unit Testing poskytuje řadu možností, jako je spuštění všech testů, spuštění testů, vyberte možnost, všechny testy ladění a ladění vybrané testy, jako na následujícím obrázku:

   ![Live Unit Testing možnosti pro selhání testu.](media/lut-start/test-failure-options.png)

1. Vyberte **ladit vybrané** k ladění selhání testu.

1. Visual Studio test spustí v režimu ladění. Testovacím přiřadí proměnné s názvem každý řetězec v poli `phrase` a předává jej do `HasEmbeddedSpaces` metody. Pozastaví provádění programu a vyvolá ladicí program první čas je výrazu assert `false`. Dialogové okno výjimky, která je výsledkem Neočekávaná hodnota v [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) volání metody je znázorněno na následujícím obrázku.

   ![Live Unit Testing dialogové okno výjimky.](media/lut-start/exception-dialog-cs.png)

   Kromě toho všechny ladicí nástroje, které poskytuje Visual Studio je možné vyřešit naše neúspěšných testů, jak ukazuje následující obrázek:

   ![Ladicí nástroje Visual Studio.](media/lut-start/debugging-tools-cs.png)

   Poznámka: v **automatické hodnoty** okno, která hodnota `phrase` proměnná je "Name\tDescription", což je druhý prvek pole. Testovací metoda očekává, že `HasEmbeddedSpaces` vrátit `true` když je jí předán tento řetězec; místo toho vrátí `false`. Je zřejmé nerozpozná "\t", znak tabulátoru jako vložené místo.

1. Vyberte **ladění** > **pokračovat**, stiskněte klávesu **F5**, nebo klikněte na tlačítko **pokračovat** tlačítko na panelu nástrojů má pokračovat provedením Otestujte aplikaci. Protože došlo k neošetřené výjimce, test se ukončí.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Přidejte následující metodu do souboru testu:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Když je spuštěn test, Live Unit Testing znamená, že `TestHasEmbeddedSpaces` metody se nezdařila, jak ukazuje následující obrázek:

   ![Průzkumník testů reporting selhání testu.](media/lut-start/test-failure.png)

1. Vyberte okno zobrazující kód knihovny. Všimněte si, že Live Unit Testing se rozšířila pokrytí kódu `HasEmbeddedSpaces` metody. Také oznámí selhání testu tak, že přidáte červený "🞩" na řádky, které jsou předmětem selhání testů.

1. Najeďte myší na řádek s `HasEmbeddedSpaces` podpis metody. Live Unit Testing zobrazí popisek, který bude hlásit, že metoda je popsaná v jeden test, jak ukazuje následující obrázek:

   ![Live Unit Testing informace o selhání testu.](media/lut-start/test-failure-info-vb.png)

1. Vyberte neúspěšný **TestHasEmbeddedSpaces** testování. Všimněte si, že zobrazuje Live Unit Testing poskytuje řadu možností, jako je spuštění všech testů, spuštění vybraných testů, všechny testy ladění nebo ladění vybrané testy, jako na následujícím obrázku:

   ![Live Unit Testing možnosti pro selhání testu.](media/lut-start/test-failure-options.png)

1. Vyberte **ladit vybrané** k ladění selhání testu.

1. Visual Studio test spustí v režimu ladění. Testovacím přiřadí proměnné s názvem každý řetězec v poli `phrase` a předává jej do `HasEmbeddedSpaces` metody. Pozastaví provádění programu a vyvolá ladicí program první čas je výrazu assert `false`. Dialogové okno výjimky, která je výsledkem Neočekávaná hodnota v [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) volání metody je znázorněno na následujícím obrázku.

   ![Live Unit Testing dialogové okno výjimky.](media/lut-start/exception-dialog-vb.png)

   Kromě toho všechny ladicí nástroje, které poskytuje Visual Studio je možné vyřešit naše neúspěšných testů, jak ukazuje následující obrázek:

   ![Ladicí nástroje Visual Studio.](media/lut-start/debugging-tools-vb.png)

   Poznámka: v **automatické hodnoty** okno, která hodnota `phrase` proměnná je vbTab "Name" + "Popis", což je druhý prvek pole. Testovací metoda očekává, že `HasEmbeddedSpaces` vrátit `true` když je jí předán tento řetězec; místo toho vrátí `false`. Je zřejmé nerozpozná znak tabulátoru jako vložené místo.

1. Vyberte **ladění** > **pokračovat**, stiskněte klávesu **F5**, nebo klikněte na tlačítko **pokračovat** tlačítko na panelu nástrojů má pokračovat provedením Otestujte aplikaci. Protože došlo k neošetřené výjimce, test se ukončí.

---

To poskytuje dostatek informací pro předběžné šetření chyby. Buď `TestHasEmbeddedSpaces` (rutina testu) provedené nesprávné předpokladů, nebo `HasEmbeddedSpaces` nerozpozná správně všechny vložené mezery. Diagnostikovat a opravit problém, začínat `StringLibrary.HasEmbeddedSpaces` metody:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Podívejte se na porovnání v `HasEmbeddedSpaces` metody. Vložené místo jako U + 0020 vyhodnotí. Unicode Standard však zahrnuje celou řadou dalších znaky. To naznačuje, že kód knihovny obsahuje nesprávně testovány z hlediska prázdným znakem.

1. Porovnání rovnosti nahraďte volání <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing automaticky znovu spustí metodu neúspěšných testů a aktualizuje výsledky v okně kódu a v **Průzkumníka testů**, jak je vidět na následujícím obrázku:

    ![Úspěšné testovací HasEmbeddedSpaces.](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Podívejte se na porovnání v `HasEmbeddedSpaces` metody. Vložené místo jako U + 0020 vyhodnotí. Unicode Standard však zahrnuje celou řadou dalších znaky. To naznačuje, že kód knihovny obsahuje nesprávně testovány z hlediska prázdným znakem.

1. Porovnání rovnosti nahraďte volání <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing automaticky znovu spustí metodu neúspěšných testů a aktualizuje výsledky v okně kódu a v **Průzkumníka testů**, jak je vidět na následujícím obrázku:

    ![Úspěšné testovací HasEmbeddedSpaces.](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>Viz také:
- [Live Unit Testing v sadě Visual Studio](live-unit-testing.md)
- [Live Unit Testing – nejčastější dotazy](live-unit-testing-faq.md)
