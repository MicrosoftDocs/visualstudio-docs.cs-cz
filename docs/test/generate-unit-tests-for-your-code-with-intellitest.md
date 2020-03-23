---
title: Generování testů jednotek kódu pomocí funkce IntelliTest
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 65b1de58f195b957d080bd21144c22479b1aafed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589588"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Postup: Generování testů částí pomocí IntelliTest

IntelliTest zkoumá váš kód .NET pro generování testovacích dat a sadu testů částí. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí.  Pro každou podmíněnou větev v kódu se provede případová analýza.  Například `if` příkazy, kontrolní výrazy a všechny operace, které mohou vyvolat výjimky jsou analyzovány. Tato analýza se používá ke generování testovacích dat pro parametrizovaný test částí pro každou z vašich metod a vytváření testů částí s vysokým pokrytím kódu.

Při spuštění IntelliTest, můžete snadno zjistit, které testy selhávají a přidat všechny potřebné kód k jejich opravě. Můžete vybrat, které z generovaných testů uložit do testovacího projektu poskytnout regresní sadu. Při změně kódu znovu spusťte IntelliTest, aby generované testy byly synchronizovány se změnami kódu.

## <a name="availability-and-extensions"></a>Dostupnost a rozšíření

Příkazy nabídky **Vytvořit intelliTest** a **Spustit intelliTest:**

* Jsou k dispozici pouze v edici Enterprise sady Visual Studio.

* Podporujte pouze kód Jazyka C#, který cílí na rozhraní .NET Framework.

