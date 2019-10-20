---
title: Generování testů jednotek kódu pomocí funkce IntelliTest
ms.date: 10/05/2015
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: cd808e23fbb94259df0805125e7d6f3e27dbaeac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664903"
---
# <a name="how-to-generate-unit-tests-by-using-intellitest"></a>Postupy: generování testů jednotek pomocí IntelliTest

IntelliTest prozkoumá váš kód .NET a vygeneruje testovací data a sadu testů jednotek. Pro každý příkaz v kódu se generuje vstupní test, který spustí tento příkaz. Pro každou podmíněnou větev v kódu se provede analýza případu. Například `if` příkazy, kontrolní výrazy a všechny operace, které mohou vyvolat výjimky, jsou analyzovány. Tato analýza slouží k vygenerování testovacích dat pro parametrizovaný test jednotek pro každou z vašich metod, vytváření testů jednotek s vysokým pokrytím kódu.

Při spuštění IntelliTest můžete snadno zjistit, které testy selžou, a přidat potřebný kód k jejich opravě. Můžete vybrat, které z vygenerovaných testů mají být uloženy do projektu testů pro zajištění regresní sady. Při změně kódu znovu spusťte IntelliTest, abyste zachovali vygenerované testy v synchronizaci se změnami kódu.

## <a name="availability-and-extensions"></a>Dostupnost a rozšíření

Příkazy nabídky **vytvořit IntelliTest** a **Spustit IntelliTest** :

* Jsou k dispozici pouze v edici Enterprise sady Visual Studio.

* Podporují pouze C# kód, který cílí na .NET Framework.

