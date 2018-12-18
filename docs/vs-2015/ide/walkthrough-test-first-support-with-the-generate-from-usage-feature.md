---
title: 'Návod: Podpora včasného testování s funkcí generování před využitím | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b2b45b75b689279a19dc1423a0cbf2b62d14a5c1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232840"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>Návod: Podpora včasného testování s funkcí Generování před využitím
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje způsob použití [Generovat z využití](../misc/generate-from-usage.md) funkci, která podporuje vývoj s včasným testu.  
  
 *Nejprve otestovat vývoj* je přístup k softwaru návrhu, ve kterém nejprve zápis testů jednotek, které jsou založeny na specifikacích produktu a potom napsat zdrojový kód, který je potřeba provést testy úspěšné. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podporuje včasného testování vývoj vygenerováním nové typy a členy ve zdrojovém kódu při prvním odkazu je v testovacích případů, předtím, než jsou definovány.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje nové typy a členové s minimálním přerušením do svého pracovního postupu. Můžete vytvořit zástupné procedury pro typy, metody, vlastnosti, pole nebo konstruktory bez opuštění vaší aktuální umístění v kódu. Když otevřete dialogové okno pro určení možností pro generování typů, zaměřuje vrátí okamžitě v aktuálně otevřeném souboru při zavření dialogového okna.  
  
 Generovat z využití funkce jde použít s rozhraní pro testování, které se integrují s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V tomto tématu je ukázáno Microsoft Unit Testing Framework.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Chcete-li vytvořit projekt knihovny tříd Windows a projekt testů  
  
1.  V [!INCLUDE[csprcs](../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], vytvořte nový projekt knihovny tříd Windows. Pojmenujte ji `GFUDemo_VB` nebo `GFUDemo_CS`podle toho, jaký jazyk používáte.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na ikonu řešení v horní části, přejděte na **přidat**a potom klikněte na tlačítko **nový projekt**. V **nový projekt** v dialogu **typy projektů** podokně nalevo, klikněte na tlačítko **Test**.  
  
3.  V **šablony** podokně klikněte na tlačítko **projekt testu jednotek** a přijměte výchozí název UnitTestProject1. Následující obrázek znázorňuje dialogových oken, když se objeví v [!INCLUDE[csprcs](../includes/csprcs-md.md)]. V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], vypadá podobně jako dialogové okno.  
  
     ![Dialogové okno Nový projekt testů](../ide/media/newproject-test.png "NewProject_Test")  
Dialogové okno Nový projekt  
  
4.  Klikněte na tlačítko **OK** zavřete **nový projekt** dialogové okno.

5.  Ve vašem projektu třídy v **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** položku a klikněte na tlačítko **přidat odkaz**.

6.  V **správce odkazů** dialogu **projekty** a pak vyberte projektu jednotkového testu.

7.  Klikněte na tlačítko **OK** zavřete **správce odkazů** dialogové okno.

8.  V **Class1** okamžitě po poslední existující soubor **pomocí** příkazy, přidejte **pomocí** příkaz pro testovací projekt:

    * V jazyce Visual Basic přidejte `Using UnitTestProject1`
    
    * V jazyce C# přidat `using UnitTestProject1;`
    
9.  Uložení vašeho řešení. Nyní jste připraveni začít psaní testů  
  
### <a name="to-generate-a-new-class-from-a-unit-test"></a>Ke generování novou třídu testu jednotek  
  
1.  Testovací projekt obsahuje soubor s názvem UnitTest1. Dvakrát klikněte na tento soubor v **Průzkumníka řešení** ho otevřete v editoru kódu. Vygenerované třídy testu a testovací metody.  
  
2.  Vyhledejte prohlášení pro třídu `UnitTest1` a přejmenujte ho na `AutomobileTest`. V jazyce C# Pokud `UnitTest1()` konstruktor je k dispozici, přejmenujte ho na `AutomobileTest()`.  
  
    > [!NOTE]
    >  Technologie IntelliSense teď poskytuje dvě možnosti pro doplňování příkazů IntelliSense: *doplňovacím režimem* a *režim návrhu*. Použijte režim návrhu pro situace, ve kterých se používají třídy a členy, než jsou definovány. Při otevření okno technologie IntelliSense můžete stisknutím CTRL + ALT + MEZERNÍK, chcete-li přepnout mezi doplňovacím režimem a režimem návrhu. Zobrazit [pomocí technologie IntelliSense](../ide/using-intellisense.md) Další informace. Režim návrhu vám pomůže při psaní `Automobile` v dalším kroku.  
  
