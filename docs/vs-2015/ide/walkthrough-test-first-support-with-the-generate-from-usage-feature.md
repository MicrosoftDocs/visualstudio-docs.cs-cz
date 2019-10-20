---
title: 'Návod: Podpora testování s prvními testy pomocí funkce generovat z použití | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f40ed5f3070f177d1c914495f78a223364d64ae4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662678"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>Návod: Podpora včasného testování s funkcí Generování před využitím
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma ukazuje, jak použít funkci [Generovat z použití](../misc/generate-from-usage.md) , která podporuje vývoj na prvním testu.

 *Vývoj pro první test* je přístup k návrhu softwaru, ve kterém jste nejprve zapisovali testy jednotek na základě specifikací produktu, a pak napíšete zdrojový kód, který je požadován k úspěšnému provedení testů. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podporuje vývoj na prvním testu tím, že generuje nové typy a členy ve zdrojovém kódu při jejich prvním odkazování v testovacích případech, než jsou definované.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje nové typy a členy s minimálním přerušením pracovního postupu. Můžete vytvořit zástupné procedury pro typy, metody, vlastnosti, pole nebo konstruktory, aniž byste opustili aktuální umístění v kódu. Když otevřete dialogové okno pro zadání možností pro generování typů, při zavření dialogového okna se fokus vrátí hned na aktuální otevřený soubor.

 Funkci generovat z použití lze použít s testovacími architekturami, které jsou integrovány s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V tomto tématu je znázorněno rozhraní testování částí společnosti Microsoft.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Vytvoření projektu knihovny tříd Windows a testovacího projektu

1. V [!INCLUDE[csprcs](../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] vytvořte nový projekt knihovny tříd Windows. Pojmenujte ho `GFUDemo_VB` nebo `GFUDemo_CS`, podle toho, který jazyk používáte.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na ikonu řešení v horní části, přejděte na **Přidat**a pak klikněte na **Nový projekt**. V dialogovém okně **Nový projekt** klikněte v podokně **typy projektů** na levé straně na **test**.

3. V podokně **šablony** klikněte na možnost **projekt testování částí** a přijměte výchozí název UnitTestProject1. Následující ilustrace zobrazuje dialogové okno, když se zobrazí v [!INCLUDE[csprcs](../includes/csprcs-md.md)]. V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] bude dialogové okno vypadat podobně.

     ![Dialogové okno Nový projekt testů](../ide/media/newproject-test.png "NewProject_Test") Nový projekt – dialogové okno

4. Kliknutím na tlačítko **OK** zavřete dialogové okno **Nový projekt** .

5. V projektu třídy klikněte v **Průzkumník řešení**pravým tlačítkem myši na položku **odkazy** a klikněte na **Přidat odkaz**.

6. V dialogovém okně **Správce odkazů** vyberte **projekty** a potom vyberte projekt testování částí.

7. Kliknutím na tlačítko **OK** zavřete dialogové okno **Správce odkazů** .

8. V souboru **Class1** hned za poslední z existujících příkazů **using** přidejte příkaz **using** pro testovací projekt:

    * V Visual Basic přidejte `Using UnitTestProject1`

    * V C#přidejte `using UnitTestProject1;`

9. Uložte své řešení. Teď jste připraveni začít psát testy.

### <a name="to-generate-a-new-class-from-a-unit-test"></a>Vygenerování nové třídy z testu jednotek

1. Testovací projekt obsahuje soubor s názvem UnitTest1. Dvojím kliknutím na tento soubor v **Průzkumník řešení** otevřete v editoru kódu. Byla vygenerována testovací třída a testovací metoda.

2. Vyhledejte deklaraci pro třídu `UnitTest1` a přejmenujte ji na `AutomobileTest`. V C#případě, že je přítomen konstruktor `UnitTest1()`, přejmenujte jej na `AutomobileTest()`.

    > [!NOTE]
    > Technologie IntelliSense nyní nabízí dvě alternativy dokončování příkazů technologie IntelliSense: *režim dokončování* a *režim návrhu*. Režim návrhu použijte pro situace, ve kterých se třídy a členy používají předtím, než budou definovány. Po otevření okna technologie IntelliSense můžete stisknutím kombinace kláves CTRL + ALT + MEZERNÍK přepínat mezi režimem dokončení a režimem návrhu. Další informace najdete v tématu [použití technologie IntelliSense](../ide/using-intellisense.md) . Režim návrhu vám pomůže při psaní `Automobile` v dalším kroku.