* Jsou [rozšiřitelné](#extend-framework) a podporují generování testů ve formátu MSTest, MSTest v2, nunit a xUnit.

* Nepodporují konfiguraci x64.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Prozkoumejte: Použití IntelliTest k prozkoumávání kódu a generování testů jednotek

Pro generování testů jednotek musí být vaše typy veřejné.

1. Otevřete řešení v aplikaci Visual Studio a pak otevřete soubor třídy, který obsahuje metody, které chcete testovat.

2. Klikněte pravým tlačítkem na metodu a vyberte možnost **Spustit IntelliTest** a Generujte testy jednotek kódu v metodě.

   ![Klikněte&#45;pravým tlačítkem na metodu a Generujte testy jednotek.](../test/media/runpex.png)

   IntelliTest spouští váš kód mnohokrát s různými vstupy. Každý běh je reprezentován v tabulce zobrazující vstupní testovací data a výsledný výstup nebo výjimku.

   ![Okno výsledků průzkumu se zobrazuje s testy](../test/media/pexexplorationresults.png)

Chcete-li generovat testy jednotek pro všechny veřejné metody ve třídě, jednoduše klikněte pravým tlačítkem myši na třídu a nikoli na konkrétní metodu a pak zvolte možnost **Spustit IntelliTest**. Pomocí rozevíracího seznamu v okně **výsledků prozkoumání** můžete zobrazit testy jednotek a vstupní data pro jednotlivé metody ve třídě.

![Vyberte výsledky testu, které se mají zobrazit v seznamu.](../test/media/selectpextest.png)

V případě testů, které jsou předávány, ověřte, že hlášené výsledky ve sloupci výsledek odpovídají vašim očekáváním pro váš kód. Pro testy, které selžou, opravte kód podle potřeby. Pak znovu spusťte IntelliTest a ověřte opravy.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Trvalé: uložte testy jednotek jako regresní sadu.

1. Vyberte řádky dat, které chcete uložit s parametrizovanou jednotkovým testem, do testovacího projektu.

     ![Vybrat testy; klikněte&#45;pravým tlačítkem a vyberte Uložit.](../test/media/savepextests.png)

     Můžete zobrazit testovací projekt a parametrizovaný test jednotky, který byl vytvořen – jednotlivé testy jednotek odpovídající jednotlivým řádkům jsou uloženy v souboru *. g.cs* v testovacím projektu a parametrizovaný test jednotky je uložen *v odpovídajícím souboru. soubor cs* . Můžete spustit testy jednotek a zobrazit výsledky z Průzkumníka testů stejným způsobem jako u všech testů jednotek, které jste vytvořili ručně.

     ![Otevřít soubor třídy v testovací metodě pro zobrazení testu jednotek](../test/media/testmethodpex.png)

     Do testovacího projektu jsou přidány také všechny nezbytné odkazy.

     Pokud se kód metody změní, znovu spusťte IntelliTest a udržujte testy jednotek synchronizované se změnami.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Pomoc: Použití IntelliTest k zaměření zkoumání kódu

1. Pokud máte komplexnější kód, IntelliTest vám pomůže se zaměřením průzkumu kódu. Například pokud máte metodu, která má rozhraní jako parametr a existuje více než jedna třída, která implementuje toto rozhraní, IntelliTest zjistí tyto třídy a ohlásí upozornění.

     Podívejte se na upozornění a rozhodněte se, co chcete udělat.

     ![Zobrazit upozornění](../test/media/pexviewwarning.png)

2. Po prozkoumání kódu a pochopení, co chcete testovat, můžete opravit upozornění a vybrat, které třídy použít k otestování rozhraní.

     ![Klikněte&#45;pravým tlačítkem na upozornění a vyberte opravit.](../test/media/pexfixwarning.png)

     Tato volba je přidána do souboru *PexAssemblyInfo.cs* .

     `[assembly: PexUseType(typeof(Camera))]`

3. Nyní můžete znovu spustit IntelliTest pro generování parametrizovaných testů jednotek a testovacích dat pouze pomocí třídy, kterou jste opravili.

     ![Znovu spusťte IntelliTest, aby se vygenerovala testovací data.](../test/media/pexwarningsfixed.png)

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Zadejte: pomocí IntelliTest ověřte vlastnosti správnosti, které zadáte v kódu.

Zadejte obecný vztah mezi vstupy a výstupy, které mají vygenerované testy jednotek ověřovat. Tato specifikace je zapouzdřena v metodě, která vypadá jako testovací metoda, ale je univerzálně kvantifikovaná. Toto je parametrizovaná Metoda testování částí a jakékoli kontrolní výrazy, které provedete, musí obsahovat všechny možné vstupní hodnoty, které může IntelliTest generovat.

## <a name="q--a"></a>Otázka & A

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Otázka: lze použít IntelliTest pro nespravovaný kód?

**A:** Ne, IntelliTest funguje jenom se spravovaným kódem.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>Otázka: kdy dojde k úspěšnému vygenerování testu?

**A:** Předává jako jakýkoliv jiný test jednotky, pokud nedošlo k výjimkám. Dojde k chybě, pokud nějaký kontrolní výraz neuspěje nebo pokud testovaný kód vyvolá neošetřenou výjimku.

Pokud máte test, který může uplynout, pokud jsou vyvolány určité výjimky, můžete nastavit jeden z následujících atributů na základě požadavků na testovací metodu, třídu testu nebo úroveň sestavení:

- **PexAllowedExceptionAttribute**

- **PexAllowedExceptionFromTypeAttribute**

- **PexAllowedExceptionFromTypeUnderTestAttribute**

- **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Otázka: mohu přidat předpoklady k parametrizovanému testu jednotek?

**A:** Ano, pomocí předpokladů určíte, která testovací data nejsou vyžadována pro testování částí konkrétní metody. K přidání předpokladů použijte třídu <xref:Microsoft.Pex.Framework.PexAssume>. Například můžete přidat předpoklad, že proměnná `lengths` nemá hodnotu null, například:

`PexAssume.IsNotNull(lengths);`

Pokud přidáte předpoklad a znovu spustíte IntelliTest, data testovacích dat, která již nejsou relevantní, se odeberou.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Otázka: mohu přidat kontrolní výrazy k parametrizovanému testu jednotek?

**A:** Ano, IntelliTest zkontroluje, že s tím, co v příkazu uplatňujete, je ve skutečnosti správné, když spustí testy jednotek. Použijte třídu <xref:Microsoft.Pex.Framework.PexAssert> nebo rozhraní API kontrolního výrazu, které jsou součástí testovacího rozhraní pro přidání kontrolních výrazů. Například můžete přidat kontrolní výraz, který má dvě proměnné stejné.

`PexAssert.AreEqual(a, b);`

Pokud přidáte kontrolní výraz a znovu spustíte IntelliTest, zkontroluje se, jestli je váš kontrolní výraz platný, a test selže, pokud není.

### <a name="NoRun"></a>Otázka: je možné generovat parametrizované testy jednotek bez spuštění IntelliTest jako první?

**A:** Ano, kliknout pravým tlačítkem na třídu nebo metodu a pak zvolit **vytvořit IntelliTest**.

![Klikněte&#45;pravým tlačítkem na Editor a vyberte vytvořit IntelliTest](../test/media/pexcreateintellitest.png)

Přijměte výchozí formát pro vygenerování testů nebo změňte způsob, jakým jsou pojmenovány projekty a testy. Můžete vytvořit nový testovací projekt nebo uložit testy do existujícího projektu.

![Vytvoření IntelliTest s výchozím MSTest](../test/media/pexcreateintellitestmstest.png)

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Otázka: je možné použít jiné architektury testování částí s IntelliTest?

**A:** Ano, pomocí následujícího postupu můžete [Najít a nainstalovat další architektury](../test/install-third-party-unit-test-frameworks.md).
Rozšíření testovacího rozhraní jsou také k dispozici v Visual Studio Marketplace například [generátor nunit test](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371).

Po restartování sady Visual Studio a opětovném otevření řešení klikněte pravým tlačítkem na třídu nebo metodu a pak zvolte **vytvořit IntelliTest**. Zde vyberte nainstalovanou architekturu:

![Vybrat jiné rozhraní pro testování částí pro IntelliTest](../test/media/pexcreateintellitestextensions.png)

Pak spusťte IntelliTest a vygenerujte jednotlivé testy jednotek v příslušných souborech *. g.cs* .

### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Otázka: mohu získat další informace o tom, jak se testy generují?

**A:** Ano, pokud chcete získat přehled vysoké úrovně, přečtěte si tento [Blogový příspěvek](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/).
