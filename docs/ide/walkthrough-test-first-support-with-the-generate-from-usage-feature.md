---
title: Vývoj pro první test pomocí generování z využití
description: Naučte se, jak začlenit přístup pro vývoj testů před testováním pomocí funkce generovat z využití.
ms.custom: SEO-VS-2020
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: how-to
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d763a937ac23b397151aec163c2d0d90d7ebe6ba
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479677"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Návod: vývoj pro první test pomocí funkce generovat z použití

Toto téma ukazuje, jak použít funkci [Generovat z použití](../ide/visual-csharp-intellisense.md#generate-from-usage) , která podporuje vývoj na prvním testu.

 *Vývoj pro první test* je přístup k návrhu softwaru, ve kterém jste nejprve zapisovali testy jednotek na základě specifikací produktu, a pak napíšete zdrojový kód, který je požadován k úspěšnému provedení testů. Visual Studio podporuje vývoj na prvním testu tím, že generuje nové typy a členy ve zdrojovém kódu při jejich prvním odkazování v testovacích případech před jejich definováním.

Visual Studio vygeneruje nové typy a členy s minimálním přerušením pracovního postupu. Můžete vytvořit zástupné procedury pro typy, metody, vlastnosti, pole nebo konstruktory, aniž byste opustili aktuální umístění v kódu. Když otevřete dialogové okno pro zadání možností pro generování typů, při zavření dialogového okna se fokus vrátí hned na aktuální otevřený soubor.

Funkci **Generovat z použití** lze použít s testovacími architekturami, které jsou integrovány se sadou Visual Studio. V tomto tématu je znázorněno rozhraní testování částí společnosti Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Vytvoření projektu knihovny tříd Windows a testovacího projektu

1. V jazyce C# nebo Visual Basic vytvořte nový projekt **knihovny tříd systému Windows** . Pojmenujte ji `GFUDemo_VB` nebo `GFUDemo_CS` , podle toho, který jazyk používáte.

2. V **Průzkumník řešení** klikněte pravým tlačítkem myši na ikonu řešení v horní části, vyberte možnost **Přidat**  >  **Nový projekt**.

3. Vytvořte nový projekt **testu jednotek (.NET Framework)** .

   ::: moniker range="vs-2017"

   Na následujícím obrázku je znázorněno dialogové okno **Nový projekt** pro šablony jazyka C#.

   ![Šablona projektu testování částí](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Přidat odkaz na projekt knihovny tříd

1. V **Průzkumník řešení** v rámci projektu testování částí klikněte pravým tlačítkem myši na položku **odkazy** a vyberte možnost **Přidat odkaz**.

2. V dialogovém okně **Správce odkazů** vyberte **projekty** a potom vyberte projekt knihovny tříd.

3. Kliknutím na **tlačítko OK** zavřete dialogové okno **Správce odkazů** .

4. Uložte své řešení. Teď jste připraveni začít psát testy.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generovat novou třídu z testu jednotek

1. Testovací projekt obsahuje soubor s názvem *UnitTest1*. Dvojím kliknutím na tento soubor v **Průzkumník řešení** otevřete v editoru kódu. Byla vygenerována testovací třída a testovací metoda.

2. Vyhledejte deklaraci třídy `UnitTest1` a přejmenujte ji na `AutomobileTest` .

   > [!NOTE]
   > Technologie IntelliSense nyní nabízí dvě alternativy dokončování příkazů technologie IntelliSense: *režim dokončování* a *režim návrhu*. Režim návrhu použijte pro situace, ve kterých se třídy a členy používají předtím, než budou definovány. Když je okno **IntelliSense** otevřené, můžete stisknout **CTRL** + **+** + **MEZERNÍK** pro přepínání mezi režimem dokončení a režimem návrhu. Další informace najdete v tématu [použití technologie IntelliSense](../ide/using-intellisense.md) . Režim návrhu vám pomůže při psaní `Automobile` v dalším kroku.

3. Vyhledejte `TestMethod1()` metodu a přejmenujte ji na `DefaultAutomobileIsInitializedCorrectly()` . V rámci této metody vytvořte novou instanci třídy s názvem `Automobile` , jak je znázorněno na následujících snímcích obrazovky. Zobrazí se vlnové podtržení, které indikuje chybu při kompilaci, a v levém horním rohu se objeví chybová žárovka Chyba [rychlé akce](../ide/quick-actions.md) , která se zobrazí na levém okraji, nebo přímo pod vlnovkou, pokud na ni najedete myší.

    ![Rychlé akce v Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Rychlé akce v jazyce C&#35;](../ide/media/genclass_underline.png)

4. Vyberte nebo klikněte na žárovku **rychlé akce** . Zobrazí se chybová zpráva s oznámením, že typ není `Automobile` definován. Zobrazí se také některá řešení.

5. Kliknutím na **generovat nový typ** otevřete dialogové okno **generovat typ** . Toto dialogové okno obsahuje možnosti, které zahrnují generování typu v jiném projektu.

6. V seznamu **projekt** klikněte na **GFUDemo \_ VB** nebo **GFUDemo_CS** , abyste aplikaci Visual Studio pověřili přidání souboru do projektu knihovny tříd namísto testovacího projektu. Pokud ještě není vybraná, vyberte **vytvořit nový soubor** a pojmenujte ho *Automobile.cs* nebo *automobil. vb*.

     ![Dialogové okno generovat nový typ](../ide/media/genotherdialog.png)

7. Kliknutím na tlačítko **OK** zavřete dialogové okno a vytvořte nový soubor.

8. V **Průzkumník řešení** vyhledejte v uzlu **GFUDemo_VB** nebo **GFUDemo_CS** projektu, abyste ověřili, že je zde nový soubor *automobil. vb* nebo *Automobile.cs* . V editoru kódu je fokus stále v `AutomobileTest.DefaultAutomobileIsInitializedCorrectly` , což vám umožní pokračovat v psaní testu s minimálním přerušením.

### <a name="generate-a-property-stub"></a>Vygenerování provizorního kódu vlastnosti
Předpokládat, že specifikace produktu uvádí, že `Automobile` Třída má dvě veřejné vlastnosti s názvem `Model` a `TopSpeed` . Tyto vlastnosti musí být inicializovány s výchozími hodnotami `"Not specified"` a `-1` výchozím konstruktorem. Následující test jednotek ověří, zda výchozí konstruktor nastaví vlastnosti na jejich správné výchozí hodnoty.

1. Do testovací metody přidejte následující řádek kódu `DefaultAutomobileIsInitializedCorrectly` .

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Vzhledem k tomu, že kód odkazuje na dvě nedefinované vlastnosti `Automobile` , zobrazí se vlnové podtržení v oblasti `Model` a `TopSpeed` . Najeďte myší `Model` a zvolte žárovku Chyba **rychlé akce** a pak zvolte **Generovat vlastnost ' automobil. model '**.

3. Vygenerujte zástupnou proceduru vlastnosti pro `TopSpeed` vlastnost stejným způsobem.

     Ve `Automobile` třídě jsou typy nových vlastností správně odvozeny z kontextu.

### <a name="generate-a-stub-for-a-new-constructor"></a>Vygenerovat zástupnou proceduru pro nový konstruktor
Nyní vytvoříme testovací metodu, která bude generovat zástupnou proceduru konstruktoru pro `Model` inicializaci `TopSpeed` vlastností a. Později přidáte další kód pro dokončení testu.

1. Přidejte do třídy následující další metodu testu `AutomobileTest` .

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. V červené vlnovce klikněte na žárovku Chyba **rychlých akcí** a pak klikněte na **vytvořit konstruktor v automobilu**.

     V `Automobile` souboru třídy si všimněte, že nový konstruktor zkontroloval názvy místních proměnných, které se používají ve volání konstruktoru, nalezené vlastnosti, které mají stejné názvy ve `Automobile` třídě, a dodaný kód v těle konstruktoru pro uložení hodnot argumentů do `Model` `TopSpeed` vlastností a.

3. Po vygenerování nového konstruktoru se zobrazí podtržení vlnovkou pod voláním výchozího konstruktoru v `DefaultAutomobileIsInitializedCorrectly` . Chybová zpráva uvádí, že `Automobile` Třída nemá žádný konstruktor, který přebírá nula argumentů. Pokud chcete vygenerovat explicitní výchozí konstruktor, který nemá parametry, klikněte na žárovku chyby **rychlých akcí** a pak klikněte na **vytvořit konstruktor v automobilu**.

### <a name="generate-a-stub-for-a-method"></a>Generování zástupné procedury pro metodu
Předpokládá, že specifikace, která je nová, `Automobile` může být vložena do `IsRunning` stavu, pokud `Model` `TopSpeed` jsou vlastnosti a vlastností nastaveny na jinou hodnotu než výchozí hodnoty.

1. Do metody přidejte následující řádky `AutomobileWithModelNameCanStart` .

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. Klikněte na žárovku chyby **rychlých akcí** pro `myAuto.Start` volání metody a pak klikněte na **vygenerovat metodu ' automobil. Start '**.

3. Klikněte na žárovku **rychlých akcí** pro `IsRunning` vlastnost a pak klikněte na **vygenerovat vlastnost ' automobil. derunning '**.

     `Automobile`Třída nyní obsahuje metodu s názvem `Start()` a vlastnost s názvem `IsRunning` .

### <a name="run-the-tests"></a>Spuštění testů

1. V nabídce **test** vyberte možnost **Spustit**  >  **všechny testy**.

     Příkaz **Spustit**  >  **všechny testy** spustí všechny testy v jakémkoli testovacím rozhraní, které jsou zapsány pro aktuální řešení. V tomto případě existují dvě testy a obě selžou, podle očekávání. `DefaultAutomobileIsInitializedCorrectly`Test se nezdařil, protože `Assert.IsTrue` podmínka se vrátí `False` . `AutomobileWithModelNameCanStart`Test se nezdařil, protože `Start` Metoda ve `Automobile` třídě vyvolá výjimku.

     Následující obrázek ukazuje **výsledky testů** okno.

     ![Výsledky testů, které selhaly](../ide/media/testsfailed.png)

2. V okně **výsledky testů** dvakrát klikněte na každý řádek výsledku testu, abyste přešli do umístění každého testu.

### <a name="implement-the-source-code"></a>Implementace zdrojového kódu

1. Do výchozího konstruktoru přidejte následující kód tak, aby `Model` `TopSpeed` `IsRunning` byly vlastnosti a všechny inicializovány na jejich správné výchozí hodnoty `"Not specified"` , `-1` a `False` (nebo `false` pro C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. Při `Start` volání metody by měl příznak nastavit na `IsRunning` hodnotu true, pouze pokud `Model` `TopSpeed` jsou vlastnosti nebo nastaveny na jinou hodnotu než výchozí hodnota. Odeberte `NotImplementedException` z těla metody a přidejte následující kód.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Spustit testy znovu

- V nabídce **test** přejděte na příkaz **Spustit** a potom klikněte na možnost **všechny testy**.

     Tentokrát testy proběhnou. Následující obrázek ukazuje **výsledky testů** okno.

     ![Výsledky testů, které byly úspěšné](../ide/media/testspassed.png)

## <a name="see-also"></a>Viz také

- [Generovat z využití](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Používání technologie IntelliSense](../ide/using-intellisense.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Rychlé akce](../ide/quick-actions.md)