3.  Vyhledejte `TestMethod1()` metoda a přejmenujte ho na `DefaultAutomobileIsInitializedCorrectly()`. V této metodě vytvoření nové instance třídy s názvem `Automobile`, jak je znázorněno na následujících obrázcích. Zobrazí se podtržení vlnovkou, což znamená chybu v době kompilace a inteligentní značky se zobrazí v části název typu. Přesné umístění inteligentní značky se liší v závislosti na tom, zda používáte [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
     ![Inteligentní značky podtržení v jazyce Visual Basic](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB")  
Visual Basic  
  
     ![Inteligentní značky podtržení v jazyce C&#35;](../ide/media/genclass-underline.png "GenClass_Underline")  
Visual C#  
  
4.  Umístěte ukazatel myši nad inteligentních značek zobrazíte chybovou zprávu s oznámením, že žádný typ s názvem `Automobile` dosud nebylo definováno. Kliknutím na inteligentní značku nebo stiskněte klávesy CTRL +. (CTRL + období) otevřete místní nabídku Generovat z využití, jak je znázorněno na následujících obrázcích.  
  
     ![Inteligentní značky kontextové nabídky v jazyce Visual Basic](../ide/media/genclass-smartvb.png "GenClass_SmartVB")  
Visual Basic  
  
     ![Inteligentní značky kontextové nabídky v jazyce C&#35;](../ide/media/genclass-smartcs.png "GenClass_SmartCS")  
Visual C#  
  
5.  Nyní máte dvě možnosti. Můžete kliknout na **generovat "Třídy Automobile"** vytvořte nový soubor v projektu testu a jeho naplnění prázdnou třídu s názvem `Automobile`. Toto je rychlý způsob, jak vytvořit novou třídu do nového souboru, který má výchozí modifikátory přístupu v aktuálním projektu. Můžete také kliknout na **generovat nový typ** otevřít **generovat nový typ** dialogové okno. To poskytuje možnosti, které zahrnují vložení třídy v existující soubor a přidání souboru do jiného projektu.  
  
     Klikněte na tlačítko **generovat nový typ** otevřít **generovat nový typ** dialogové okno, která je znázorněna na následujícím obrázku. V **projektu** klikněte na možnost **GFUDemo_VB** nebo **GFUDemo_CS** dáte pokyn, aby [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přidat soubor do projektu zdrojového kódu namísto testovacího projektu.  
  
     ![Generovat dialogové okno Nový typ](../ide/media/genotherdialog.png "GenOtherDialog")  
Generovat dialogové okno Nový typ  
  
6.  Klikněte na tlačítko **OK** zavřete dialogové okno a vytvořte nový soubor.  
  
7.  V **Průzkumníka řešení**, podívejte se do části GFUDemo_VB nebo GFUDemo_CS uzel projektu pro ověření, že nové Automobile.vb nebo Automobile.cs soubor existuje. V editoru kódu, zaměřuje je stále v `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. Můžete pokračovat v psaní testu se minimálně přerušení.  
  
### <a name="to-generate-a-property-stub"></a>Pro vygenerování provizorního kódu vlastnosti  
  
1.  Předpokládejme, že specifikace uvádí, že `Automobile` třídy mají dvě veřejné vlastnosti s názvem `Model` a `TopSpeed`. Tyto vlastnosti je nutné inicializovat s výchozími hodnotami `"Not specified"` a `-1` pomocí výchozího konstruktoru. Následující test jednotky se ověří, že výchozí konstruktor nastaví vlastnosti pro jejich správnou výchozí hodnoty.  
  
     Přidejte následující řádek kódu, který `DefaultAutomobileIsInitializedCorrectly`.  
  
     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]  
  
     Vzhledem k tomu, že kód odkazuje na dva nedefinovanými vlastnostmi `Automobile`, zobrazí se inteligentní značky. Kliknutím na inteligentní značku pro `Model` a potom klikněte na tlačítko **generování provizorního kódu vlastnosti**. Generování provizorního kódu vlastnosti pro `TopSpeed` vlastnost také.  
  
     V `Automobile` tříd, typy nové vlastnosti jsou správně odvodit z kontextu.  
  
     Následující obrázek znázorňuje místní nabídce inteligentních značek.  
  
     ![Generovat vlastnost místní nabídky v jazyce Visual Basic](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB")  
Visual Basic  
  
     ![Generovat vlastnost místní nabídky v jazyce C&#35;](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS")  
Visual C#  
  
### <a name="to-locate-the-source-code"></a>Vyhledejte zdrojový kód  
  
1.  Použití **přejít na** funkce Přejít k souboru zdrojového kódu Automobile.cs nebo Automobile.vb, aby mohli ověřit, že byly vytvořeny nové vlastnosti.  
  
     **Přejít na** funkce vám umožní rychle zadat textový řetězec, jako je název typu nebo část názvu a přejděte do požadovaného umístění po kliknutí na prvek v seznamu výsledků.  
  
     Otevřít **přejít na** dialogové okno kliknutím v editoru kódu a stisknutím klávesy CTRL +, (CTRL + čárka). V textovém poli zadejte `automobile`. Klikněte na tlačítko **Automobile** třídy v seznamu a potom klikněte na tlačítko **OK**.  
  
     **Přejít na** je okno zobrazeno na následujícím obrázku.  
  
     ![Dialogové okno Přejít na](../ide/media/navigate-2.png "Navigate_2")  
Navigovat na okno  
  
### <a name="to-generate-a-stub-for-a-new-constructor"></a>Generování zástupných procedur pro nový konstruktor  
  
1.  V této testovací metody, bude generovat konstruktor zástupnou proceduru, která bude inicializovat `Model` a `TopSpeed` vlastnosti hodnoty, které zadáte. Později přidáte další kód pro dokončení testu. Přidat následující dodatečné testovací metodu do vaší `AutomobileTest` třídy.  
  
     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]  
  
2.  Kliknutím na inteligentní značku v rámci konstruktoru nové třídy a pak klikněte na tlačítko **generovat konstruktor se zakázaným inzerováním**. V `Automobile` třídy souboru, Všimněte si, že nový konstruktor má prověřit, názvy místních proměnných, které se používají ve volání konstruktoru, nalezené vlastnosti, které mají stejné názvy v `Automobile` třídy a zadaný kód v těle konstruktoru na ukládání hodnot argumentů v `Model` a `TopSpeed` vlastnosti. (V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], `_model` a `_topSpeed` polí v konstruktoru nové jsou implicitně definovaný pomocné pole `Model` a `TopSpeed` vlastnosti.)  
  
3.  Jakmile vygenerujete nový konstruktor, podtržení vlnovkou se zobrazí pod volání výchozího konstruktoru v `DefaultAutomobileIsInitializedCorrectly`. Chybová zpráva uvádí, že `Automobile` třída nemá žádný konstruktor, který nepřijímá žádné argumenty. Pokud chcete generovat explicitní výchozí konstruktor, který nemá žádné parametry, klikněte na inteligentní značku a potom klikněte na **generovat konstruktor se zakázaným inzerováním**.  
  
### <a name="to-generate-a-stub-for-a-method"></a>Generování zástupných procedur pro metodu  
  
1.  Předpokládejme, že specifikace uvádí, že nový `Automobile` můžou být přepnuté do stavu spuštění, pokud jeho `Model` a `TopSpeed` vlastnosti jsou nastaveny na jinou hodnotu než výchozí hodnoty. Přidejte následující řádky do `AutomobileWithModelNameCanStart` metody.  
  
     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]  
  
2.  Klikněte na inteligentní značku a `myAuto.Start` metoda volání a pak klikněte na **generovat pahýl metody**.  
  
3.  Klikněte na inteligentní značku a `IsRunning` vlastnosti a pak klikněte na tlačítko **generování provizorního kódu vlastnosti**. `Automobile` Třída nyní obsahuje následující kód.  
  
     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]  
  
### <a name="to-run-the-tests"></a>Ke spuštění testů  
  
1.  Na **Jednotkový Test** nabídky, přejděte k **spustit jednotkové testy**a potom klikněte na tlačítko **všechny testy**. Tento příkaz spustí všechny testy ve všech testovacích architektur, které jsou určeny pro aktuální řešení.  
  
     V tomto případě existují dva testy a oba jsou neúspěšné, podle očekávání. `DefaultAutomobileIsInitializedCorrectly` Test selže, protože `Assert.IsTrue` podmínka vrátí `False`. `AutomobileWithModelNameCanStart` Test selže, protože `Start` metodu `Automobile` třída vyvolá výjimku.  
  
     **Výsledky testů** je okno zobrazeno na následujícím obrázku.  
  
     ![Výsledky testu, který selhal](../ide/media/testsfailed.png "TestsFailed")  
okno výsledků testu  
  
2.  V **výsledky testu** okna, dvakrát klikněte na každý řádek výsledků testu přejděte do umístění jednotlivých selhání testu.  
  
### <a name="to-implement-the-source-code"></a>K implementaci zdrojového kódu  
  
1.  Přidejte následující kód do výchozího konstruktoru tak, `Model`, `TopSpeed` a `IsRunning` vlastnosti jsou inicializovány na jejich správnou výchozí hodnoty `"Not specified"`, `-1`, a `True` (`true`).  
  
     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]  
  
2.  Když `Start` metoda je volána, měli nastavit `IsRunning` příznak na hodnotu true pouze tehdy, pokud `Model` nebo `TopSpeed` vlastnosti jsou nastaveny na jinou hodnotu než výchozí hodnoty. Odeberte `NotImplementedException` z metody body a přidejte následující kód.  
  
     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]  
  
### <a name="to-run-the-tests-again"></a>Znovu spustit testy  
  
1.  Na **testovací** nabídky, přejděte k **spustit**a potom klikněte na tlačítko **všechny testy v řešení**. Tentokrát testy jsou úspěšné. **Výsledky testů** je okno zobrazeno na následujícím obrázku.  
  
     ![Výsledky testu, který předává](../ide/media/testspassed.png "TestsPassed")  
okno výsledků testu  
  
## <a name="see-also"></a>Viz také  
 [Generování před využitím](../misc/generate-from-usage.md)   
 [Psaní kódu](../ide/writing-code-in-the-code-and-text-editor.md)   
 [Používání atributu IntelliSense](../ide/using-intellisense.md)   
 [Testování částí kódu](../test/unit-test-your-code.md)



