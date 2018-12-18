---
title: Kód pokrytí testování
ms.date: 09/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc8b08b68bb6c48fa22abaa90ba8b0b9daa25e89
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370936"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Určení rozsahu testovaného kódu pomocí pokrytí kódu

Funkci pokrytí kódu sady Visual Studio lze použít ke zjištění toho, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako jsou například jednotkové testy. Pro efektivní ochranu před chybami je vhodné testovat, neboli „pokrýt“, velkou část kódu projektu.

Analýza pokrytí kódu může být použita jak pro spravovaný (CLI), tak pro nespravovaný (nativní) kód.

Pokrytí kódu je jedna z možností při spouštění testovacích metod pomocí Průzkumníku testů. Tabulka výsledků zobrazuje procentuální podíl kódu, který byl spuštěn v každém sestavení, třídě a metodě. Editor zdrojového kódu navíc ukazuje samotný kód, který byl testován.

![Výsledky pokrytí kódu s barevné zvýrazňování](../test/media/codecoverage1.png)

## <a name="requirements"></a>Požadavky

Funkci pokrytí kódu je k dispozici pouze v edici Visual Studio Enterprise.

## <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Analýza pokrytí kódu jednotkovými testy v Průzkumníku testů

1. Na **testovací** nabídce zvolte **analyzovat pokrytí kódu**.

2. Chcete-li zobrazit řádky, které byly spuštěny, zvolte ![zobrazit barevné označení ikona pokrytí kódu](../test/media/codecoverage-showcoloringicon.png) **zobrazit barevné označení pokrytí kódu**.

   Pro změnu barvy nebo použití tučného písma zvolte **nástroje** > **možnosti** > **prostředí** > **písma a Barvy** > **zobrazit nastavení pro: textový Editor**. V části **zobrazit položky**, nastavte položky pokrytí.

3. Pokud výsledky zobrazují nízké pokrytí, prozkoumejte, které části kódu nejsou testovány, a vytvořte pro ně další testy. Vývojové týmy obvykle usilují o 80% pokrytí kódu. V některých situacích je přijatelné i nižší pokrytí. Nižší pokrytí je například přijatelné tehdy, pokud je část kódu generována ze standardní šablony.

> [!TIP]
> - Ujistěte se, že tento optimalizace kompilátoru je vypnutý.
> - Pokud pracujete s nespravovaným (nativním) kódem, použijte sestavení pro ladění
> - Ujistěte se, že jsou generovány soubory s příponou .pdb (symbol) pro každé sestavení.

Pokud neobdržíte výsledky, které jste očekávali, přečtěte si téma [Poradce při potížích s pokrytím kódu](../test/troubleshooting-code-coverage.md). Nezapomeňte spustit pokrytí kódu po aktualizaci kódu. Výsledky pokrytí kódu a barevné zvýraznění kódu nejsou po změně kódu nebo při spuštění testů automaticky aktualizovány.

## <a name="report-in-blocks-or-lines"></a>Sestava v blocích nebo řádcích

Pokrytí kódu je určováno *bloky*. Blok je část kódu s právě jedním vstupním a výstupním bodem.  Pokud tok řízení programu projde přes blok během testovacího běhu, tento blok se započítá jako pokrytý. Počet průchodů blokem nemá na výsledek žádný vliv.

Je také možné výsledky zobrazit podle výběru řádků **Přidat/odebrat sloupce** v záhlaví tabulky. Pokud testovací běh otestoval všechny bloky na jednom řádku kódu, započítá se tento řádek jako úplný řádek. Když řádek obsahuje jak otestované, tak i neotestované bloky, pak se započítá jako částečný řádek.

Někteří uživatelé dávají přednost určování pokrytí podle počtu řádků, protože jeho procenta lépe odpovídají velikosti fragmentů, které jsou vidět ve zdrojovém kódu. Dlouhý blok výpočtu by byl započítán jako jeden blok i v případě, že zabírá mnoho řádků.

## <a name="manage-code-coverage-results"></a>Správa výsledků pokrytí kódu

**Výsledky pokrytí kódu** okno obvykle zobrazuje výsledek posledního spuštění. Výsledky se budou lišit, pokud dojde ke změně zkušebních dat nebo jsou pokaždé spuštěny jen některé testy.

Okno pokrytí kódu lze také použít k zobrazení předchozích výsledků nebo výsledků získaných na jiných počítačích.

Je také možné sloučit výsledky několika běhů, pokud například používají jiná testovací data.

- **Chcete-li zobrazit předchozí sady výsledků**, vyberte ho z rozevírací nabídky. Nabídka obsahuje dočasný seznam, který je po otevření nového řešení vyprázdněn.

- **Pro zobrazení výsledků z předchozí relace**, zvolte **importovat výsledky pokrytí kódu**, přejděte **TestResults** složky v řešení a import *.coverage* souboru.

   Vybarvení pokrytí může být nesprávné v případě, že byl zdrojový kód změněn od *.coverage* vygeneroval soubor.

- **Aby byly výsledky čitelné jako text**, zvolte **exportovat výsledky pokrytí kódu**. Tím se vygeneruje čitelné *.coveragexml* soubor, který může zpracovat v jiných nástrojích nebo jednoduše odeslat e-mailu.

- **Pro odeslání výsledků někomu jinému**, odeslat buď *.coverage* souboru nebo exportovaná *.coveragexml* souboru. Tento soubor je pak možné importovat. Pokud se navíc shodují verze zdrojového kódu, je možné zobrazit i vybarvení pokrytí.

## <a name="merge-results-from-different-runs"></a>Sloučení výsledků různých běhů

