---
title: 'Návod: Vývoj včasného testování s funkcí generování před využitím'
ms.date: 10/09/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c500f7a245ffd3a0dec175dd5f016cf1b2596fa4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821484"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Návod: Vývoj včasného testování s funkcí generování před využitím

Toto téma popisuje způsob použití [Generovat z využití](../ide/visual-csharp-intellisense.md#generate-from-usage) funkci, která podporuje vývoj s včasným testu.

 *Nejprve otestovat vývoj* je přístup k softwaru návrhu, ve kterém nejprve zápis testů jednotek, které jsou založeny na specifikacích produktu a potom napsat zdrojový kód, který je potřeba provést testy úspěšné. Visual Studio podporuje vývoj s včasným test vygenerováním nové typy a členy ve zdrojovém kódu při prvním odkazu je v testovacích případů, předtím, než jsou definovány.

 Visual Studio vygeneruje nové typy a členové s minimálním přerušením do svého pracovního postupu. Můžete vytvořit zástupné procedury pro typy, metody, vlastnosti, pole nebo konstruktory bez opuštění vaší aktuální umístění v kódu. Když otevřete dialogové okno pro určení možností pro generování typů, zaměřuje vrátí okamžitě v aktuálně otevřeném souboru při zavření dialogového okna.

 **Generovat z využití** funkci jde použít s rozhraní pro testování, které se integrují se sadou Visual Studio. V tomto tématu je ukázáno Microsoft Unit Testing Framework.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Vytvořte projekt knihovny tříd Windows a projekt testů

1. V [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vytvořte nový **knihovny tříd Windows** projektu. Pojmenujte ji `GFUDemo_VB` nebo `GFUDemo_CS`podle toho, jaký jazyk používáte.

2. V **Průzkumníka řešení**, klikněte pravým tlačítkem na ikonu řešení v horní části, zvolte **přidat**a klikněte na tlačítko **nový projekt**. V levém podokně **nový projekt** dialogového okna zvolte **Test**.

3. V prostředním podokně vyberte **projekt testu jednotek** a přijměte výchozí název `UnitTestProject1`. Následující obrázek znázorňuje dialogových oken, když se objeví v [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. V [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vypadá podobně jako dialogové okno.

    ![Dialogové okno Nový projekt testů](../ide/media/newproject_test.png)

4. Zvolte **OK** zavřete **nový projekt** dialogové okno.

### <a name="add-a-reference-to-the-class-library-project"></a>Přidejte odkaz na projekt knihovny tříd

1.  V **Průzkumníka řešení**, v části jednotky testování projektu, klikněte pravým tlačítkem na **odkazy** položku a zvolte **přidat odkaz**.

2.  V **správce odkazů** dialogu **projekty** a pak vyberte projekt knihovny tříd.

3.  Zvolte **OK** zavřete **správce odkazů** dialogové okno.

4.  Uložení vašeho řešení. Nyní je připraven k započetí psaní testů.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generovat novou třídu testu jednotek

1. Projekt testů obsahuje soubor s názvem *UnitTest1*. Dvakrát klikněte na tento soubor v **Průzkumníka řešení** ho otevřete v editoru kódu. Vygenerované třídy testu a testovací metody.

2. Vyhledejte prohlášení pro třídu `UnitTest1` a přejmenujte ho na `AutomobileTest`.

   > [!NOTE]
   >  Technologie IntelliSense teď poskytuje dvě možnosti pro doplňování příkazů IntelliSense: *doplňovacím režimem* a *režim návrhu*. Použijte režim návrhu pro situace, ve kterých se používají třídy a členy, než jsou definovány. Když **IntelliSense** je otevřeno okno, můžete stisknout **Ctrl**+**Alt**+**místo** přepínat mezi doplňovacím režimem a režimem návrhu. Zobrazit [použití IntelliSense](../ide/using-intellisense.md) Další informace. Režim návrhu vám pomůže při psaní `Automobile` v dalším kroku.

3. Vyhledejte `TestMethod1()` metoda a přejmenujte ho na `DefaultAutomobileIsInitializedCorrectly()`. V této metodě vytvoření nové instance třídy s názvem `Automobile`, jak je znázorněno na následujících snímcích obrazovky. Zobrazí se podtržení vlnovkou, což znamená chybu kompilace a [rychlé akce](../ide/quick-actions.md) na levém okraji se zobrazí žárovka (C# pouze), nebo přímo pod vlnovka, pokud se při najetí myší nad ním.

    ![Rychlé akce v jazyce Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Rychlé akce v jazyce C&#35;](../ide/media/genclass_underline.png)

4. Zvolte nebo klikněte na tlačítko **rychlé akce** žárovky. Zobrazí se vám chybová zpráva s oznámením, že typ `Automobile` není definován. Také se zobrazí některá řešení.

5. Klikněte na tlačítko **generovat nový typ** otevřít **generovat typ** dialogové okno. Toto dialogové okno obsahuje možnosti, které zahrnují generování typ v jiném projektu.

6. V **projektu** klikněte na možnost **GFUDemo\_VB** nebo **GFUDemo_CS** dáte pokyn, aby sada Visual Studio přidejte soubor do projektu knihovny tříd místo testu projekt. Pokud ještě není vybraná, zvolte **vytvořit nový soubor** a pojmenujte ho *Automobile.cs* nebo *Automobile.vb*.

     ![Generovat dialogové okno Nový typ](../ide/media/genotherdialog.png)

7. Klikněte na tlačítko **OK** zavřete dialogové okno a vytvořte nový soubor.

8. V **Průzkumníka řešení**, podívejte se do části **GFUDemo_VB** nebo **GFUDemo_CS** uzel projektu pro ověření, že nový *Automobile.vb* nebo  *Automobile.cs* soubor existuje. V editoru kódu, zaměřuje se pořád ještě v `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`, což vám umožní pokračovat v psaní testu se minimálně přerušení.

### <a name="generate-a-property-stub"></a>Generování provizorního kódu vlastnosti
Předpokládejme, že specifikace uvádí, že `Automobile` třídy mají dvě veřejné vlastnosti s názvem `Model` a `TopSpeed`. Tyto vlastnosti je nutné inicializovat s výchozími hodnotami `"Not specified"` a `-1` pomocí výchozího konstruktoru. Následující test jednotky se ověří, že výchozí konstruktor nastaví vlastnosti pro jejich správnou výchozí hodnoty.

1. Přidejte následující řádek kódu, který `DefaultAutomobileIsInitializedCorrectly` zkušební metody.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Vzhledem k tomu, že kód odkazuje na dva nedefinovanými vlastnostmi `Automobile`, podtržení vlnovkou se zobrazí v části `Model` a `TopSpeed`. Najeďte myší na `Model` a zvolte **rychlé akce** světle žárovku a pak zvolte **generovat vlastnost "Automobile.Model"**.

3. Generování provizorního kódu vlastnosti pro `TopSpeed` vlastnost stejným způsobem.

     V `Automobile` tříd, typy nové vlastnosti jsou správně odvodit z kontextu.

### <a name="generate-a-stub-for-a-new-constructor"></a>Generování zástupných procedur pro nový konstruktor
Teď vytvoříme testovací metoda, která se generovat podložení konstruktor k inicializaci `Model` a `TopSpeed` vlastnosti. Později přidáte další kód pro dokončení testu.

1. Přidat následující dodatečné testovací metodu do vaší `AutomobileTest` třídy.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2.  Klikněte na tlačítko **rychlé akce** světle kuličky v rámci červená vlnovka a potom klikněte na **generovat konstruktor 'Auto'**.

     V `Automobile` třídy souboru, Všimněte si, že nový konstruktor má prověřit, názvy místních proměnných, které se používají ve volání konstruktoru, nalezené vlastnosti, které mají stejné názvy v `Automobile` třídy a zadaný kód v těle konstruktoru na ukládání hodnot argumentů v `Model` a `TopSpeed` vlastnosti.


3.  Jakmile vygenerujete nový konstruktor, podtržení vlnovkou se zobrazí pod volání výchozího konstruktoru v `DefaultAutomobileIsInitializedCorrectly`. Chybová zpráva uvádí, že `Automobile` třída nemá žádný konstruktor, který nepřijímá žádné argumenty. Chcete-li generovat explicitní výchozí konstruktor, který nemá žádné parametry, klikněte na tlačítko **rychlé akce** světle žárovku a pak klikněte na **generovat konstruktor 'Auto'**.

### <a name="generate-a-stub-for-a-method"></a>Generování zástupných procedur pro metodu
Předpokládejme, že specifikace uvádí, že nový `Automobile` můžou být přepnuté do `IsRunning` stavu, pokud jeho `Model` a `TopSpeed` vlastnosti jsou nastaveny na jinou hodnotu než výchozí hodnoty.

1. Přidejte následující řádky do `AutomobileWithModelNameCanStart` metody.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2.  Klikněte na tlačítko **rychlé akce** návrhy pro `myAuto.Start` metoda volání a pak klikněte na **generovat metodu "Automobile.Start"**.

3.  Klikněte na tlačítko **rychlé akce** návrhy pro `IsRunning` vlastnosti a pak klikněte na tlačítko **generovat vlastnost "Automobile.IsRunning"**.

     `Automobile` Třída nyní obsahuje metodu s názvem `Start()` a vlastnost s názvem `IsRunning`.

### <a name="run-the-tests"></a>Spustit testy

1.  Na **testovací** nabídce zvolte **spustit** > **všechny testy**.

     **Spustit** > **všechny testy** příkaz spustí všechny testy ve všech testovacích architektur, které jsou určeny pro aktuální řešení. V tomto případě existují dva testy a oba jsou neúspěšné, podle očekávání. `DefaultAutomobileIsInitializedCorrectly` Test selže, protože `Assert.IsTrue` podmínka vrátí `False`. `AutomobileWithModelNameCanStart` Test selže, protože `Start` metodu `Automobile` třída vyvolá výjimku.

     **Výsledky testů** je okno zobrazeno na následujícím obrázku.

     ![Výsledky testů, které se nezdařilo](../ide/media/testsfailed.png)

2.  V **výsledky testu** okna, dvakrát klikněte na každý řádek výsledků testu přejděte do umístění každého testu.

### <a name="implement-the-source-code"></a>Implementace zdrojového kódu

1.  Přidejte následující kód do výchozího konstruktoru tak, `Model`, `TopSpeed` a `IsRunning` vlastnosti jsou inicializovány na jejich správnou výchozí hodnoty `"Not specified"`, `-1`, a `False` (nebo `false` pro C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2.  Když `Start` metoda je volána, měli nastavit `IsRunning` příznak na hodnotu true pouze tehdy, pokud `Model` nebo `TopSpeed` vlastnosti jsou nastaveny na jinou hodnotu než výchozí hodnoty. Odeberte `NotImplementedException` z metody body a přidejte následující kód.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Znovu spusťte testy

- Na **testovací** nabídky, přejděte k **spustit**a potom klikněte na tlačítko **všechny testy**.

     Tentokrát testy jsou úspěšné. **Výsledky testů** je okno zobrazeno na následujícím obrázku.

     ![Výsledky testů, které předávají](../ide/media/testspassed.png)

## <a name="see-also"></a>Viz také:

- [Generování před využitím](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Používání technologie IntelliSense](../ide/using-intellisense.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Rychlé akce](../ide/quick-actions.md)