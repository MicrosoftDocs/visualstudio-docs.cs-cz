---
title: Naučte se testovat kód pomocí Live Unit Test.
description: Naučte se používat Live Unit Testing vytvořením jednoduché knihovny tříd, která cílí na .NET Standard, a vytvořením projektu MSTest, který cílí na .NET Core a otestuje ho.
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
ms.openlocfilehash: 2270216e7245f20d26df580ad90dc627319adcc1
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798632"
---
# <a name="get-started-with-live-unit-testing"></a>Začínáme s funkcí Live Unit Testing

Když povolíte Live Unit Testing v Visual Studio řešení, vizuálně znázorňuje pokrytí testu a stav testů. Live Unit Testing také dynamicky provádí testy při každé úpravě kódu a okamžitě vás upozorní, když vaše změny způsobí selhání testů.

Live Unit Testing můžete použít k testování řešení, která cílí na .NET Framework nebo .NET Core. V tomto kurzu se naučíte používat Live Unit Testing vytvořením jednoduché knihovny tříd, která cílí na .NET Standard, a vytvoříte projekt MSTest, který cílí na .NET Core a otestuje ho.

Kompletní řešení v jazyce C# si můžete stáhnout z [úložiště MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) na GitHubu.

## <a name="prerequisites"></a>Požadavky

Tento kurz vyžaduje, že jste nainstalovali Visual Studio Enterprise edici s úlohou vývoj pro **různé platformy v .NET Core.**

## <a name="create-the-solution-and-the-class-library-project"></a>Vytvoření řešení a projektu knihovny tříd

Začněte vytvořením nového Visual Studio s názvem UtilityLibraries, které se skládá z jednoho .NET Standard knihovny tříd StringLibrary.

Řešení je jen kontejner pro jeden nebo více projektů. Pokud chcete vytvořit prázdné řešení, otevřete Visual Studio a proveďte následující:

1. V **nabídce** nejvyšší úrovně vyberte File  >  **New**  >  **Project** (Soubor Visual Studio projekt).

