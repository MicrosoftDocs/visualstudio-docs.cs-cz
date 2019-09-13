---
title: Testování pokrytí kódu
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24bc4c54e455f43aa5fd5fee0ce0d5a44042e497
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913190"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Určení rozsahu testovaného kódu pomocí pokrytí kódu

Funkci pokrytí kódu sady Visual Studio lze použít ke zjištění toho, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako jsou například jednotkové testy. Pro efektivní ochranu před chybami je vhodné testovat, neboli „pokrýt“, velkou část kódu projektu.

Analýza pokrytí kódu může být použita jak pro spravovaný (CLI), tak pro nespravovaný (nativní) kód.

Pokrytí kódu je jedna z možností při spouštění testovacích metod pomocí Průzkumníku testů. Tabulka výsledků zobrazuje procentuální podíl kódu, který byl spuštěn v každém sestavení, třídě a metodě. Editor zdrojového kódu navíc ukazuje samotný kód, který byl testován.

::: moniker range="vs-2017"

![Výsledky pokrytí kódu s barevné zvýrazňování](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Požadavky

Funkce pokrytí kódu je k dispozici pouze v edici Visual Studio Enterprise.

## <a name="analyze-code-coverage"></a>Analyzovat pokrytí kódu

::: moniker range="vs-2017"

1. V nabídce **test** vyberte možnost **Analyzovat pokrytí kódu**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V **Průzkumníku testů**vyberte v nabídce **Spustit** možnost **Analyzovat pokrytí kódu pro všechny testy** .

   ![Nabídka Analýza pokrytí kódu ve VS 2019](../test/media/vs-2019/analyze-code-coverage.png)

   Pokud **není Průzkumník testů** otevřený, otevřete ho tak, že vyberete **test** > **Průzkumník testů** **systému Windows** > , nebo stisknete klávesy **CTRL**+**E**,**T**.

::: moniker-end

2. Po spuštění testů, chcete-li zjistit, které řádky byly spuštěny, ![vyberte možnost Zobrazit ikonu](../test/media/codecoverage-showcoloringicon.png) barevného pokrytí kódu **Zobrazit barvy pokrytí kódu** v okně **výsledky pokrytí kódu** . Ve výchozím nastavení je kód, který je pokrytý testy, zvýrazněný světle modře.

   > [!TIP]
   > Chcete-li změnit barvy nebo použít tučnou plochu, vyberte možnost **nástroje** > **Možnosti** > **prostředí** > **písma a barvy** > **zobrazit nastavení pro: Textový editor**. V části **Zobrazit položky**upravte nastavení položek pokrytí, například **Rozsah nedotčená oblast**.
   >
   > ![Písma a barvy pokrytí kódu](media/vs-2019/coverage-fonts-and-colors.png)

3. Pokud výsledky zobrazují nízké pokrytí, prozkoumejte, které části kódu nejsou testovány, a vytvořte pro ně další testy. Vývojové týmy obvykle usilují o 80% pokrytí kódu. V některých situacích je přijatelné i nižší pokrytí. Nižší pokrytí je například přijatelné tehdy, pokud je část kódu generována ze standardní šablony.

> [!TIP]
> - Zapnout optimalizaci kompilátoru
> - Pokud pracujete s nespravovaným (nativním) kódem, použijte sestavení pro ladění.
> - Generovat soubory. pdb (symbol) pro každé sestavení

Pokud nezískáte očekávané výsledky, přečtěte si téma [řešení potíží s pokrytím kódu](../test/troubleshooting-code-coverage.md).

Po aktualizaci kódu nezapomeňte znovu spustit pokrytí kódu. Výsledky pokrytí kódu a barevné zvýraznění kódu nejsou po změně kódu nebo při spuštění testů automaticky aktualizovány.

## <a name="report-in-blocks-or-lines"></a>Sestava v blocích nebo řádcích

Pokrytí kódu se počítá v *blocích*. Blok je část kódu s právě jedním vstupním a výstupním bodem.  Pokud tok řízení programu projde během testovacího běhu blok, započítá se tento blok jako pokrytý. Počet průchodů blokem nemá na výsledek žádný vliv.

Výsledky můžete zobrazit také v části řádky kliknutím na možnost **Přidat nebo odebrat sloupce** v záhlaví tabulky. Někteří uživatelé dávají přednost určování pokrytí podle počtu řádků, protože jeho procenta lépe odpovídají velikosti fragmentů, které jsou vidět ve zdrojovém kódu. Dlouhý blok výpočtu by byl započítán jako jeden blok i v případě, že zabírá mnoho řádků.

> [!TIP]
> Řádek kódu může obsahovat více než jeden blok kódu. Pokud se jedná o tento případ a testovací běh vykonává všechny bloky kódu na řádku, počítá se jako jeden řádek. Pokud jsou některé, ale ne všechny bloky kódu na řádku, vykonávány, počítá se jako částečný řádek.

## <a name="manage-code-coverage-results"></a>Správa výsledků pokrytí kódu

V okně **výsledky pokrytí kódu** se obvykle zobrazuje výsledek posledního spuštění. Výsledky se budou lišit, pokud dojde ke změně zkušebních dat nebo jsou pokaždé spuštěny jen některé testy.

Okno pokrytí kódu lze také použít k zobrazení předchozích výsledků nebo výsledků získaných na jiných počítačích.

Je také možné sloučit výsledky několika běhů, pokud například používají jiná testovací data.

- Pokud **chcete zobrazit předchozí sadu výsledků**, vyberte ji z rozevírací nabídky. Nabídka obsahuje dočasný seznam, který je po otevření nového řešení vyprázdněn.

- Pokud **chcete zobrazit výsledky z předchozí relace**, vyberte možnost **importovat výsledky pokrytí kódu**, přejděte do složky **TestResults** ve vašem řešení a importujte soubor *. pokrytí* .

   Pokud se zdrojový kód od vygenerování souboru *. pokrytí* změnil, může se vybarvení pokrytí nesprávným.

- Pokud chcete, aby **výsledky byly čitelné jako text**, vyberte **Exportovat výsledky pokrytí kódu**. Tím se vygeneruje čitelný soubor s *příponou. coveragexml* , který můžete zpracovat pomocí jiných nástrojů nebo jednoduše poslat e-mailem.

- **Chcete-li odeslat výsledky někomu jinému**, odešlete soubor *. pokrytí* nebo exportovaný soubor *. coveragexml* . Tento soubor je pak možné importovat. Pokud se navíc shodují verze zdrojového kódu, je možné zobrazit i vybarvení pokrytí.

## <a name="merge-results-from-different-runs"></a>Sloučit výsledky z různých běhů

V některých situacích se na základě testovacích dat použijí různé bloky kódu. Může být tedy nutné sloučit výsledky různých testovacích běhů.

Například při spuštění testu se vstupem „2“ je zjištěno 50% pokrytí určité funkce. Při druhém spuštění testu se vstupem "-2" se zobrazí v zobrazení vybarvení pokrytí, na které se vztahuje další 50% funkce. Po sloučení výsledků těchto dvou testovacích běhů ukáže sestava i vybarvení 100% pokrytí funkce.

K ![tomu slouží ikona tlačítka pro sloučení v okně](../test/media/codecoverage-mergeicon.png) pokrytí kódu pro **sloučení výsledků pokrytí kódu** . Ke sloučení je možné použít libovolnou kombinaci předešlých běhů nebo importovaných výsledků. Pokud je potřeba sloučit exportované výsledky, je nejprve nutné je importovat.

Pomocí **exportu výsledků pokrytí kódu** uložte výsledky operace sloučení.

### <a name="limitations-in-merging"></a>Omezení při slučování

- Při sloučení dat pokrytí rozdílných verzí kódu jsou výsledky zobrazeny odděleně, ale nejsou sloučeny. Pro kompletní sloučení výsledků je potřeba použít stejné sestavení kódu pouze s odlišnými testovacími daty.

- Pokud dojde ke sloučení souboru výsledků, který byl exportován a poté importován, je možné zobrazit výsledky jen podle řádků, nikoli podle bloků. K zobrazení dat řádku použijte příkaz **Přidat nebo odebrat sloupce** .

- Při sloučení výsledků testů projektu aplikace ASP.NET dojde k zobrazení výsledků samostatných testů, ale ne k jejich sloučení. To platí pouze pro samotné artefakty ASP.NET, výsledky pro jakákoli jiná sestavení budou sloučeny.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Vyloučit elementy z výsledků pokrytí kódu

Je možné vyloučit určité prvky v kódu z výpočtů pokrytí, například proto, že je kód generován z textové šablony. <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> Přidejte atribut do některého z následujících prvků kódu: třída, struktura, metoda, vlastnost, vlastnost setter nebo getter, Event.

> [!TIP]
> Vyloučení třídy nevylučuje své odvozené třídy.

Příklad:

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Vyloučit elementy v nativním C++ kódu

Vyloučení nespravovaných (nativních) prvků kódu jazyka C++:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Použijte následující makra:

`ExcludeFromCodeCoverage(`*Vyloučení* `, L"` *Funkce Function*`");`

`ExcludeSourceFromCodeCoverage(`*Vyloučení* `, L"` *SourceFilePath*`");`

- Název *vyloučení* je libovolný jedinečný název.

- Název *funkce* je plně kvalifikovaný název funkce. Může obsahovat zástupné znaky. Chcete-li například vyloučit všechny funkce třídy, zapište`MyNamespace::MyClass::*`

- *SourceFilePath* je místní cesta nebo cesta UNC k souboru. cpp. Může obsahovat zástupné znaky. Následující příklad vyloučí všechny soubory v konkrétním adresáři:`\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Umístěte volání maker vyloučení do globálního oboru názvů a nikoli v rámci libovolného oboru názvů nebo třídy.

- Vyloučení se umisťuje buď do souboru kódu jednotkového testu, nebo do souboru kódu aplikace.

- Vyloučení musí být zkompilována jako nespravovaný (nativní) kód, a to buď nastavením možnosti kompilátoru, nebo pomocí `#pragma managed(off)`.

> [!NOTE]
> Chcete-li vyloučit C++funkce v kódu/CLI, použijte `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` atribut pro funkci. Toto je stejné použití jako v jazyce C#.

### <a name="include-or-exclude-additional-elements"></a>Zahrnout nebo vyloučit další prvky

Analýza pokrytí kódu se provádí pouze na sestaveních, která jsou načtena a pro které je soubor *. pdb* k dispozici ve stejném adresáři jako soubor *. dll* nebo *. exe* . Proto je v některých případech možné roztáhnout sadu sestavení, která jsou součástí, a získat tak kopie příslušných souborů *. pdb* .

Můžete vykonat větší kontrolu nad tím, která sestavení a prvky jsou vybrány pro analýzu pokrytí kódu, zápisem souboru *. runsettings* . Je tak například možné vyloučit určitá sestavení bez nutnosti přidávání atributů jejich třídám. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analýza pokrytí kódu v Azure Pipelines

Při vrácení kódu se změnami jsou testy spuštěny na serveru sestavení společně s testy od jiných členů týmu. Je vhodné analyzovat pokrytí kódu v Azure Pipelines a získat tak nejaktuálnější a ucelený přehled o pokrytí celého projektu. Zahrnuje taky automatizované systémové testy a další kódované testy, které obvykle nespouštíte ve vývojových počítačích. Další informace naleznete v tématu [spuštění testů jednotek ve vašich sestaveních](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analýza pokrytí kódu z příkazového řádku

Chcete-li spustit testy z příkazového řádku, použijte *VSTest. Console. exe*. Pokrytí kódu je možnost nástroje *VSTest. Console. exe* .

1. Spusťte Developer Command Prompt pro Visual Studio:

   ::: moniker range="vs-2017"

   V nabídce **Start** systému Windows vyberte možnost **Visual Studio 2017** > **Developer Command Prompt pro vs 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   V nabídce **Start** systému Windows vyberte možnost **Visual Studio 2019** > **Developer Command Prompt pro vs 2019**.

   ::: moniker-end

2. Na příkazovém řádku spusťte následující příkaz:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Další informace najdete v tématu [Možnosti příkazového řádku VSTest. Console. exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Řešení potíží

Pokud nevidíte výsledky pokrytí kódu, může vám pomoct článek věnované [řešení potíží s kódem](../test/troubleshooting-code-coverage.md) .

## <a name="see-also"></a>Viz také:

- [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)
- [Řešení potíží s pokrytím kódu](../test/troubleshooting-code-coverage.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
