---
title: Generování testů jednotek pro kód pomocí funkce IntelliTest | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.assetid: cd9ff940-e948-4d28-a72c-b291ef5c1e90
caps.latest.revision: 35
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6743db0b10d8df4f131f8125b3e2f83bca262054
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226509"
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Generování testů jednotek pro kód pomocí funkce IntelliTest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inteligentní testování vám umožní prozkoumat kód .NET a vygenerovat testovací data a sady testování částí. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí. Pro každou podmíněnou větev v kódu se provede Případová analýza. Například, pokud jsou analyzovány příkazy, výrazy a všechny operace, které můžou vyvolat výjimku. Této analýzy se generují testovací data pro parametrizovaný test části metod, vytváření testů jednotek s vysokým pokrytím kódu používá.  
  
 Při spuštění IntelliTest můžete snadno zobrazit, jaké testy se nedaří a přidejte všechny nezbytné kód a opravte je. Můžete vybrat, které z vygenerované testy k uložení do testovacího projektu poskytnout sadu regrese. Po provedení změny kódu, znovu spusťte IntelliTest pro synchronizaci vygenerované testy se změnami kódu.  
  
 IntelliTest se pouze k dispozici pro jazyk C# a nepodporuje x64 konfigurace.  
  
## <a name="get-started-with-intellitest"></a>Začínáme s IntelliTest  
 Visual Studio Enterprise, budete potřebovat.  
  
