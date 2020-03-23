---
title: Vývoj první ho testu pomocí funkce Generovat z využití
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bf9a7e613a482167a01739320282f9ba8fdea26
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596889"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Návod: Vývoj na prvním místě s funkcí Generovat z použití

Toto téma ukazuje, jak používat [funkci Generovat z použití,](../ide/visual-csharp-intellisense.md#generate-from-usage) která podporuje vývoj první test.

 *Vývoj první test* je přístup k návrhu softwaru, ve kterém nejprve zapíšete testy částí na základě specifikací produktu a pak napíšete zdrojový kód, který je nutný k úspěšnému provedení testů. Visual Studio podporuje vývoj první test generováním nové typy a členy ve zdrojovém kódu při prvním odkazu na ně v testovacích případech, před jejich definování.

Visual Studio generuje nové typy a členy s minimálním přerušením pracovního postupu. Můžete vytvořit zástupné procedury pro typy, metody, vlastnosti, pole nebo konstruktory, aniž byste opustili aktuální umístění v kódu. Když otevřete dialogové okno pro určení voleb pro generování textu, fokus se po zavření dialogového okna okamžitě vrátí do aktuálního otevřeného souboru.

Funkci **Generovat z použití** lze použít s testovacími rámci, které se integrují s aplikací Visual Studio. V tomto tématu je demonstrována architektura testování částí společnosti Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Vytvoření projektu knihovny tříd systému Windows a testovacího projektu

1. V jazyce C# nebo Visual Basic vytvořte nový projekt **knihovny tříd systému Windows.** Pojmenujte jej `GFUDemo_VB` nebo `GFUDemo_CS`v závislosti na tom, který jazyk používáte.

2. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na ikonu řešení v horní části a zvolte **Přidat** > **nový projekt**.

3. Vytvořte nový **projekt projektu testování částí (.NET Framework).**

   ::: moniker range="vs-2017"

   Následující obrázek znázorňuje dialogové okno **Nový projekt** pro šablony jazyka C#.

   ![Šablona projektu projekt testování částí](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Přidání odkazu na projekt Knihovny tříd

1. V **Průzkumníku řešení**klikněte v rámci projektu testování částí pravým tlačítkem myši na položku **Reference** a zvolte **Přidat odkaz**.

2. V dialogovém okně **Správce odkazů** vyberte **Projekty** a pak vyberte projekt knihovny tříd.

3. Chcete-li zavřít dialogové okno **Správce odkazů,** zvolte **OK.**

4. Uložte své řešení. Nyní jste připraveni začít psát testy.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generovat novou třídu z testování částí

1. Testovací projekt obsahuje soubor s názvem *UnitTest1*. Poklepáním na tento soubor v **Průzkumníku řešení** jej otevřete v editoru kódu. Byla vygenerována testovací třída a zkušební metoda.

2. Vyhledejte deklaraci `UnitTest1` třídy a `AutomobileTest`přejmenujte ji na .

   > [!NOTE]
   > Technologie IntelliSense nyní nabízí dvě alternativy pro dokončování výpisu IntelliSense: *režim dokončení* a *režim návrhů*. Režim návrhů použijte pro situace, ve kterých jsou třídy a členy používány před jejich definováním. Když je otevřené okno **IntelliSense,** můžete stisknutím **kláves Ctrl**+**Alt**+**Space** přepínat mezi režimem dokončení a režimem návrhů. Další informace najdete [v tématu Použití technologie IntelliSense.](../ide/using-intellisense.md) Režim návrhu vám pomůže `Automobile` při psaní v dalším kroku.

3. Vyhledejte `TestMethod1()` metodu a `DefaultAutomobileIsInitializedCorrectly()`přejmenujte ji na . Uvnitř této metody vytvořte novou instanci třídy s názvem `Automobile`, jak je znázorněno na následujících snímcích obrazovky. Zobrazí se podtržení vlnovkou, která označuje chybu v době kompilace, a na levém okraji se zobrazí chybová žárovka [Rychlých akcí](../ide/quick-actions.md) nebo přímo pod vlnovkou, pokud na ni najedete.

    ![Rychlé akce v jazyce Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Rychlé akce v&#35; C](../ide/media/genclass_underline.png)

4. Zvolte nebo klikněte na žárovku **Rychlé akce.** Zobrazí se chybová zpráva, která `Automobile` uvádí, že typ není definován. Jsou také prezentovány s některými řešeními.

5. Kliknutím na **Generovat nový typ** otevřete dialogové okno Generovat **typ.** Toto dialogové okno obsahuje možnosti, které zahrnují generování typu v jiném projektu.

6. V seznamu **projekt** klepněte na **tlačítko GFUDemo\_VB** nebo **GFUDemo_CS** pokyn Visual Studio přidat soubor do projektu knihovny tříd namísto testovacího projektu. Pokud ještě není vybraná, zvolte **Vytvořit nový soubor** a pojmenujte ho *Automobile.cs* nebo *Automobile.vb*.

     ![Dialogové okno Generovat nový typ](../ide/media/genotherdialog.png)

7. Klepnutím na **tlačítko OK** zavřete dialogové okno a vytvořte nový soubor.

8. V **Průzkumníku řešení**vyhledejte pod uzětem **projektu GFUDemo_VB** nebo **GFUDemo_CS** a ověřte, zda je k dispozici nový soubor *Automobile.vb* nebo *Automobile.cs.* V editoru kódu je fokus stále v aplikaci , což umožňuje pokračovat v `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`psaní testu s minimálním přerušením.

### <a name="generate-a-property-stub"></a>Generování vlastností se zakázaným inzerováním
Předpokládejme, že specifikace `Automobile` produktu uvádí, že `Model` `TopSpeed`třída má dvě veřejné vlastnosti s názvem a . Tyto vlastnosti musí být inicializovány s výchozími `"Not specified"` hodnotami a `-1` výchozím konstruktorem. Následující testování částí ověří, zda výchozí konstruktor nastaví vlastnosti na správné výchozí hodnoty.

1. Do `DefaultAutomobileIsInitializedCorrectly` testovací metody přidejte následující řádek kódu.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Vzhledem k tomu, že `Automobile`kód odkazuje na dvě `Model` nedefinované vlastnosti zapnuté , zobrazí se pod a `TopSpeed`. Najeďte `Model` nad ním a zvolte chybovou žárovku **Rychlé akce** a pak zvolte **Generovat vlastnost "Automobil.Model"**.

3. Stejným způsobem vygenerujte zástupný kód vlastnosti `TopSpeed` pro vlastnost.

     Ve `Automobile` třídě jsou typy nových vlastností správně odvozeny z kontextu.

### <a name="generate-a-stub-for-a-new-constructor"></a>Generovat zástupný kód pro nového konstruktoru
Nyní vytvoříme testovací metodu, která vygeneruje příkazový příkaz `Model` `TopSpeed` se zakázaným inicializací vlastností a. Později přidáte další kód k dokončení testu.

1. Přidejte následující další testovací `AutomobileTest` metodu do vaší třídy.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. Klepněte na chybovou žárovku **Rychlé akce** pod červenou vlnovkou a potom klepněte na příkaz **Generovat konstruktor v části Automobil**.

     V `Automobile` souboru třídy všimněte si, že nový konstruktor prozkoumal názvy místních proměnných, které se používají `Automobile` ve volání konstruktoru, nalezené vlastnosti, které `Model` `TopSpeed` mají stejné názvy ve třídě, a zadali kód v těle konstruktoru pro uložení hodnot argumentů ve vlastnostech a.

3. Po vgenerování nového konstruktoru se pod voláním výchozího konstruktoru v `DefaultAutomobileIsInitializedCorrectly`. Chybová zpráva uvádí, že `Automobile` třída nemá žádný konstruktor, který přebírá nulové argumenty. Chcete-li vygenerovat explicitní výchozí konstruktor, který nemá parametry, klepněte na chybovou žárovku **Rychlé akce** a potom klepněte na příkaz **Generovat konstruktor v části Automobil**.

### <a name="generate-a-stub-for-a-method"></a>Generování zástupné procedury pro metodu
Předpokládejme, že specifikace `Automobile` uvádí, že `IsRunning` nový může `Model` `TopSpeed` být uveden do stavu, pokud jeho a vlastnosti jsou nastaveny na něco jiného než výchozí hodnoty.

1. Přidejte do `AutomobileWithModelNameCanStart` metody následující řádky.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. Klikněte **Quick Actions** na chybovou žárovku `myAuto.Start` Rychlé akce pro volání metody a potom klepněte na příkaz Generovat **metodu "Automobile.Start"**.

3. Klikněte **Quick Actions** na žárovku `IsRunning` Rychlé akce pro vlastnost a potom klepněte na příkaz Generovat vlastnost **Automobile.IsRunning**.

     Třída `Automobile` nyní obsahuje metodu s `Start()` `IsRunning`názvem a vlastnost s názvem .

### <a name="run-the-tests"></a>Spuštění testů

1. V nabídce **Test** zvolte **Spustit** > **všechny testy**.

      > Spustit **Run****všechny testy** příkaz spustí všechny testy ve všech testovacích rámců, které jsou zapsány pro aktuální řešení. V tomto případě existují dva testy a oba selhat, podle očekávání. Test `DefaultAutomobileIsInitializedCorrectly` se `Assert.IsTrue` nezdaří, `False`protože podmínka vrátí . Test `AutomobileWithModelNameCanStart` se nezdaří, `Start` `Automobile` protože metoda ve třídě vyvolá výjimku.

     Okno **Výsledky testů** je znázorněno na následujícím obrázku.

     ![Výsledky testů, které se nezdařily](../ide/media/testsfailed.png)

2. V okně **Výsledky testu** poklepejte na každý řádek výsledků testu a přejděte do umístění každého testu.

### <a name="implement-the-source-code"></a>Implementace zdrojového kódu

1. Přidejte následující kód do výchozího `Model`konstruktoru tak, aby byly všechny vlastnosti , `TopSpeed` a `IsRunning` vlastnosti inicializovány na správné výchozí hodnoty `"Not specified"`, `-1`a `False` (nebo `false` pro C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. Při `Start` volání metody by měla `IsRunning` nastavit příznak true `Model` pouze `TopSpeed` v případě, že vlastnosti nebo jsou nastaveny na něco jiného než jejich výchozí hodnotu. Odeberte `NotImplementedException` z těla metody a přidejte následující kód.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Spusťte testy znovu

- V nabídce **Test** přejděte na **Spustit**a potom klepněte na příkaz **Všechny testy**.

     Tentokrát testy projít. Okno **Výsledky testů** je znázorněno na následujícím obrázku.

     ![Výsledky zkoušek, které prošly](../ide/media/testspassed.png)

## <a name="see-also"></a>Viz také

- [Generovat z využití](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Používání technologie IntelliSense](../ide/using-intellisense.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Rychlé akce](../ide/quick-actions.md)
