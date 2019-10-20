---
title: Vývoj pro první test pomocí funkce generovat z využití
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81ab4b1597ea9f91a1b5081e89fd4cb77e0d8c63
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647161"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Návod: vývoj pro první test pomocí funkce generovat z použití

Toto téma ukazuje, jak použít funkci [Generovat z použití](../ide/visual-csharp-intellisense.md#generate-from-usage) , která podporuje vývoj na prvním testu.

 *Vývoj pro první test* je přístup k návrhu softwaru, ve kterém jste nejprve zapisovali testy jednotek na základě specifikací produktu, a pak napíšete zdrojový kód, který je požadován k úspěšnému provedení testů. Visual Studio podporuje vývoj na prvním testu tím, že generuje nové typy a členy ve zdrojovém kódu při jejich prvním odkazování v testovacích případech před jejich definováním.

Visual Studio vygeneruje nové typy a členy s minimálním přerušením pracovního postupu. Můžete vytvořit zástupné procedury pro typy, metody, vlastnosti, pole nebo konstruktory, aniž byste opustili aktuální umístění v kódu. Když otevřete dialogové okno pro zadání možností pro generování typů, při zavření dialogového okna se fokus vrátí hned na aktuální otevřený soubor.

Funkci **Generovat z použití** lze použít s testovacími architekturami, které jsou integrovány se sadou Visual Studio. V tomto tématu je znázorněno rozhraní testování částí společnosti Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Vytvoření projektu knihovny tříd Windows a testovacího projektu

1. V C# nebo Visual Basic vytvořte nový projekt **knihovny tříd systému Windows** . Pojmenujte ho `GFUDemo_VB` nebo `GFUDemo_CS`, podle toho, který jazyk používáte.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na ikonu řešení v horní části a vyberte **Přidat**  > **Nový projekt**.

3. Vytvořte nový projekt **testu jednotek (.NET Framework)** .

   ::: moniker range="vs-2017"

   Na následujícím obrázku je znázorněno dialogové okno **Nový projekt** pro C# šablony.

   ![Šablona projektu testování částí](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Přidat odkaz na projekt knihovny tříd

1. V **Průzkumník řešení**v rámci projektu testování částí klikněte pravým tlačítkem myši na položku **odkazy** a vyberte možnost **Přidat odkaz**.

2. V dialogovém okně **Správce odkazů** vyberte **projekty** a potom vyberte projekt knihovny tříd.

3. Kliknutím na **tlačítko OK** zavřete dialogové okno **Správce odkazů** .

4. Uložte své řešení. Teď jste připraveni začít psát testy.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generovat novou třídu z testu jednotek

1. Testovací projekt obsahuje soubor s názvem *UnitTest1*. Dvojím kliknutím na tento soubor v **Průzkumník řešení** otevřete v editoru kódu. Byla vygenerována testovací třída a testovací metoda.

2. Vyhledejte deklaraci pro třídu `UnitTest1` a přejmenujte ji na `AutomobileTest`.

   > [!NOTE]
   > Technologie IntelliSense nyní nabízí dvě alternativy dokončování příkazů technologie IntelliSense: *režim dokončování* a *režim návrhu*. Režim návrhu použijte pro situace, ve kterých se třídy a členy používají předtím, než budou definovány. Když je okno **IntelliSense** otevřené, můžete stisknout **Ctrl** +**ALT** +**MEZERNÍK** pro přepínání mezi režimem dokončení a režimem návrhu. Další informace najdete v tématu [použití technologie IntelliSense](../ide/using-intellisense.md) . Režim návrhu vám pomůže při psaní `Automobile` v dalším kroku.

3. Vyhledejte metodu `TestMethod1()` a přejmenujte ji na `DefaultAutomobileIsInitializedCorrectly()`. V rámci této metody vytvořte novou instanci třídy s názvem `Automobile`, jak je znázorněno na následujících snímcích obrazovky. Zobrazí se vlnové podtržení, které indikuje chybu při kompilaci, a v levém horním rohu se objeví chybová žárovka Chyba [rychlé akce](../ide/quick-actions.md) , která se zobrazí na levém okraji, nebo přímo pod vlnovkou, pokud na ni najedete myší.

    ![Rychlé akce v Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Rychlé akce v jazyce C&#35;](../ide/media/genclass_underline.png)

4. Vyberte nebo klikněte na žárovku **rychlé akce** . Zobrazí se chybová zpráva s oznámením, že typ `Automobile` není definován. Zobrazí se také některá řešení.

5. Kliknutím na **generovat nový typ** otevřete dialogové okno **generovat typ** . Toto dialogové okno obsahuje možnosti, které zahrnují generování typu v jiném projektu.

6. V seznamu **projekt** klikněte na **GFUDemo \_VB** nebo **GFUDemo_CS** , abyste aplikaci Visual Studio vydali pokyn k přidání souboru do projektu knihovny tříd namísto testovacího projektu. Pokud ještě není vybraná, vyberte **vytvořit nový soubor** a pojmenujte ho *Automobile.cs* nebo *automobil. vb*.

     ![Dialogové okno generovat nový typ](../ide/media/genotherdialog.png)

7. Kliknutím na tlačítko **OK** zavřete dialogové okno a vytvořte nový soubor.

8. V **Průzkumník řešení**vyhledejte v uzlu projektu **GFUDemo_VB** nebo **GFUDemo_CS** , zda je k dispozici nový soubor *automobil. vb* nebo *Automobile.cs* . V editoru kódu je fokus stále v `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`, což vám umožní pokračovat v psaní testu s minimálním přerušením.

### <a name="generate-a-property-stub"></a>Vygenerování provizorního kódu vlastnosti
Předpokládat, že specifikace produktu uvádí, že třída `Automobile` má dvě veřejné vlastnosti s názvem `Model` a `TopSpeed`. Tyto vlastnosti musí být inicializovány s výchozími hodnotami `"Not specified"` a `-1` výchozím konstruktorem. Následující test jednotek ověří, zda výchozí konstruktor nastaví vlastnosti na jejich správné výchozí hodnoty.

1. Do metody `DefaultAutomobileIsInitializedCorrectly` test přidejte následující řádek kódu.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Vzhledem k tomu, že kód odkazuje na dvě nedefinované vlastnosti `Automobile`, v části `Model` a `TopSpeed` se zobrazí vlnové podtržení. Najeďte myší na `Model` a zvolte žárovku chyby **rychlých akcí** a pak zvolte **Generovat vlastnost ' automobil. model '** .

3. Vygenerujte zástupnou proceduru vlastnosti pro vlastnost `TopSpeed` stejným způsobem.

     Ve třídě `Automobile` jsou typy nových vlastností správně odvozeny z kontextu.

### <a name="generate-a-stub-for-a-new-constructor"></a>Vygenerovat zástupnou proceduru pro nový konstruktor
Nyní vytvoříme testovací metodu, která vygeneruje zástupnou proceduru konstruktoru pro inicializaci `Model` a `TopSpeed` vlastností. Později přidáte další kód pro dokončení testu.

1. Přidejte následující další testovací metodu do třídy `AutomobileTest`.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. V červené vlnovce klikněte na žárovku Chyba **rychlých akcí** a pak klikněte na **vytvořit konstruktor v automobilu**.

     V souboru `Automobile` třídy si všimněte, že nový konstruktor zkontroloval názvy místních proměnných, které se používají ve volání konstruktoru, nalezené vlastnosti, které mají stejné názvy ve třídě `Automobile` a dodávají kód v těle konstruktoru pro uložení hodnoty argumentů ve vlastnostech `Model` a `TopSpeed`.

3. Po vygenerování nového konstruktoru se pod voláním výchozího konstruktoru v `DefaultAutomobileIsInitializedCorrectly` zobrazí vlnové podtržení. Chybová zpráva uvádí, že třída `Automobile` nemá žádný konstruktor, který přebírá nula argumentů. Pokud chcete vygenerovat explicitní výchozí konstruktor, který nemá parametry, klikněte na žárovku chyby **rychlých akcí** a pak klikněte na **vytvořit konstruktor v automobilu**.

### <a name="generate-a-stub-for-a-method"></a>Generování zástupné procedury pro metodu
Předpokládá se, že specifikace uvádí, že nový `Automobile` může být vložen do `IsRunning` stavu, pokud je jeho `Model` a `TopSpeed` vlastností nastaveno na jinou hodnotu než výchozí hodnoty.

1. Do metody `AutomobileWithModelNameCanStart` přidejte následující řádky.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. Klikněte na žárovku chyby **rychlých akcí** pro volání metody `myAuto.Start` a pak klikněte na **vygenerovat metodu ' automobil. Start '** .

3. Klikněte na žárovku **rychlých akcí** pro vlastnost `IsRunning` a pak klikněte na **vygenerovat vlastnost ' automobil. derunning '** .

     Třída `Automobile` nyní obsahuje metodu s názvem `Start()` a vlastnost s názvem `IsRunning`.

### <a name="run-the-tests"></a>Spustit testy

1. V nabídce **test** vyberte možnost **Spustit**  > **všechny testy**.

     Příkaz **spustit**  > **všechny testy** spustí všechny testy v jakémkoli testovacím rozhraní, které jsou zapsány pro aktuální řešení. V tomto případě existují dvě testy a obě selžou, podle očekávání. Test `DefaultAutomobileIsInitializedCorrectly` se nezdařil, protože podmínka `Assert.IsTrue` vrací `False`. Test `AutomobileWithModelNameCanStart` se nezdařil, protože metoda `Start` ve třídě `Automobile` vyvolá výjimku.

     Následující obrázek ukazuje **výsledky testů** okno.

     ![Výsledky testů, které selhaly](../ide/media/testsfailed.png)

2. V okně **výsledky testů** dvakrát klikněte na každý řádek výsledku testu, abyste přešli do umístění každého testu.

### <a name="implement-the-source-code"></a>Implementace zdrojového kódu

1. Přidejte následující kód do výchozího konstruktoru tak, aby byly všechny vlastnosti `Model`, `TopSpeed` a `IsRunning` všechny inicializovány na jejich správné výchozí hodnoty `"Not specified"`, `-1` a `False` (nebo `false` pro C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. Když je volána metoda `Start`, měla by nastavit příznak `IsRunning` na hodnotu true, pouze pokud jsou vlastnosti `Model` nebo `TopSpeed` nastaveny na jinou hodnotu než jejich výchozí hodnota. Odeberte `NotImplementedException` z těla metody a přidejte následující kód.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Spustit testy znovu

- V nabídce **test** přejděte na příkaz **Spustit**a potom klikněte na možnost **všechny testy**.

     Tentokrát testy proběhnou. Následující obrázek ukazuje **výsledky testů** okno.

     ![Výsledky testů, které byly úspěšné](../ide/media/testspassed.png)

## <a name="see-also"></a>Viz také:

- [Generovat z využití](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Používání technologie IntelliSense](../ide/using-intellisense.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Rychlé akce](../ide/quick-actions.md)