### <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Prozkoumejte: Použití IntelliTest dá prozkoumat kód a generování testů jednotek  
 Generování testů jednotek, vaše typy musí být veřejné. V opačném případě [vytvořit testy jednotek](#NoRun) první před jejich vytvořením.  
  
1.  Otevřete řešení v sadě Visual Studio. Pak otevřete soubor třídy, která obsahuje metody, které chcete testovat.  
  
2.  Klikněte pravým tlačítkem v metodě v kódu a zvolte **spustit inteligentní testování** ke generování testů jednotek pro kód v metodě.  
  
     ![Pravé&#45;klikněte na tlačítko ve své metodě ke generování testů jednotek](../test/media/runpex.png "RunPEX")  
  
     IntelliTest spustí váš kód několikrát s různými vstupy. Každé spuštění je vyjádřena v tabulka zobrazující vstupní testovací data a výsledný výstup nebo výjimky.  
  
     ![Zobrazí se okno výsledků průzkumu s testy](../test/media/pexexplorationresults.png "PEXExplorationResults")  
  
     Generování testů jednotek pro všechny veřejné metody ve třídě, jednoduše klikněte pravým tlačítkem ve třídě, nikoli konkrétní metody. Klikněte na tlačítko **spustit inteligentní testování**. Pomocí rozevíracího seznamu v okně výsledky průzkumu pro zobrazení testů jednotek a vstupní data pro jednotlivé metody ve třídě.  
  
     ![Vyberte výsledky testu, chcete-li zobrazit ze seznamu](../test/media/selectpextest.png "SelectPEXTest")  
  
     Zaznamenané výsledky ve sloupci výsledků testů, které předat, zkontrolujte, jestli odpovídat vašim očekáváním pro váš kód. Pro testy, které selžou kód podle potřeby opravte. Pak znovu spusťte IntelliTest ověření opravy.  
  
### <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Zachovat: Testy jednotek uložte jako sadu regrese  
  
1.  Vyberte řádky dat, které chcete uložit s parametrizovaný test jednotek do testovacího projektu.  
  
     ![Vyberte testy; správné&#45;klikněte a vyberte Uložit](../test/media/savepextests.png "SavePEXTests")  
  
     Můžete zobrazit projekt testů a parametrizovaný test části, který byl vytvořen - jednotlivých částí odpovídající na jednotlivých řádcích, se ukládají do. g.cs soubor v projektu testu a parametrizovaný test části je uložen v jeho odpovídající soubor cs. Můžete spustit testy jednotek a zobrazit výsledky z Průzkumníka testů, stejně jako byste to udělali pro všechny testy, které jste vytvořili ručně.  
  
     ![Soubor otevřete třídy v testovací metodě zobrazíte testování částí](../test/media/testmethodpex.png "TestMethodPEX")  
  
     Všechny potřebné odkazy jsou také přidány do projektu testů.  
  
     Pokud se změní kód metody, znovu spusťte IntelliTest pro synchronizaci jednotkové testy se změnami.  
  
### <a name="assist-use-intellitest-to-focus-code-exploration"></a>Asistent: Použití IntelliTest pro zkoumání kódu fokus  
  
1.  Pokud máte složitější kód, Intellitestu vám pomůže soustředit zkoumání kódu. Například pokud máte metodu, která má rozhraní jako parametr a existuje více než jednu třídu, která implementuje rozhraní, Intellitestu zjistí tyto třídy a zprávy upozornění.  
  
     Zobrazování upozornění se rozhodnout, co chcete udělat.  
  
     ![Zobrazování upozornění](../test/media/pexviewwarning.png "PEXViewWarning")  
  
2.  Po zkoumání kódu a pochopit, co chcete otestovat, můžete je vyřešit upozornění rozhodnout, které třídy k otestování rozhraní.  
  
     ![Pravé&#45;kliknutím na upozornění a zvolte opravu](../test/media/pexfixwarning.png "PEXFixWarning")  
  
     Tato volba se přidá do souboru PexAssemblyInfo.cs.  
  
     `[assembly: PexUseType(typeof(Camera))]`  
  
3.  Teď můžete znovu spustit Intellitestu a generovat parametrizovaný test části testovací data jenom pomocí třídy, která jste opravili.  
  
     ![Znovu spusťte IntelliTest generují testovací data](../test/media/pexwarningsfixed.png "PEXWarningsFixed")  
  
### <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Zadejte: IntelliTest použijte k ověření správnosti vlastnosti, které zadáte v kódu  
 Zadejte obecné vztah mezi vstupy a výstupy, které chcete, aby vygenerované testy jednotek pro ověření. Tato specifikace zapouzdřena v metodě, která vypadá jako testovací metody, ale univerzálně vyjadřuje. Toto je testovací metody parametrizované jednotky a pro všechny možné vstupní hodnoty, která mohou generovat IntelliTest musí obsahovat žádné kontrolní výrazy, které provedete.  
  
##  <a name="QandALink"></a> Q & A  
  
### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Dotaz: lze použít pro nespravovaný kód IntelliTest?  
 **Odpověď:** Ne, Intellitestu funguje jenom se spravovaným kódem.  
  
### <a name="q-when-does-a-generated-test-pass-or-fail"></a>Otázka: kdy generovaný test úspěšné nebo neúspěšné?  
 **Odpověď:** předává jako libovolné jiné jednotky testování, pokud dojde k žádné výjimky. Selže, pokud žádné kontrolní výraz selže nebo pokud testovaný kód vyvolá neošetřenou výjimku.  
  
 Pokud máte test, který můžete předat, pokud jsou vyvolány některé výjimky, můžete nastavit jednu z následujících atributů na základě vašich požadavků na testovací metody, třídě testu nebo sestavení úrovně:  
  
-   **PexAllowedExceptionAttribute**  
  
-   **PexAllowedExceptionFromTypeAttribute**  
  
-   **PexAllowedExceptionFromTypeUnderTestAttribute**  
  
-   **PexAllowedExceptionFromAssemblyAttribute**  
  
### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Dotaz: lze přidat předpoklady pro parametrizovaný test jednotek?  
 **Odpověď:** Ano, použijte k určení, které testovací data se nevyžaduje, pro testy jednotek pro konkrétní metody předpoklady. Použití <xref:Microsoft.Pex.Framework.PexAssume> třídy přidat předpoklady. Můžete například přidat předpokládá, že proměnné délky není null následujícím způsobem.  
  
 `PexAssume.IsNotNull(lengths);`  
  
 Pokud přidáte předpokládá a znovu spusťte IntelliTest, odeberou se testovací data, která už nejsou relevantní.  
  
### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Dotaz: lze přidat kontrolní výrazy do parametrizovaný test jednotek?  
 **Odpověď:** Ano, IntelliTest se zkontrolujte, že jsou uplatnění v příkazu ve skutečnosti správný při spuštění testů jednotek. Použití <xref:Microsoft.Pex.Framework.PexAssert> třídy nebo rozhraní API, která je součástí rozhraní pro testování přidat kontrolní výrazy kontrolního výrazu. Například můžete přidat kontrolní výraz, že dvě proměnné, které jsou stejné.  
  
 `PexAssert.AreEqual(a, b);`  
  
 Pokud chcete přidat kontrolní výraz a znovu spusťte IntelliTest, zkontroluje, že vaše kontrolní výraz je platný a test se nezdaří, pokud není.  
  
###  <a name="NoRun"></a> Dotaz: lze generovat parametrizované testy částí bez nutnosti nejprve spuštění IntelliTest  
 **Odpověď:** Ano, klikněte pravým tlačítkem na třídy nebo metody a pak zvolte **vytvořit IntelliTest**.  
  
 ![Pravé&#45;klikněte na tlačítko editoru, zvolte možnost vytvořit IntelliTest](../test/media/pexcreateintellitest.png "PEXCreateIntelliTest")  
  
 Přijměte výchozí formát vygenerovat vaše testy nebo změnit, jak se s názvem projektu a testy. Můžete vytvořit nový testovací projekt nebo uložit do existujícího projektu testů.  
  
 ![Vytvoření IntelliTest se výchozí MSTest](../test/media/pexcreateintellitestmstest.png "PEXCreateIntelliTestMSTest")  
  
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Otázka: Mohu použít jiné rozhraní pro testování částí s Intellitestem?  
 **Odpověď:** Ano, postupujte podle těchto kroků [najít a nainstalovat jiná rozhraní Framework](../test/install-third-party-unit-test-frameworks.md). Po restartování sady Visual Studio a znovu otevřete řešení, klikněte pravým tlačítkem na třídy nebo metody a pak zvolte **vytvořit IntelliTest**. Vyberte nainstalované rozhraní tady:  
  
 ![Vyberte jiné rámce jednotkových testů pro IntelliTest](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")  
  
 Potom spusťte IntelliTest generování testů jednotek v jejich odpovídající. g.cs soubory.  
  
### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Otázka: mohu dozvědět více o tom, jak jsou generovány testy?  
 **Odpověď:** Ano, chcete-li získat základní přehled, najdete v tomto [blogový příspěvek](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx).