* Jsou [rozšiřitelné](#extend-framework) a podporují emitující testy ve formátu MSTest, MSTest V2, NUnit a xUnit.

* Nepodporují konfiguraci x64.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Prozkoumat: Pomocí IntelliTest prozkoumat svůj kód a generovat testy částí

Chcete-li generovat testy částí, musí být vaše typy veřejné.

1. Otevřete řešení v sadě Visual Studio a potom otevřete soubor třídy, který má metody, které chcete testovat.

2. Klikněte pravým tlačítkem myši na metodu a zvolte **Spustit IntelliTest** pro generování testů částí pro kód ve vaší metodě.

   ![Kliknutím pravým&#45;tlačítkem myši na metodu generování testů částí](../test/media/runpex.png)

   IntelliTest spustí váš kód mnohokrát s různými vstupy. Každý běh je reprezentován v tabulce zobrazující vstupní testovací data a výsledný výstup nebo výjimku.

   ![Zobrazí se okno Výsledky průzkumu s testy](../test/media/pexexplorationresults.png)

Chcete-li generovat testy částí pro všechny veřejné metody ve třídě, jednoduše klepněte pravým tlačítkem myši ve třídě spíše než konkrétní metodu a pak zvolte **Spustit IntelliTest**. Pomocí rozevíracího seznamu v okně **Výsledky průzkumu** zobrazte testy částí a vstupní data pro každou metodu ve třídě.

![Vyberte výsledky testů, které chcete zobrazit ze seznamu.](../test/media/selectpextest.png)

U testů, které projdou, zkontrolujte, zda hlášené výsledky ve sloupci výsledek odpovídají vašim očekáváním pro váš kód. Pro testy, které se nezdaří, opravit kód podle potřeby. Potom znovu spusťte IntelliTest k ověření oprav.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Zachovat: Uložte testy částí jako regresní sadu

1. Vyberte řádky dat, které chcete uložit s parametrizovaným testováním částí do testovacího projektu.

     ![Vyberte testy; klikněte&#45;pravým tlačítkem myši a zvolte Uložit](../test/media/savepextests.png)

     Můžete zobrazit testovací projekt a parametrizovaný test jednotky, který byl vytvořen - jednotlivé testy částí, odpovídající každému z řádků, jsou uloženy v souboru *.g.cs* v testovacím projektu a parametrizovaný test částí je uložen v odpovídajícím souboru *.cs.* Můžete spustit testy částí a zobrazit výsledky z Průzkumníka testů stejně jako u všech testů jednotek, které jste vytvořili ručně.

     ![Otevřít soubor třídy v testovací metodě pro zobrazení testu částí](../test/media/testmethodpex.png)

     Všechny potřebné odkazy jsou také přidány do testovacího projektu.

     Pokud se kód metody změní, znovu spusťte IntelliTest, aby byly testy jednotek synchronizovány se změnami.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Pomoc: Použití intellitestu k zaměření průzkumu kódu

1. Pokud máte složitější kód, IntelliTest vám pomůže se zaměřením průzkumu kódu. Například pokud máte metodu, která má rozhraní jako parametr a existuje více než jedna třída, která implementuje toto rozhraní, IntelliTest zjišťuje tyto třídy a hlásí upozornění.

     Zobrazením upozornění se můžete rozhodnout, co chcete udělat.

     ![Zobrazit upozornění](../test/media/pexviewwarning.png)

2. Po prozkoumání kódu a pochopit, co chcete testovat, můžete opravit upozornění zvolit, které třídy chcete použít k testování rozhraní.

     ![Klikněte pravým&#45;na upozornění a zvolte Opravit](../test/media/pexfixwarning.png)

     Tato volba je přidána do *souboru PexAssemblyInfo.cs.*

     `[assembly: PexUseType(typeof(Camera))]`

3. Nyní můžete znovu spustit IntelliTest generovat parametrizované testování částí a testovací data pouze pomocí třídy, kterou jste opravili.

     ![Znovu spusťte IntelliTest pro generování testovacích dat](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Určit: Pomocí testu IntelliTest ověřte vlastnosti správnosti, které zadáte v kódu.

Zadejte obecný vztah mezi vstupy a výstupy, které mají ověřit generované testy jednotek. Tato specifikace je zapouzdřena v metodě, která vypadá jako zkušební metoda, ale je univerzálně kvantifikována. Toto je parametrizovaná metoda testování částí a všechny kontrolní výrazy, které provedete, musí obsahovat všechny možné vstupní hodnoty, které může intelliTest generovat.

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Otázka: Můžete použít IntelliTest pro nespravovaný kód?

**A:** Ne, IntelliTest funguje pouze se spravovaným kódem.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>Otázka: Kdy vygenerovaný test projde nebo selže?

**A:** Předá jako jakýkoli jiný test jednotky, pokud nedojde k žádné výjimky. Selže, pokud se nezdaří kontrolní výraz nebo pokud testovaný kód vyvolá neošetřenou výjimku.

Pokud máte test, který může projít, pokud jsou vyvolány určité výjimky, můžete nastavit jeden z následujících atributů na základě vašich požadavků na zkušební metodu, testovací třídu nebo úroveň sestavení:

- **Atribut PexAllowedExceptionAttribute**

- **Atribut PexAllowedExceptionFromTypeAttribute**

- **Atribut PexAllowedExceptionFromTypeUnderTest**

- **Atribut PexAllowedExceptionFromAssembly**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Otázka: Lze přidat předpoklady k parametrizovanému testu částí?

**A:** Ano, použijte předpoklady k určení, která testovací data nejsou vyžadována pro jednotkový test pro konkrétní metodu. Pomocí <xref:Microsoft.Pex.Framework.PexAssume> třídy přidejte předpoklady. Můžete například přidat předpoklad, `lengths` že proměnná není null takto:

`PexAssume.IsNotNull(lengths);`

Pokud přidáte předpoklad a znovu spustíte IntelliTest, testovací data, která již není relevantní, budou odebrána.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Otázka: Lze přidat kontrolní výrazy do parametrizovaného testu částí?

**A:** Ano, IntelliTest zkontroluje, že to, co tvrdí teve ve vašem prohlášení je ve skutečnosti správné při spuštění testů částí. Použijte <xref:Microsoft.Pex.Framework.PexAssert> třídu nebo rozhraní API pro kontrolní výrazy, které je dodáváno s testovacím rámcem, a přidejte kontrolní výrazy. Můžete například přidat kontrolní výraz, že dvě proměnné jsou stejné.

`PexAssert.AreEqual(a, b);`

Pokud přidáte kontrolní výraz a znovu spustit IntelliTest, zkontroluje, zda je kontrolní výraz platný a test se nezdaří, pokud není.

### <a name="q-can-i-generate-parameterized-unit-tests-without-running-intellitest-first"></a><a name="NoRun"></a>Otázka: Lze generovat parametrizované testy částí bez předchozího spuštění testu IntelliTest?

**A:** Ano, klepněte pravým tlačítkem myši na třídu nebo metodu a pak zvolte **Vytvořit intelliTest**.

![Vpravo&#45;klikněte na editor, zvolte Vytvořit intelliTest](../test/media/pexcreateintellitest.png)

Přijměte výchozí formát pro generování testů nebo změňte název projektu a testů. Můžete vytvořit nový testovací projekt nebo uložit testy do existujícího projektu.

![Vytvoření intellitestu s výchozím nastavením MSTestu](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Otázka: Lze použít jiné rozhraní testování částí s IntelliTest?

**A:** Ano, pomocí těchto kroků [vyhledejte a nainstalujte další rozhraní](../test/install-third-party-unit-test-frameworks.md).
Rozšíření rozhraní test jsou k dispozici také v Sadě Visual Studio Marketplace, například [NUnit Test Generator](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Po restartování sady Visual Studio a opětovném otevření řešení klepněte pravým tlačítkem myši na třídu nebo metodu a pak zvolte **Vytvořit intelliTest**. Zde vyberte nainstalovaný rámec:

![Vyberte další rozhraní testování částí pro IntelliTest](../test/media/pexcreateintellitestextensions.png)

Potom spusťte IntelliTest generovat jednotlivé testy částí v jejich odpovídající *.g.cs* soubory.

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Otázka: Mohu se dozvědět více o tom, jak jsou testy generovány?

**A:** Ano, chcete-li získat přehled na vysoké úrovni, přečtěte si tento [blogový příspěvek](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/).