1. Do **vyhledávacího** pole šablony zadejte solution a pak vyberte **šablonu Prázdné** řešení. Projekt **pojmenováte UtilityLibraries**.

   ::: moniker range="vs-2017"

   ![Dialogové okno **Nový projekt**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Dokončete vytváření řešení.

Teď, když jste vytvořili řešení, vytvoříte knihovnu tříd s názvem StringLibrary, která obsahuje řadu rozšiřujících metod pro práci s řetězci.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení Utility (Nástroje) a vyberte Add New Project **(Přidat**  >  **nový projekt).**

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

   ```csharp
   using System;

   namespace UtilityLibraries
   {
       public static class StringLibrary
       {
           public static bool StartsWithUpper(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsUpper(s[0]);
           }

           public static bool StartsWithLower(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsLower(s[0]);
           }

           public static bool HasEmbeddedSpaces(this string s)
           {
               foreach (var ch in s.Trim())
               {
                   if (ch == ' ')
                       return true;
               }
               return false;
           }
       }
   }
   ```

   StringLibrary má tři statické metody:

   - `StartsWithUpper` Vrátí, `true` zda řetězec začíná velkým znakem. v opačném případě vrátí `false` .

   - `StartsWithLower`Vrátí, `true` zda řetězec začíná malým znakem. v opačném případě vrátí hodnotu `false` .

   - `HasEmbeddedSpaces` Vrátí, `true` zda řetězec obsahuje vložený prázdný znak. v opačném případě vrátí `false` .

6.   >  V nabídce aplikace Visual Studio nejvyšší úrovně vyberte **řešení** sestavení Build. Sestavení by mělo být úspěšné.

## <a name="create-the-test-project"></a>Vytvoření testovacího projektu

Dalším krokem je vytvoření projektu testu jednotek pro otestování knihovny StringLibrary. Testy jednotek vytvoříte provedením následujících kroků:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení Utility (Nástroje) a vyberte Add New Project **(Přidat**  >  **nový projekt).**

::: moniker range="vs-2017"

2. V dialogovém **okně Přidat nový** projekt vyberte uzel C# a pak vyberte **.NET Core.**

   > [!NOTE]
   > Testy jednotek není možné psát ve stejném jazyce jako knihovna tříd.

3. V pravém podokně vyberte šablonu Projekt testu jednotek **(.NET Core)** a  do textového pole Název zadejte **StringLibraryTests,** jak je znázorněno na následujícím obrázku:

   ![Dialogové okno **Přidat nový projekt** pro projekt testů jednotek](./media/lut-start/add-unit-test-cs.png)

4. Vyberte **OK** a vytvořte projekt.

   > [!NOTE]
   > Tento kurz Začínáme používá Live Unit Testing s testovací architekturou MSTest. Můžete také použít testovací architektury xUnit a NUnit.

::: moniker-end

::: moniker range=">=vs-2019"

2. Do **vyhledávacího** pole šablony zadejte test jednotek, jako jazyk vyberte **C#** a pak vyberte šablonu **Projekt** testování jednotek pro .NET Core. Klikněte na **Next** (Další).

   > [!NOTE]
   > Od verze Visual Studio 2019 verze 16.9 se název šablony projektu MSTest změnil z **projektu MSTest Unit Test (.NET Core)** na **Unit Test Project**.

3. Pojmete projekt **StringLibraryTests** a klikněte na **Další.**

4. Zvolte doporučené cílové rozhraní (.NET Core 3.1) nebo .NET 5 a pak zvolte **Vytvořit.**

   > [!NOTE]
   > Tento kurz Začínáme používá Live Unit Testing s testovací architekturou MSTest. Můžete také použít testovací architektury xUnit a NUnit.

::: moniker-end

5. Projekt testování částí nemůže automaticky přistupovat ke knihovně tříd, kterou testuje. Přístup ke knihovně testů můžete poskytnout přidáním odkazu na projekt knihovny tříd. To můžete udělat tak, že kliknete pravým tlačítkem na projekt a `StringLibraryTests` **vyberete Přidat**  >  **odkaz.** V dialogovém **okně Správce** odkazů  se ujistěte, že je vybraná karta Řešení, a vyberte projekt StringLibrary, jak je znázorněno na následujícím obrázku.

   ![Dialogové okno **Správce odkazů**](./media/lut-start/add-reference.png)

6. Nahraďte často používaný kód testu jednotek poskytovaný šablonou následujícím kódem:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using UtilityLibraries;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestStartsWithUpper()
           {
               // Tests that we expect to return true.
               string[] words = { "Alphabet", "Zebra", "ABC", "Αθήνα", "Москва" };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsTrue(result,
                                 $"Expected for '{word}': true; Actual: {result}");
               }
           }

           [TestMethod]
           public void TestDoesNotStartWithUpper()
           {
               // Tests that we expect to return false.
               string[] words = { "alphabet", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                                  "1234", ".", ";", " " };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsFalse(result,
                                  $"Expected for '{word}': false; Actual: {result}");
               }
           }

           [TestMethod]
           public void DirectCallWithNullOrEmpty()
           {
               // Tests that we expect to return false.
               string[] words = { String.Empty, null };
               foreach (var word in words)
               {
                   bool result = StringLibrary.StartsWithUpper(word);
                   Assert.IsFalse(result,
                                  $"Expected for '{(word == null ? "<null>" : word)}': " +
                                  $"false; Actual: {result}");
               }
           }
       }
   }
   ```

7. Uložte projekt výběrem **ikony Uložit** na panelu nástrojů.

   Vzhledem k tomu, že kód testu jednotek obsahuje několik znaků, které nejsou ASCII, zobrazí se následující dialogové okno s upozorněním, že některé znaky budou ztraceny, pokud soubor uložíte ve výchozím formátu ASCII.

8. Klikněte na tlačítko **Uložit s jiným kódováním** .

   ![Zvolit kódování souboru](media/lut-start/ascii-encoding.png)

9. V rozevíracím seznamu **kódování** v dialogovém okně **možnosti uložení zálohy** vyberte možnost **Unicode (UTF-8 bez podpisu)-znaková stránka 65001**, jak ukazuje následující obrázek:

   ![Výběr kódování UTF-8](media/lut-start/utf8-encoding.png)

10. Zkompilujte projekt testů jednotek výběrem **sestavení sestavit znovu**  >  **sestavit** v nabídce aplikace Visual Studio nejvyšší úrovně.

Vytvořili jste knihovnu tříd a také některé testy jednotek pro ni. Nyní jste dokončili nezbytné úkony, která je potřebná k použití Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Povolit Live Unit Testing

Zatím i když jste napsali testy pro knihovnu tříd StringLibrary, neudělali jste je. Po povolení je Live Unit Testing spustí automaticky. Uděláte to takto:

1. Volitelně můžete vybrat okno editoru kódu, které obsahuje kód pro StringLibrary. To je buď *Class1. cs* pro projekt C# nebo *Class1. vb* pro Visual Basic projekt. (Tento krok vám umožní vizuální kontrolu výsledku testů a rozsahu pokrytí kódu, když povolíte Live Unit Testing.)

1.   >    >  V nabídce aplikace Visual Studio nejvyšší úrovně vyberte test Live Unit Testing **Spustit** .

1. Visual Studio spustí živý test jednotek, který automaticky spustí všechny testy.

::: moniker range="vs-2017"
Po dokončení testů v **Průzkumníku testů** se zobrazí celkové výsledky a výsledek jednotlivých testů. Kromě toho okno editoru kódu graficky zobrazuje jak pokrytí testovacího kódu, tak i výsledek pro vaše testy. Jak ukazuje následující obrázek, všechny tři testy byly úspěšně provedeny. Ukazuje také, že naše testy pokryly všechny cesty kódu v metodě a všechny testy byly úspěšně provedeny (což je označeno zelenou `StartsWithUpper` značkou zaškrtnutí """").. Nakonec ukazuje, že žádná z ostatních metod v Řetězcové knihovna nemá pokrytí kódu (což je označeno modrým řádkem "➖").

![Průzkumník testů a okno editoru kódu po spuštění live unit testing](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019&quot;
Po dokončení testů zobrazí Live Unit Testing **výsledky** i výsledky jednotlivých testů. Kromě toho okno editoru kódu graficky zobrazuje pokrytí testovacího kódu i výsledek pro vaše testy. Jak je vidět na následujícím obrázku, všechny tři testy byly úspěšně provedeny. Ukazuje také, že naše testy pokryly všechny cesty kódu v metodě a všechny testy byly úspěšně provedeny (což je označeno zelenou `StartsWithUpper` značkou zaškrtnutí &quot;&quot;&quot;").. Nakonec ukazuje, že žádná z ostatních metod v Řetězcové knihovna nemá pokrytí kódu (což je označeno modrým řádkem "➖").

![Live Test Explorer a okno editoru kódu po spuštění Live Unit Testing](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Můžete také získat podrobnější informace o pokrytí testu a výsledcích testu výběrem konkrétní ikony pokrytí kódu v okně editoru kódu. Pokud chcete prozkoumat tyto podrobnosti, proveďte následující:

1. Klikněte na zelenou značku zaškrtnutí na řádku, který `if (String.IsNullOrWhiteSpace(s))` čte v `StartsWithUpper` metodě . Jak je vidět na následujícím obrázku, Live Unit Testing, že tento řádek kódu pokrývají tři testy a že všechny byly úspěšně provedeny.

   ![Pokrytí kódu pro podmíněný příkaz "if"](media/lut-start/code-coverage-cs1.png)

1. Klikněte na zelenou značku zaškrtnutí na řádku, který `return Char.IsUpper(s[0])` čte v `StartsWithUpper` metodě . Jak je vidět na následujícím obrázku, Live Unit Testing, že tento řádek kódu pokrývají pouze dva testy a že všechny byly úspěšně provedeny.

   ![Pokrytí kódu pro příkaz return](media/lut-start/code-coverage-cs2.png)

Hlavní problém, který Live Unit Testing identifikuje, je neúplné pokrytí kódu. Budete ho řešit v další části.

## <a name="expand-test-coverage"></a>Rozšíření pokrytí testu

V této části rozšíříte testování částí do `StartsWithLower` metody. I když to uděláte, Live Unit Testing bude dynamicky pokračovat v testování kódu.

Chcete-li rozšíření pokrytí kódu k `StartsWithLower` metodě, postupujte následovně:

1. `TestStartsWithLower` `TestDoesNotStartWithLower` Do souboru zdrojového kódu testu projektu přidejte následující metody a:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet1":::

1. Upravte `DirectCallWithNullOrEmpty` metodu přidáním následujícího kódu hned za volání [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet2":::

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

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet3":::

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

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/program2.cs" id="Snippet1":::

1. Live Unit Testing automaticky znovu spustí testovací metodu, která se nezdařila.

   Live Unit Testing zobrazí aktualizované výsledky, které se také zobrazí v okně Editor kódu.

## <a name="see-also"></a>Viz také

- [Live Unit Testing v aplikaci Visual Studio](live-unit-testing.md)
- [Live Unit Testing nejčastějších dotazech](live-unit-testing-faq.yml)