V některých situacích se na základě testovacích dat použijí různé bloky kódu. Může být tedy nutné sloučit výsledky různých testovacích běhů.

Například při spuštění testu se vstupem „2“ je zjištěno 50% pokrytí určité funkce. Při spuštění testu podruhé se vstupem "-2" se zobrazí v okně pokrytí zobrazí pokrytí zbylých, že se věnujeme zbylých 50 % funkce. Po sloučení výsledků těchto dvou testovacích běhů ukáže sestava i vybarvení 100% pokrytí funkce.

Použití ![ikony pro tlačítko sloučení v okně pokrytí kódu](../test/media/codecoverage-mergeicon.png) **sloučit výsledky pokrytí kódu** provedete to tak. Ke sloučení je možné použít libovolnou kombinaci předešlých běhů nebo importovaných výsledků. Pokud je potřeba sloučit exportované výsledky, je nejprve nutné je importovat.

Použití **exportovat výsledky pokrytí kódu** k uložení výsledků operace sloučení.

### <a name="limitations-in-merging"></a>Omezení při slučování

- Při sloučení dat pokrytí rozdílných verzí kódu jsou výsledky zobrazeny odděleně, ale nejsou sloučeny. Pro kompletní sloučení výsledků je potřeba použít stejné sestavení kódu pouze s odlišnými testovacími daty.

- Pokud dojde ke sloučení souboru výsledků, který byl exportován a poté importován, je možné zobrazit výsledky jen podle řádků, nikoli podle bloků. Použití **Přidat/odebrat sloupce** příkazu můžete zobrazit data řádku.

- Při sloučení výsledků testů projektu aplikace ASP.NET dojde k zobrazení výsledků samostatných testů, ale ne k jejich sloučení. To platí pouze pro samotné artefakty ASP.NET, výsledky pro jakákoli jiná sestavení budou sloučeny.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Vyloučení prvků z výsledků pokrytí kódu

Je možné vyloučit určité prvky v kódu z výpočtů pokrytí, například proto, že je kód generován z textové šablony. Přidat <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atributu na některý z následujících prvků kódu: třídy, struktury, metoda, vlastnost, vlastnost setter nebo getter, události.

> [!TIP]
> Vyloučení třídy nevylučuje její odvozené třídy.

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

### <a name="exclude-elements-in-native-c-code"></a>Vyloučení prvků v nativním kódu jazyka C++

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

`ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *cestakezdrojovemusouboru* `");`

- *ExclusionName* je libovolný jedinečný název.

- *FunctionName* je funkce plně kvalifikovaného názvu. Může obsahovat zástupné znaky. Například pro vyloučení všech funkcí třídy, zápis `MyNamespace::MyClass::*`

- *Cestakezdrojovemusouboru* je místní cesta nebo cesta UNC souboru s příponou .cpp. Může obsahovat zástupné znaky. Následující příklad vylučuje všechny soubory v určitém adresáři: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Umístěte volání maker vyloučení do globálního oboru názvů a nikoli v rámci libovolného oboru názvů nebo třídy.

- Vyloučení se umisťuje buď do souboru kódu jednotkového testu, nebo do souboru kódu aplikace.

- Vyloučení musí být kompilována jako nespravovaný (nativní) kód buď nastavením možnosti kompilátoru, nebo pomocí `#pragma managed(off)`.

> [!NOTE]
> Pro vyloučení funkcí v jazyce C + +/ CLI kódu, použijte atribut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` funkci. Toto je stejné použití jako v jazyce C#.

### <a name="include-or-exclude-additional-elements"></a>Zahrnutí nebo vyloučení dalších prvků

Analýza pokrytí kódu je provedena pouze na sestavení, která jsou načtena a pro které *PDB* je k dispozici ve stejném adresáři jako soubor *.dll* nebo *.exe* souboru. Proto v některých případech můžete rozšířit sadu sestavení, která je zahrnutá získáním kopie jejich odpovídající *PDB* soubory.

Je také možné získat větší kontrolu nad tím, které sestavení a prvky vybranými pro analýzu pokrytí kódu pomocí zápisu *s příponou .runsettings* souboru. Je tak například možné vyloučit určitá sestavení bez nutnosti přidávání atributů jejich třídám. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analýza pokrytí kódu v kanálech Azure

Při vrácení se změnami ve vašem kódu, testy spustit na serveru sestavení společně s testy ostatních členů týmu. To je užitečné analyzovat pokrytí kódu v kanálech Azure získat nejaktuálnější a nejsrozumitelnější obraz o pokrytí celého projektu. Zahrnuje také automatizované systémové testy a další kódované testy, které nejsou obvykle spouštěny na počítačích vývojářů. Další informace najdete v tématu [spouštění testů jednotek s buildy](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analýza pokrytí kódu z příkazového řádku

Chcete-li spustit testy z příkazového řádku, použijte *vstest.console.exe*. Pokrytí kódu je jednou z možností *vstest.console.exe* nástroj.

1. Spusťte příkazový řádek pro vývojáře pro sadu Visual Studio:

   V Windows **Start** nabídce zvolte **Visual Studio 2017** > **Developer Command Prompt for VS 2017**.

2. Na příkazovém řádku spusťte následující příkaz:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Další informace najdete v tématu [možnosti příkazového řádku VSTest.Console.exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Řešení potíží

Pokud se nezobrazí výsledky pokrytí kódu [Poradce při potížích s pokrytím kódu](../test/troubleshooting-code-coverage.md) článku vám můžou pomoct.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)
- [Poradce při potížích s pokrytím kódu](../test/troubleshooting-code-coverage.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