3. Vyhledejte metodu `TestMethod1()` a přejmenujte ji na `DefaultAutomobileIsInitializedCorrectly()`. V rámci této metody vytvořte novou instanci třídy s názvem `Automobile`, jak je znázorněno na následujícím obrázku. Zobrazí se vlnové podtržení, které indikuje chybu při kompilaci, a v rámci názvu typu se zobrazí inteligentní značka. Přesné umístění inteligentní značky se liší v závislosti na tom, zda používáte [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../includes/csprcs-md.md)].

     ![Podtržení inteligentních značek v Visual Basic](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB") Visual Basic

     ![Podtržení inteligentních značek&#35; v jazyce C](../ide/media/genclass-underline.png "GenClass_Underline") VisualC#

4. Umístěte ukazatel myši na inteligentní značku, aby se zobrazila chybová zpráva oznamující, že ještě není definovaný žádný typ s názvem `Automobile`. Klikněte na inteligentní značku nebo stiskněte klávesy CTRL +. (CTRL + tečka) otevřete místní nabídku generovat z použití, jak je znázorněno na následujících obrázcích.

     ![Místní nabídka inteligentních značek v Visual Basic](../ide/media/genclass-smartvb.png "GenClass_SmartVB") Visual Basic

     ![Místní nabídka inteligentních značek v&#35; jazyce C](../ide/media/genclass-smartcs.png "GenClass_SmartCS") VisualC#

5. Nyní máte dvě možnosti. Můžete kliknout na **vygenerovat třídu auto** a vytvořit nový soubor v testovacím projektu a naplnit ho prázdnou třídou s názvem `Automobile`. Toto je rychlý způsob, jak vytvořit novou třídu v novém souboru s modifikátory výchozích možností přístupu v aktuálním projektu. Můžete také kliknout na možnost **generovat nový typ** a otevřít tak dialogové okno **generovat nový typ** . To poskytuje možnosti, které zahrnují vložení třídy do existujícího souboru a přidání souboru do jiného projektu.

     Kliknutím na možnost **generovat nový typ** otevřete dialogové okno **generovat nový typ** , které je znázorněno na následujícím obrázku. V seznamu **projekt** klikněte na **GFUDemo_VB** nebo **GFUDemo_CS** a poskytněte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby se soubor přidal do projektu zdrojového kódu namísto testovacího projektu.

     ![Dialogové okno generovat nový typ](../ide/media/genotherdialog.png "GenOtherDialog") Dialogové okno generovat nový typ

6. Kliknutím na tlačítko **OK** zavřete dialogové okno a vytvořte nový soubor.

7. V **Průzkumník řešení**vyhledejte v uzlu projektu GFUDemo_VB nebo GFUDemo_CS, zda je k dispozici nový soubor automobil. VB nebo Automobile.cs. V editoru kódu je fokus stále v `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. Můžete pokračovat v psaní testu s minimálním přerušením.

### <a name="to-generate-a-property-stub"></a>Vygenerování zástupné procedury vlastnosti

1. Předpokládat, že specifikace produktu uvádí, že třída `Automobile` má dvě veřejné vlastnosti s názvem `Model` a `TopSpeed`. Tyto vlastnosti musí být inicializovány s výchozími hodnotami `"Not specified"` a `-1` výchozím konstruktorem. Následující test jednotek ověří, zda výchozí konstruktor nastaví vlastnosti na jejich správné výchozí hodnoty.

     Přidejte následující řádek kódu pro `DefaultAutomobileIsInitializedCorrectly`.

     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]

     Vzhledem k tomu, že kód odkazuje na dvě nedefinované vlastnosti v `Automobile`, zobrazí se inteligentní značka. Klikněte na inteligentní značku pro `Model` a pak klikněte na **vygenerovat zástupnou proceduru vlastnosti**. Vygenerujte také zástupnou proceduru vlastnosti pro vlastnost `TopSpeed`.

     Ve třídě `Automobile` jsou typy nových vlastností správně odvozeny z kontextu.

     Následující ilustrace znázorňuje místní nabídku inteligentních značek.

     ![Vytvořit místní nabídku vlastnosti v Visual Basic](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB") Visual Basic

     ![Vytvořit kontextovou nabídku vlastnosti v&#35; jazyce C](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS") VisualC#

### <a name="to-locate-the-source-code"></a>Vyhledání zdrojového kódu

1. Pomocí funkce **Přejít k** přejděte k souboru se zdrojovým kódem Automobile.cs nebo automobil. vb, abyste mohli ověřit, že byly vygenerovány nové vlastnosti.

     Funkce **Přejít k** vám umožňuje rychle zadat textový řetězec, jako je například název typu nebo část názvu, a přejít na požadované místo kliknutím na prvek v seznamu výsledků.

     Kliknutím na tlačítko v editoru kódu a stisknutím kombinace kláves CTRL + (CTRL + čárka) otevřete dialogové okno **Přejít k** . Do textového pole zadejte `automobile`. V seznamu klikněte na třídu **automobil** a pak klikněte na **OK**.

     Na následujícím obrázku je vidět okno **Přejít k** .

     ![Přejít k dialogovému oknu](../ide/media/navigate-2.png "Navigate_2") Přejít na okno

### <a name="to-generate-a-stub-for-a-new-constructor"></a>Vygenerování zástupné procedury pro nový konstruktor

1. V této testovací metodě vygenerujete zástupnou proceduru konstruktoru, která inicializuje `Model` a `TopSpeed` vlastností tak, aby měly hodnoty, které zadáte. Později přidáte další kód pro dokončení testu. Přidejte následující další testovací metodu do třídy `AutomobileTest`.

     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]

2. V konstruktoru New Class klikněte na inteligentní značku a pak klikněte na **vygenerovat zástupnou proceduru vygenerovat konstruktor**. V souboru `Automobile` třídy si všimněte, že nový konstruktor zkontroloval názvy místních proměnných, které se používají ve volání konstruktoru, nalezené vlastnosti, které mají stejné názvy ve třídě `Automobile` a dodávají kód v těle konstruktoru pro uložení hodnoty argumentů ve vlastnostech `Model` a `TopSpeed`. (V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] pole `_model` a `_topSpeed` v novém konstruktoru jsou implicitně definovaná zálohovací pole pro `Model` a `TopSpeed` vlastnosti.)

3. Po vygenerování nového konstruktoru se pod voláním výchozího konstruktoru v `DefaultAutomobileIsInitializedCorrectly` zobrazí vlnové podtržení. Chybová zpráva uvádí, že třída `Automobile` nemá žádný konstruktor, který přebírá nula argumentů. Chcete-li vygenerovat explicitní výchozí konstruktor, který nemá parametry, klikněte na inteligentní značku a pak klikněte na **vygenerovat zástupnou proceduru pro vygenerování konstruktoru**.

### <a name="to-generate-a-stub-for-a-method"></a>Vygenerování zástupné procedury pro metodu

1. Předpokládá se, že specifikace uvádí, že nový `Automobile` může být přepnut do běžícího stavu, pokud jsou vlastnosti `Model` a `TopSpeed` nastavené na jinou hodnotu než výchozí hodnoty. Do metody `AutomobileWithModelNameCanStart` přidejte následující řádky.

     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]

2. Klikněte na inteligentní značku pro volání metody `myAuto.Start` a pak klikněte na **vygenerovat zástupnou proceduru metody**.

3. Klikněte na inteligentní značku vlastnosti `IsRunning` a pak klikněte na **vygenerovat zástupnou proceduru vlastnosti**. Třída `Automobile` nyní obsahuje následující kód.

     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]

### <a name="to-run-the-tests"></a>Spuštění testů

1. V nabídce **Test jednotky** ukažte na **Spustit testy jednotek**a potom klikněte na **všechny testy**. Tento příkaz spustí všechny testy ve všech testovacích rozhraních, která jsou zapsána pro aktuální řešení.

     V tomto případě existují dvě testy a obě selžou, podle očekávání. Test `DefaultAutomobileIsInitializedCorrectly` se nezdařil, protože podmínka `Assert.IsTrue` vrací `False`. Test `AutomobileWithModelNameCanStart` se nezdařil, protože metoda `Start` ve třídě `Automobile` vyvolá výjimku.

     Následující obrázek ukazuje **výsledky testů** okno.

     ![Výsledky testů, které selhaly](../ide/media/testsfailed.png "TestsFailed") Výsledky testů okno

2. V okně **výsledky testů** dvakrát klikněte na každý řádek výsledku testu, abyste přešli do umístění jednotlivých selhání testu.

### <a name="to-implement-the-source-code"></a>Implementace zdrojového kódu

1. Přidejte následující kód do výchozího konstruktoru tak, aby byly všechny vlastnosti `Model`, `TopSpeed` a `IsRunning` všechny inicializovány na jejich správné výchozí hodnoty `"Not specified"`, `-1` a `True` (`true`).

     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]

2. Když je volána metoda `Start`, měla by nastavit příznak `IsRunning` na hodnotu true, pouze pokud jsou vlastnosti `Model` nebo `TopSpeed` nastaveny na jinou hodnotu než jejich výchozí hodnota. Odeberte `NotImplementedException` z těla metody a přidejte následující kód.

     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]

### <a name="to-run-the-tests-again"></a>Chcete-li spustit testy znovu

1. V nabídce **test** přejděte na příkaz **Spustit**a potom klikněte na možnost **všechny testy v řešení**. Tentokrát testy proběhnou. Následující obrázek ukazuje **výsledky testů** okno.

     ![Výsledky testů, které byly úspěšné](../ide/media/testspassed.png "TestsPassed") Výsledky testů okno

## <a name="see-also"></a>Viz také
 [Generuje se z použití](../misc/generate-from-usage.md) při [psaní kódu](../ide/writing-code-in-the-code-and-text-editor.md) [pomocí technologie IntelliSense](../ide/using-intellisense.md) [testování částí kódu](../test/unit-test-your-code.md)
