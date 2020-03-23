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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dd6dde83720c6e6f37bd6827bb5d97526202aa7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585597"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Určení rozsahu testovaného kódu pomocí pokrytí kódu

Funkci pokrytí kódu sady Visual Studio lze použít ke zjištění toho, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako jsou například jednotkové testy. Pro efektivní ochranu před chybami je vhodné testovat, neboli „pokrýt“, velkou část kódu projektu.

Analýza pokrytí kódu může být použita jak pro spravovaný (CLI), tak pro nespravovaný (nativní) kód.

Pokrytí kódu je jedna z možností při spouštění testovacích metod pomocí Průzkumníku testů. Tabulka výsledků zobrazuje procentuální podíl kódu, který byl spuštěn v každém sestavení, třídě a metodě. Editor zdrojového kódu navíc ukazuje samotný kód, který byl testován.

::: moniker range="vs-2017"

![Výsledky pokrytí kódu s vybarvením](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Požadavky

Funkce pokrytí kódu je k dispozici pouze v edici Visual Studio Enterprise.

## <a name="analyze-code-coverage"></a>Analýza pokrytí kódu

::: moniker range="vs-2017"

1. V nabídce **Test** zvolte **Analyzovat pokrytí kódu**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V nabídce **Test** vyberte **analyzovat pokrytí kódu pro všechny testy**.

   ![Analýza nabídky pokrytí kódu ve VS 2019](../test/media/vs-2019/analyze-code-coverage.png)

   Pokrytí kódu můžete spustit také z okna nástroje Průzkumník testů.

::: moniker-end

2. Chcete-li po spuštění testů zjistit, které ![řádky byly spuštěny, zvolte Zobrazit ikonu](../test/media/codecoverage-showcoloringicon.png) Zbarvení pokrytí kódu **Zobrazit zbarvení pokrytí kódu** v okně Výsledky pokrytí **kódu.** Ve výchozím nastavení je kód, který je pokryt testy zvýrazněn světle modrou barvou.

   > [!TIP]
   > Chcete-li změnit barvy nebo použít tučnou plochu, zvolte**Volby** >  **nástrojů** > **Nastavení** > **prostředí Písma a barvy** > **Zobrazit nastavení pro: Textový editor**. V části **Zobrazit položky**upravte nastavení položek "Pokrytí", například **Oblast nedotknutosti**.
   >
   > ![Písma a barvy pokrytí kódu](media/vs-2019/coverage-fonts-and-colors.png)

3. Pokud výsledky zobrazují nízké pokrytí, prozkoumejte, které části kódu nejsou testovány, a vytvořte pro ně další testy. Vývojové týmy obvykle usilují o 80% pokrytí kódu. V některých situacích je přijatelné i nižší pokrytí. Nižší pokrytí je například přijatelné tehdy, pokud je část kódu generována ze standardní šablony.

> [!TIP]
> - Vypnutí optimalizace kompilátoru
> - Pokud pracujete s nespravovaným (nativním) kódem, použijte sestavení ladění
> - Generovat soubory .pdb (symbol) pro každé sestavení

Pokud nedosáhnete očekávaných výsledků, [přečtěte si článek Poradce při potížích s pokrytím kódu](../test/troubleshooting-code-coverage.md).

Nezapomeňte znovu spustit pokrytí kódu po aktualizaci kódu. Výsledky pokrytí kódu a barevné zvýraznění kódu nejsou po změně kódu nebo při spuštění testů automaticky aktualizovány.

## <a name="report-in-blocks-or-lines"></a>Sestava v blocích nebo řádcích

Pokrytí kódu se počítá v *blocích*. Blok je část kódu s právě jedním vstupním a výstupním bodem.  Pokud tok řízení programu prochází blokem během testovacího běhu, tento blok se počítá jako krytý. Počet průchodů blokem nemá na výsledek žádný vliv.

Výsledky můžete také zobrazit v řádcích tak, že v záhlaví tabulky zvolíte **Přidat nebo odebrat sloupce.** Někteří uživatelé dávají přednost určování pokrytí podle počtu řádků, protože jeho procenta lépe odpovídají velikosti fragmentů, které jsou vidět ve zdrojovém kódu. Dlouhý blok výpočtu by byl započítán jako jeden blok i v případě, že zabírá mnoho řádků.

> [!TIP]
> Řádek kódu může obsahovat více než jeden blok kódu. Pokud se jedná o tento případ a spuštění testu vykonává všechny bloky kódu v řádku, počítá se jako jeden řádek. Pokud některé, ale ne všechny bloky kódu v řádku jsou vykonávány, se počítá jako částečný řádek.

## <a name="manage-code-coverage-results"></a>Správa výsledků pokrytí kódu

Okno **Výsledky pokrytí kódu** obvykle zobrazuje výsledek posledního spuštění. Výsledky se budou lišit, pokud dojde ke změně zkušebních dat nebo jsou pokaždé spuštěny jen některé testy.

Okno pokrytí kódu lze také použít k zobrazení předchozích výsledků nebo výsledků získaných na jiných počítačích.

Je také možné sloučit výsledky několika běhů, pokud například používají jiná testovací data.

- **Chcete-li zobrazit předchozí sadu výsledků**, vyberte ji z rozevírací nabídky. Nabídka obsahuje dočasný seznam, který je po otevření nového řešení vyprázdněn.

- **Chcete-li zobrazit výsledky z předchozí relace**, **zvolte Importovat výsledky pokrytí kódu**, přejděte do složky **TestResults** v řešení a importujte soubor *.coverage.*

   Zbarvení pokrytí může být nesprávné, pokud se zdrojový kód od generování souboru *.coverage* změnil.

- **Chcete-li, aby byly výsledky čitelné jako text**, zvolte **Exportovat výsledky pokrytí kódu**. Tím se vygeneruje čitelný soubor *.coveragexml,* který můžete zpracovat pomocí jiných nástrojů nebo snadno odeslat poštou.

- **Chcete-li odeslat výsledky někomu jinému**, odešlete soubor *.coverage* nebo exportovaný soubor *.coveragexml.* Tento soubor je pak možné importovat. Pokud se navíc shodují verze zdrojového kódu, je možné zobrazit i vybarvení pokrytí.

## <a name="merge-results-from-different-runs"></a>Sloučení výsledků z různých spuštění

V některých situacích se na základě testovacích dat použijí různé bloky kódu. Může být tedy nutné sloučit výsledky různých testovacích běhů.

Například při spuštění testu se vstupem „2“ je zjištěno 50% pokrytí určité funkce. Při spuštění testu podruhé se vstupem "-2", uvidíte v zobrazení barev pokrytí, že ostatní 50% funkce je pokryta. Po sloučení výsledků těchto dvou testovacích běhů ukáže sestava i vybarvení 100% pokrytí funkce.

K ![tomu použijte tlačítko Ikona](../test/media/codecoverage-mergeicon.png) pro sloučení v okně Pokrytí **kódu Sloučit výsledky pokrytí kódu.** Ke sloučení je možné použít libovolnou kombinaci předešlých běhů nebo importovaných výsledků. Pokud je potřeba sloučit exportované výsledky, je nejprve nutné je importovat.

K uložení výsledků operace sloučení použijte **výsledky pokrytí exportu.**

### <a name="limitations-in-merging"></a>Omezení při slučování

- Při sloučení dat pokrytí rozdílných verzí kódu jsou výsledky zobrazeny odděleně, ale nejsou sloučeny. Pro kompletní sloučení výsledků je potřeba použít stejné sestavení kódu pouze s odlišnými testovacími daty.

- Pokud dojde ke sloučení souboru výsledků, který byl exportován a poté importován, je možné zobrazit výsledky jen podle řádků, nikoli podle bloků. Pomocí příkazu **Přidat nebo odebrat sloupce** zobrazte data řádku.

- Při sloučení výsledků testů projektu aplikace ASP.NET dojde k zobrazení výsledků samostatných testů, ale ne k jejich sloučení. To platí pouze pro samotné artefakty ASP.NET, výsledky pro jakákoli jiná sestavení budou sloučeny.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Vyloučit prvky z výsledků pokrytí kódu

Je možné vyloučit určité prvky v kódu z výpočtů pokrytí, například proto, že je kód generován z textové šablony. Přidejte <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atribut do některého z následujících prvků kódu: třída, struktura, metoda, vlastnost, setter vlastností nebo getter, event.

> [!TIP]
> Vyloučení třídy nevylučuje její odvozené třídy.

Například:

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

### <a name="exclude-elements-in-native-c-code"></a>Vyloučit prvky v nativním kódu C++

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

`ExcludeFromCodeCoverage(``, L"` Název_funkce *Název_exclusionname* *FunctionName*`");`

`ExcludeSourceFromCodeCoverage(`*Cesta* `, L"` *_SourceFilePath_*`");`

- *ExclusionName* je libovolný jedinečný název.

- *FunctionName* je plně kvalifikovaný název funkce. Může obsahovat zástupné znaky. Chcete-li například vyloučit všechny funkce třídy, zapište`MyNamespace::MyClass::*`

- *SourceFilePath* je místní cesta nebo cesta UNC souboru CPP. Může obsahovat zástupné znaky. Následující příklad vylučuje všechny soubory v určitém adresáři:`\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Umístěte volání maker vyloučení do globálního oboru názvů a nikoli v rámci libovolného oboru názvů nebo třídy.

- Vyloučení se umisťuje buď do souboru kódu jednotkového testu, nebo do souboru kódu aplikace.

- Vyloučení musí být zkompilován jako nespravovaný (nativní) kód, buď nastavením možnosti kompilátoru nebo pomocí `#pragma managed(off)`.

> [!NOTE]
> Chcete-li vyloučit funkce v kódu C++/CLI, použijte atribut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` funkce. Toto je stejné použití jako v jazyce C#.

### <a name="include-or-exclude-additional-elements"></a>Zahrnout nebo vyloučit další prvky

Analýza disponibility kódu se provádí pouze u načtených sestavení, pro která je soubor *PDB* k dispozici ve stejném adresáři jako soubor *DLL* nebo *EXE.* Proto v některých případech můžete rozšířit sadu sestavení, která je součástí získání kopií příslušné soubory *.pdb.*

Můžete vykonávat větší kontrolu nad sestavení a prvky jsou vybrány pro analýzu pokrytí kódu napsáním souboru *.runsettings.* Je tak například možné vyloučit určitá sestavení bez nutnosti přidávání atributů jejich třídám. Další informace naleznete v [tématu Customize code coverage analysis](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analýza pokrytí kódu v Azure Pipelines

Při vrácení kódu se změnami testy spustit na serveru sestavení spolu s testy od ostatních členů týmu. Je užitečné analyzovat pokrytí kódu v Azure Pipelines, abyste získali nejaktuálnější a nejkomplexnější obraz o pokrytí v celém projektu. Zahrnuje také automatizované systémové testy a další kódované testy, které obvykle nespouštěte na vývojových počítačích. Další informace naleznete v [tématu Spuštění testů částí s sestaveními](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analýza pokrytí kódu z příkazového řádku

Chcete-li spustit testy z příkazového řádku, použijte *vstest.console.exe*. Pokrytí kódu je možnost *vstest.console.exe* utility.

1. Spusťte příkazový řádek pro vývojáře pro Visual Studio:

   ::: moniker range="vs-2017"

   V nabídce **Start** systému Windows zvolte **Visual Studio 2017** > **Developer Command Prompt for VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   V nabídce **Start** systému Windows zvolte **Visual Studio 2019** > **Developer Command Prompt for VS 2019**.

   ::: moniker-end

2. Na příkazovém řádku spusťte následující příkaz:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Další informace naleznete v tématu [Možnosti příkazového řádku VSTest.Console.exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Řešení potíží

Pokud nevidíte výsledky pokrytí kódu, článek [Poradce při potížích s pokrytím kódu](../test/troubleshooting-code-coverage.md) vám může pomoci.

## <a name="see-also"></a>Viz také

- [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)
- [Řešení problémů s pokrytím kódu](../test/troubleshooting-code-coverage.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
